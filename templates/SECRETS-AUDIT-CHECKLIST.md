# Secrets Audit Checklist

**Company:** [YOUR COMPANY]
**Application:** [YOUR APP]
**Version:** 1.0
**Effective Date:** [DATE]
**Last Updated:** [DATE]
**Owner:** [YOUR NAME], Security Lead
**Audit Frequency:** Monthly (<!-- CUSTOMIZE: adjust based on risk tolerance -->)

---

## Team Size Adaptation

This template uses role names like "Security Lead" as a placeholder. For solo founders, you fill all these roles yourself — simply use your own name. For small teams (2–5), assign roles based on who handles infrastructure/security. The controls are the same regardless of team size; only the assignment changes.

---

## Overview

This checklist ensures that secrets (API keys, database credentials, encryption keys, tokens) are never committed to version control, are properly rotated, and are securely managed in your application. A single exposed secret can compromise the entire application.

<!-- CUSTOMIZE: Add your specific services and secrets inventory -->

---

## Part 1: Git Repository Audit

### 1.1 .gitignore Verification

**Objective:** Ensure all secret files are excluded from version control.

- [ ] **Review .gitignore File**
  ```bash
  # Show current .gitignore
  cat .gitignore
  ```

  Verify it contains:
  - [ ] `.env` (local environment file)
  - [ ] `.env.local` / `.env.*.local`
  - [ ] `*.pem` / `*.key` (private keys)
  - [ ] `.ssh/` (SSH keys)
  - [ ] `secrets/` (local secrets directory)
  - [ ] `config/secrets.yml` or equivalent (Rails, other frameworks)
  - [ ] Cloud provider credential files:
    - [ ] `~/.aws/credentials`
    - [ ] `~/.gcloud/`
    - [ ] `~/.azure/`
  - [ ] IDE/Editor files: `.vscode/settings.json` (if contains secrets)
  - [ ] OS files: `.DS_Store`, `Thumbs.db`
  - [ ] Dependency lock files (if they could contain secrets)

- [ ] **Commit .gitignore Changes**
  ```bash
  git add .gitignore
  git commit -m "[SECURITY] Update .gitignore to exclude all secret types"
  ```

---

### 1.2 Git History Scanning for Exposed Secrets

**Objective:** Detect any secrets accidentally committed in the past.

- [ ] **Scan Repository with Truffledog / git-secrets / Gitleaks**

  **Option 1: Gitleaks (Recommended)**
  ```bash
  # Install gitleaks (if not already installed)
  brew install gitleaks  # or: npm install -g gitleaks / apt-get install gitleaks

  # Scan entire repository history
  gitleaks detect --source . --verbose

  # Scan since a specific commit
  gitleaks detect --source . --log-opts "commit1..commit2"
  ```

  **Option 2: git-secrets**
  ```bash
  # Install git-secrets
  brew install git-secrets

  # Add AWS patterns
  git secrets --register-aws

  # Scan repository
  git secrets --scan
  ```

  **Option 3: TruffleHog**
  ```bash
  # Install TruffleHog
  pip install truffleHog

  # Scan repository
  truffleHog filesystem .
  ```

- [ ] **Review Scan Results**
  - [ ] No API keys found
  - [ ] No database passwords found
  - [ ] No AWS/GCP/Azure credentials found
  - [ ] No private encryption keys found
  - [ ] No OAuth tokens found
  - [ ] No payment processor keys found

- [ ] **If Secrets Found:**
  1. [ ] **CRITICAL:** Immediately revoke the exposed secret (rotate/delete)
  2. [ ] [ ] Remove secret from git history (see Git History Cleanup section below)
  3. [ ] [ ] Verify the secret was not misused (check access logs, API usage)
  4. [ ] [ ] Document the incident in security log
  5. [ ] [ ] If secret leaked to remote (GitHub, etc.), assume compromise and revoke immediately

---

### 1.3 Recent Commit Review

**Objective:** Check recent commits (past 30 days) for accidentally committed secrets.

