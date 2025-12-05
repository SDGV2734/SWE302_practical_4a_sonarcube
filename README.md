## CICD WORKSHOP SAST/DAST

PRACTICAL 4: INTEGRATING SNYK WITH GITHUB ACTIONS

## Setup Instructions

### Required GitHub Secrets

To run the GitHub Actions workflows successfully, you need to configure the following secrets in your repository:

1. **SNYK_TOKEN** (Required)

   - Go to [Snyk.io](https://snyk.io) and create an account
   - Navigate to Account Settings → API Token
   - Copy your API token
   - Add it as a repository secret named `SNYK_TOKEN`

2. **SONAR_TOKEN** (Required for SonarCloud)

   - Create an account at [SonarCloud.io](https://sonarcloud.io)
   - Create a new project for your repository
   - Generate a token in your SonarCloud account settings
   - Add it as a repository secret named `SONAR_TOKEN`

3. **SONAR_ORGANIZATION** (Required for SonarCloud)

   - Your SonarCloud organization key
   - Add it as a repository secret named `SONAR_ORGANIZATION`

4. **SLACK_WEBHOOK_URL** (Optional)
   - If you want Slack notifications for security alerts
   - Create a Slack app and generate a webhook URL
   - Add it as a repository secret named `SLACK_WEBHOOK_URL`
   - If not configured, Slack notifications will be skipped

### How to Add Secrets

1. Go to your GitHub repository
2. Click on **Settings** tab
3. In the left sidebar, click **Secrets and variables** → **Actions**
4. Click **New repository secret**
5. Add the secret name and value
6. Click **Add secret**

## Troubleshooting

### SonarCloud Issues

If you encounter `InvalidProtocolBufferException` or other SonarCloud errors:

1. **Run the troubleshooting script**:

   ```bash
   ./scripts/sonar-troubleshoot.sh
   ```

2. **Manual troubleshooting steps**:

   ```bash
   # Clean build and cache
   mvn clean
   rm -rf ~/.sonar/cache/*

   # Build project step by step
   mvn compile
   mvn test
   mvn jacoco:report
   mvn sonar:sonar
   ```

3. **Common fixes**:
   - Ensure your `SONAR_TOKEN` is valid and not expired
   - Verify your organization name matches your SonarCloud account
   - Make sure your project key is correct in both `pom.xml` and `sonar-project.properties`
   - Check that your SonarCloud project exists and you have permissions

### Recent Fixes Applied

- ✅ Updated SonarCloud Maven plugin to version 4.0.0.4121
- ✅ Fixed organization configuration conflicts
- ✅ Corrected coverage report paths
- ✅ Added proper error handling in GitHub Actions
- ✅ Fixed syntax errors in workflow files

- ✅ Fixed syntax errors in workflow files

hi