- [ ] **Review Last 30 Days of Commits**
  ```bash
  git log --oneline --since="30 days ago" | head -20
  ```

  For each significant commit, check:
  - [ ] `git show [COMMIT_HASH]` — Review changes
  - [ ] Look for patterns: `password=`, `api_key=`, `secret=`, `token=`, `AWS_ACCESS_KEY`
  - [ ] Check for binary files (could be credentials)

- [ ] **Check Diff Against main/production Branch**
  ```bash
  git diff main..HEAD --name-only | head -20
  ```

  Verify no secret files are in the diff.

---

### 1.4 Git Commit Configuration

**Objective:** Enforce signed commits to prevent unauthorized changes.

- [ ] **Configure Git to Sign Commits (GPG)**
  ```bash
  # List available GPG keys
  gpg --list-secret-keys --keyid-format LONG

  # Set default signing key
  git config --global user.signingkey [KEY_ID]

  # Enable commit signing by default
  git config --global commit.gpgsign true
  ```

- [ ] **Verify Recent Commits Are Signed**
  ```bash
  git log --show-signature -n 5
  ```

  Check: `Good signature from [Your Name]`

- [ ] **Add Pre-Commit Hook to Enforce Signing**
  ```bash
  # File: .git/hooks/pre-commit
  #!/bin/bash
  # Prevent commits without GPG signature

  if ! git config --get user.signingkey > /dev/null; then
    echo "ERROR: Commit signing not configured. Run: git config --global commit.gpgsign true"
    exit 1
  fi
  ```

  Make executable:
  ```bash
  chmod +x .git/hooks/pre-commit
  ```

---

## Part 2: Environment Variables & Secrets Management

### 2.1 Environment Variable Inventory

**Objective:** Document all secrets used by [YOUR APP].

Create a file: `SECRETS-INVENTORY.md` (keep this file in secure location, NOT in git):

```markdown
# Secrets Inventory

## API Keys

| Service | Secret Name | Purpose | Rotation Schedule | Last Rotated |
|---------|------------|---------|------------------|--------------|
| OpenAI | OPENAI_API_KEY | LLM API calls | Monthly | 2026-03-15 |
| Twilio | TWILIO_AUTH_TOKEN | Voice/SMS API | Quarterly | 2026-02-01 |
| Stripe | STRIPE_SECRET_KEY | Payment processing | Quarterly | 2026-01-20 |

## Database Credentials

| Service | Secret Name | User | Host | Rotation Schedule | Last Rotated |
|---------|------------|------|------|------------------|--------------|
| PostgreSQL | DATABASE_PASSWORD | [YOUR DATABASE] admin | prod.db.internal | Quarterly | 2026-02-10 |

## Encryption Keys

| Key Type | Secret Name | Purpose | Key Size | Rotation Schedule | Last Rotated |
|----------|------------|---------|----------|------------------|--------------|
| Master Key | MASTER_ENCRYPTION_KEY | Data encryption | 256-bit | Annually | 2025-06-01 |

## OAuth & Tokens

| Service | Secret Name | Purpose | Expiry | Notes |
|---------|------------|---------|--------|-------|
| GitHub | GITHUB_OAUTH_TOKEN | CI/CD automation | N/A (no expiry) | Needs rotation plan |
```

- [ ] **Secrets Inventory Completed**
  - [ ] Document all API keys
  - [ ] Document all database credentials
  - [ ] Document all encryption keys
  - [ ] Document all OAuth tokens
  - [ ] Store inventory in secure location (not in git)
  - [ ] Limit access to inventory (security team only)

---

### 2.2 Environment Variable Management

**Objective:** Ensure all secrets use environment variables, never hardcoded.

- [ ] **Search Codebase for Hardcoded Secrets**
  ```bash
  # Search for common patterns
  grep -r "password\s*=" src/ --include="*.py" --include="*.js" --include="*.go"
  grep -r "api_key\s*=" src/ --include="*.py" --include="*.js" --include="*.go"
  grep -r "secret\s*=" src/ --include="*.py" --include="*.js" --include="*.go"
  grep -r "BEGIN RSA PRIVATE KEY" src/ --include="*.py" --include="*.js"
  ```

  - [ ] No hardcoded secrets found (or all flagged issues remediated)

- [ ] **Verify All Secrets Use Environment Variables**

  Example (Python):
  ```python
  import os

  # ✓ CORRECT: Load from environment
  api_key = os.getenv('OPENAI_API_KEY')

  # ✗ WRONG: Hardcoded (NEVER do this)
  # api_key = "sk-1234567890abcdef"
  ```

  Example (Node.js):
  ```javascript
  // ✓ CORRECT: Load from environment
  const apiKey = process.env.OPENAI_API_KEY;

  // ✗ WRONG: Hardcoded (NEVER do this)
  // const apiKey = "sk-1234567890abcdef";
  ```

- [ ] **Create .env.example Template**
  ```bash
  # File: .env.example (SAFE to commit to git)
  # Description of what each variable does, but NO actual values

  OPENAI_API_KEY=your_openai_api_key_here
  TWILIO_AUTH_TOKEN=your_twilio_token_here
  DATABASE_PASSWORD=your_db_password_here
  STRIPE_SECRET_KEY=your_stripe_key_here
  ```

  - [ ] `.env.example` committed to git (no secrets, only template)
  - [ ] `.env` (actual secrets) in `.gitignore` (NOT in git)

---

### 2.3 Secret Validation

**Objective:** Verify secrets are valid and accessible.

- [ ] **Test Each Secret Works**
  ```bash
  # Example: Test OpenAI API key
  curl -H "Authorization: Bearer $OPENAI_API_KEY" \
       https://api.openai.com/v1/models

  # Example: Test Stripe key
  curl -u $STRIPE_SECRET_KEY: \
       https://api.stripe.com/v1/account
  ```

  - [ ] All API keys valid and return 200 OK (or expected response)
  - [ ] All database credentials can authenticate
  - [ ] All encryption keys can encrypt/decrypt test data

- [ ] **Verify Permissions Are Correct**
  - [ ] API keys have minimal required permissions (principle of least privilege)
  - [ ] Database users have only necessary roles (not admin)
  - [ ] OAuth tokens have scoped permissions

---

## Part 3: Secrets Storage

### 3.1 Local Development

**Objective:** Ensure secrets are securely managed in local development environment.

- [ ] **Use .env File for Local Development**
  ```bash
  # File: .env (never commit to git)
  OPENAI_API_KEY=sk-...
  DATABASE_PASSWORD=...
  STRIPE_SECRET_KEY=sk_live_...
  ```

- [ ] **Load .env Automatically**

  Example (Python + python-dotenv):
  ```python
  from dotenv import load_dotenv
  load_dotenv()
  api_key = os.getenv('OPENAI_API_KEY')
  ```

  Example (Node.js + dotenv):
  ```javascript
  require('dotenv').config();
  const apiKey = process.env.OPENAI_API_KEY;
  ```

- [ ] **Restrict File Permissions**
  ```bash
  # Make .env readable only by owner
  chmod 600 .env

  # Verify permissions (should show: -rw-------)
  ls -la .env
  ```

- [ ] **Document in README**
  ```markdown
  ## Local Development Setup

  1. Copy `.env.example` to `.env`:
     ```bash
     cp .env.example .env
     ```

  2. Fill in actual secret values in `.env` (retrieve from [VAULT/MANAGER])

  3. Never commit `.env` to git (it's in .gitignore)
  ```

---

### 3.2 CI/CD Pipeline (GitHub Actions, GitLab CI, etc.)

**Objective:** Manage secrets securely in automated pipelines.

#### GitHub Actions

- [ ] **Use GitHub Secrets for All Sensitive Data**
  ```yaml
  # File: .github/workflows/deploy.yml

  env:
    OPENAI_API_KEY: ${{ secrets.OPENAI_API_KEY }}
    DATABASE_PASSWORD: ${{ secrets.DATABASE_PASSWORD }}

  steps:
    - name: Run tests
      run: npm test
  ```

- [ ] **Secrets Not Logged**
  - [ ] Verify logs don't print secrets:
    ```bash
    # NEVER do this in CI/CD:
    echo "API Key: $OPENAI_API_KEY"  # ✗ WRONG

    # Secrets should be masked:
    echo "API Key: ***"  # ✓ CORRECT
    ```

- [ ] **Audit Secret Usage**
  ```bash
  # GitHub: Settings → Secrets and variables → Actions
  # Review all secrets listed
  # Verify only used by necessary workflows
  ```

#### GitLab CI

- [ ] **Use GitLab Protected Variables**
  ```yaml
  # File: .gitlab-ci.yml

  deploy:
    script:
      - npm install
      - OPENAI_API_KEY=$OPENAI_API_KEY npm run build
    only:
      - main
  ```

  Variables configured in: Settings → CI/CD → Variables

#### General CI/CD Audit

- [ ] **All Secrets Stored in CI/CD Platform (not in code)**
- [ ] **Restrict Secret Access to Production Branch Only**
- [ ] **Log CI/CD Secret Access** (audit trail)
- [ ] **No Secrets in Build Logs/Artifacts**

---

### 3.3 Production Environment (Cloud Provider)

**Objective:** Manage secrets securely in production.

#### AWS Secrets Manager / Parameter Store

- [ ] **Store All Production Secrets in AWS Secrets Manager**
  ```bash
  # Create a secret
  aws secretsmanager create-secret \
    --name prod/openai-api-key \
    --secret-string '{"api_key":"sk-..."}'

  # Retrieve secret in application
  import boto3
  client = boto3.client('secretsmanager')
  secret = client.get_secret_value(SecretId='prod/openai-api-key')
  ```

- [ ] **Enable Secret Rotation**
  ```bash
  # Configure auto-rotation for long-lived secrets
  aws secretsmanager rotate-secret \
    --secret-id prod/openai-api-key \
    --rotation-rules AutomaticallyAfterDays=30
  ```

- [ ] **Restrict IAM Access**
  - [ ] Only application role (EC2, Lambda) can read secrets
  - [ ] No human user direct access to production secrets
  - [ ] Audit logging enabled (CloudTrail)

#### Google Cloud Secret Manager

- [ ] **Store Secrets in Google Secret Manager**
  ```bash
  # Create secret
  echo -n "sk-..." | gcloud secrets create openai-api-key --data-file=-

  # Retrieve in application
  from google.cloud import secretmanager
  client = secretmanager.SecretManagerServiceClient()
  secret = client.access_secret_version(request={"name": secret_name})
  ```

#### Azure Key Vault

- [ ] **Store Secrets in Azure Key Vault**
  ```bash
  # Create secret
  az keyvault secret set --vault-name MyKeyVault \
    --name openai-api-key --value "sk-..."

  # Retrieve in application
  from azure.identity import DefaultAzureCredential
  from azure.keyvault.secrets import SecretClient

  credential = DefaultAzureCredential()
  client = SecretClient(vault_url=vault_url, credential=credential)
  secret = client.get_secret("openai-api-key")
  ```

---

## Part 4: Secret Rotation

### 4.1 Rotation Schedule

**Objective:** Regularly rotate secrets to limit blast radius if compromised.

- [ ] **Document Rotation Schedule**

  | Secret | Type | Rotation Frequency | Last Rotated | Next Due | Owner |
  |--------|------|-------------------|---|---|---|
  | OpenAI API Key | API Key | Monthly | 2026-03-15 | 2026-04-15 | [NAME] |
  | Database Password | Credential | Quarterly | 2026-02-01 | 2026-05-01 | [NAME] |
  | Encryption Master Key | Key | Annually | 2025-06-01 | 2026-06-01 | [NAME] |
  | Stripe Secret Key | API Key | Quarterly | 2026-01-20 | 2026-04-20 | [NAME] |

- [ ] **Rotation Frequency Guidelines**
  - **High-Risk** (payment, admin access): Monthly
  - **Medium-Risk** (API keys): Monthly–Quarterly
  - **Low-Risk** (read-only API keys): Quarterly–Annually
  - **Master Keys**: Annually (balance: security vs. operational burden)

---

### 4.2 Rotation Procedures

- [ ] **For Each Secret Being Rotated:**

  1. [ ] **Create New Secret**
     - Generate new API key / password / token
     - Store new secret in secrets manager

  2. [ ] **Dual-Run Period**
     - Update application to accept both old and new secrets
     - Deploy code change to production
     - Wait 24 hours (allow connections to drain)

  3. [ ] **Revoke Old Secret**
     - Revoke/delete old secret in source system (API provider, database, etc.)
     - Remove acceptance of old secret from application
     - Deploy code change

  4. [ ] **Verification**
     - [ ] Application logs confirm only new secret used
     - [ ] No failed authentications in logs
     - [ ] All services still operational

  5. [ ] **Document**
     - [ ] Update rotation table with new "Last Rotated" date
     - [ ] Document in audit log
     - [ ] Example: "Rotated OPENAI_API_KEY on 2026-03-15, revoked old key on 2026-03-16"

---

### 4.3 Automated Rotation

- [ ] **Enable Automatic Rotation Where Possible**

  **AWS Secrets Manager:**
  ```bash
  aws secretsmanager rotate-secret \
    --secret-id prod/database-password \
    --rotation-rules AutomaticallyAfterDays=90
  ```

  **Kubernetes Secrets (if applicable):**
  ```yaml
  apiVersion: bitnami.com/v1alpha1
  kind: SealedSecret
  metadata:
    name: my-secret
  spec:
    encryptedData:
      password: AgBYGWu6f...
  ```

- [ ] **Test Automated Rotation**
  - [ ] Manually trigger a test rotation in staging
  - [ ] Verify application still works with new secret
  - [ ] Monitor logs for any failures

---

## Part 5: Access Control & Auditing

### 5.1 Who Has Access to Secrets?

- [ ] **Document Secret Access Control**

  | Secret | Access Level | Who | Purpose | Last Reviewed |
  |--------|---|---|---|---|
  | OPENAI_API_KEY | Production | Engineering team | Code deployment | 2026-03-01 |
  | DATABASE_PASSWORD | Admin | Senior engineer [NAME] | Backup/recovery | 2026-03-01 |
  | MASTER_ENCRYPTION_KEY | Restricted | Security lead [NAME] | Key rotation only | 2026-03-01 |

- [ ] **Principle of Least Privilege**
  - [ ] Developers: Have access to staging secrets only
  - [ ] CI/CD: Has access only to secrets needed for deployment
  - [ ] Database admins: Have access to database credentials only
  - [ ] Security team: Have access to all secrets (read-only audit)

- [ ] **Restrict Secret Access in Secrets Manager**

  AWS Secrets Manager IAM Policy:
  ```json
  {
    "Version": "2012-10-17",
    "Statement": [
      {
        "Effect": "Allow",
        "Principal": {
          "AWS": "arn:aws:iam::ACCOUNT:role/ECSTaskRole"
        },
        "Action": [
          "secretsmanager:GetSecretValue"
        ],
        "Resource": "arn:aws:secretsmanager:region:account:secret:prod/*"
      }
    ]
  }
  ```

---

### 5.2 Audit Logging

- [ ] **Enable Audit Logging for Secret Access**

  **AWS CloudTrail:**
  ```bash
  # Verify CloudTrail is logging Secrets Manager API calls
  aws cloudtrail describe-trails --region us-east-1
  ```

  **CloudWatch Logs:**
  ```bash
  # Search for GetSecretValue calls
  aws logs filter-log-events \
    --log-group-name /aws/secretsmanager \
    --filter-pattern "GetSecretValue"
  ```

- [ ] **Monitor Secret Access**
  - [ ] Set up CloudWatch alarms for failed secret access
  - [ ] Alert if secret accessed outside normal hours
  - [ ] Alert if secret accessed by unexpected principal

- [ ] **Regular Audit Log Review**
  - [ ] Monthly review of secret access logs
  - [ ] Document any unusual access patterns
  - [ ] Verify only authorized users accessed secrets

---

## Part 6: Incident Response

### 6.1 Secret Exposure Response

**Objective:** Rapid response if a secret is exposed or compromised.

- [ ] **If Secret Is Exposed (in git, logs, etc.):**

  **Within 5 Minutes:**
  1. [ ] **Remove from Exposure Source**
     - If in git: Use `git filter-branch` or BFG to remove from history
     - If in logs: Delete log files containing secret
     - If in CI/CD: Purge build logs

  2. [ ] **Notify Security Team**
     - [ ] Declare security incident
     - [ ] Add to incident log

  **Within 30 Minutes:**
  3. [ ] **Revoke the Secret**
     - [ ] Delete/revoke API key from provider
     - [ ] Reset password if database credential
     - [ ] Revoke OAuth token

  4. [ ] **Rotate the Secret**
     - [ ] Generate new secret
     - [ ] Update in secrets manager
     - [ ] Redeploy application

  5. [ ] **Investigate Impact**
     - [ ] Check API usage logs for unauthorized calls
     - [ ] Check database access logs for unusual queries
     - [ ] Determine if any data was accessed
     - [ ] Determine exposure timeline

  **Within 24 Hours:**
  6. [ ] **Post-Incident Review**
     - [ ] Root cause analysis (how did secret leak?)
     - [ ] Preventive measures (improve .gitignore, scanning, etc.)
     - [ ] Document in security log

---

## Part 7: Pre-Deployment Checklist

**Before deploying to production:**

- [ ] **Secrets Audit Passed**
  - [ ] No hardcoded secrets in code
  - [ ] No secrets in git history
  - [ ] All .env files in .gitignore

- [ ] **Environment Variables Set**
  - [ ] All required secrets loaded from environment
  - [ ] Secrets manager integration tested
  - [ ] Fallback to local .env in development

- [ ] **Access Controls Verified**
  - [ ] Only necessary services/users have access
  - [ ] IAM policies restrict to least privilege
  - [ ] Audit logging enabled

- [ ] **Rotation Scheduled**
  - [ ] All secrets have rotation schedule
  - [ ] Automated rotation configured where possible
  - [ ] Rotation dates documented

---

## Audit Results

| Check | Status | Notes | Verified By | Date |
|-------|--------|-------|---|---|
| .gitignore complete | ✓ / ⚠ / ✗ | | | |
| Git history scanned for secrets | ✓ / ⚠ / ✗ | | | |
| No hardcoded secrets in code | ✓ / ⚠ / ✗ | | | |
| Environment variables configured | ✓ / ⚠ / ✗ | | | |
| Secrets manager integrated | ✓ / ⚠ / ✗ | | | |
| Access controls verified | ✓ / ⚠ / ✗ | | | |
| Audit logging enabled | ✓ / ⚠ / ✗ | | | |
| Rotation schedule documented | ✓ / ⚠ / ✗ | | | |
| CI/CD secrets secured | ✓ / ⚠ / ✗ | | | |

---

## Remediation Log

| Issue | Severity | Description | Remediation Steps | Completed By | Date Completed |
|-------|----------|-------------|---|---|---|
| | | | | | |

---

## Sign-Off

| Role | Name | Signature | Date |
|------|------|-----------|------|
| Security Lead | [YOUR NAME] | _____________ | ________ |
| Engineering Lead | [YOUR NAME] | _____________ | ________ |

---

## Appendix: Useful Commands

```bash
# Scan git history for secrets
gitleaks detect --source . --verbose

# Search for hardcoded secrets in code
grep -r "password\|api_key\|secret\|token" src/ --include="*.py"

# Check file permissions
ls -la .env

# List all environment variables in use
printenv | sort

# Test API key validity
curl -H "Authorization: Bearer $API_KEY" https://api.example.com/v1/test

# Rotate a database password
mysql -u root -p -e "ALTER USER 'app'@'localhost' IDENTIFIED BY 'newpassword';"
```

---

## Change Log

| Date | Change | Owner |
|------|--------|-------|
| [DATE] | Initial secrets audit checklist | [YOUR NAME] |
| [DATE] | Added Gitleaks scanning procedure | [YOUR NAME] |
