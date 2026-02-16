# AWS-Account-Creation-for-Leo

Part 1: Creating Your AWS Account. If you already have an AWS account, please skip to Part 2. 

Prerequisites

Before you begin, ensure you have:

* A valid email address (preferably a corporate email distribution list for business accounts)
* A credit card for payment verification
* A phone number for account verification
* Company information (for business accounts)

Step-by-Step Account Creation

1. Visit the AWS Sign-Up Page

    * Go to https://portal.aws.amazon.com/billing/signup
    * Click "Create an AWS Account"

1. Enter Account Information

    * Provide your email address (this becomes your root user email)
    * Create a strong password for the root user
    * Enter an AWS account name (appears on invoices and consoles)

1. Choose Account Type

    * Select "Business" or "Personal"
    * For business accounts, use a corporate email distribution list and company phone number

1. Provide Contact Information

    * Enter your company or personal information
    * Provide a complete address
    * For Indian addresses, additional verification may be required

1. Add Payment Method

    * Enter credit card details
    * Provide CVV and complete any additional verification (one-time password if required)

1. Verify Your Identity

    * Enter your phone number
    * Receive and enter the verification code via phone call or text message
    * Complete the CAPTCHA verification

1. Accept the AWS Customer Agreement

    * Review and accept the terms

1. Choose a Support Plan

    * Select an appropriate support plan (Basic, Developer, Business, or Enterprise)
    * Basic support is free and suitable for getting started

1. Complete Sign-Up

    * Wait for account activation (typically a few minutes, up to 24 hours)
    * Check your email for confirmation
    * Respond to this E-mail with your Account Number. 

For additional Help:

* AWS Account Set-Up Guide: https://docs.aws.amazon.com/accounts/latest/reference/getting-started.html
* YouTube Tutorial: https://www.youtube.com/watch?v=lIdh92JmWtg

# Part 2: Security and IAM Role Set-Up

Amazon Leo has created a Cloud Formation Template that can be added to your AWS account. Running this template will not only help secure your account, but also give Amazon Leo the necessary access to assist with future inquiries.  

What You'll Need Before Starting

* Your AWS account (already created and logged in)
* The CloudFormation template file (usually ends in .json or .yaml)
* About 10-15 minutes

Step 1: Save the Template File

1. Download the template above (.YAML file)
2. Remember where you saved it (like your Downloads folder or Desktop)
3. Note the file name (for example: aws-setup-template.yaml)

Step 2: Sign In to AWS

1. Go to https://aws.amazon.com
2. Click the "Sign In to the Console" button (top right corner)
3. Enter your email address and password
4. Complete any multi-factor authentication if you set it up

Step 3: Open CloudFormation

1. Once logged in, you'll see a search bar at the top of the page
2. Type "CloudFormation" in the search bar
3. Click on "CloudFormation" from the results (it has an orange icon)

Step 4: Create a New Stack

1. You'll see a button that says "Create stack" (orange button)
2. Click on it
3. A dropdown menu appears—select "With new resources (standard)"

Step 5: Upload Your Template

1. You'll see a page titled "Create stack"
2. Under "Specify template," you'll see several options
3. Select the option that says "Upload a template file"
4. Click the "Choose file" button
5. Find and select the template file you saved in Step 1
6. Click "Next" at the bottom of the page

Step 6: Name Your Stack

1. You'll see a field called "Stack name"
2. Enter a simple name (for example: MyFirstStack or SecuritySetup)

    * Use only letters, numbers, and hyphens (no spaces)

1. You may see some "Parameters" below

    * These are questions the template needs answered
    * Fill them in as instructed (I'll provide guidance on what to enter)

1. Click "Next" at the bottom

Step 7: Configure Stack Options (Optional)

1. This page has advanced settings—you can skip most of these
2. Simply scroll to the bottom and click "Next"

Step 8: Review and Create

1. Review the summary of what will be created
2. Scroll to the bottom of the page
3. You'll see a checkbox that says something like:

    * "I acknowledge that AWS CloudFormation might create IAM resources"

1. Check this box (this gives CloudFormation permission to create security resources)
2. Click the orange "Submit" button

Step 9: Wait for Creation to Complete

1. You'll see a page showing your stack with a status
2. The status will say "CREATE_IN_PROGRESS" (with a spinning icon)
3. This can take 5-15 minutes depending on what's being created
4. The page will automatically refresh
5. When complete, the status will change to "CREATE_COMPLETE" (with a green checkmark)

Step 10: Verify Everything Worked

1. Click on the "Resources" tab
2. You'll see a list of everything that was created
3. Each item should show a status of "CREATE_COMPLETE"
4. If you see any errors (red text), take a screenshot and contact support

If You See an Error Message

1. CloudFormation will automatically clean up
2. Take a screenshot of the error message
3. The status will show "ROLLBACK_COMPLETE" (this means it undid any changes)
4. Common issues:

    * Permission errors: You may need administrator access
    * Resource limits: Your account may have limits on certain resources
    * Invalid parameters: Double-check any values you entered in Step 6

Getting Help

* Click on the "Events" tab to see detailed information about what happened
* Look for any red error messages
* Contact AWS Support or your IT administrator with the error details

After Successful Creation

What to Do Next

1. Review what was created: Click through the "Resources" tab to see all the AWS resources
2. Save your stack name: You'll need this if you want to update or delete resources later
3. Check the "Outputs" tab: This may contain important information like URLs or resource IDs

Managing Your Stack Later

To Update Resources:

1. Go back to CloudFormation
2. Select your stack
3. Click "Update"
4. Upload a new template or modify parameters



AWS Account Security Best Practices

1. Secure Your Root User Account

Enable Multi-Factor Authentication (MFA) for Root User

* Sign in to the AWS Management Console as root user
* Navigate to IAM dashboard
* Select "Add MFA" for root user
* Choose MFA device type (virtual MFA app, hardware token, or security key)
* Follow the setup instructions
* Why this matters: Root users have unrestricted access to all AWS services and resources

Limit Root User Usage

* Use root user only for tasks that specifically require root access
* Do not create access keys for the root user
* Store root user credentials securely

2. Create an Administrative User

Enable AWS IAM Identity Center

* Sign in as root user
* Navigate to IAM Identity Center
* Enable the service
* Create your first administrative user

Create IAM Administrative User (Alternative Method)

* Go to IAM console
* Create a new user with administrative permissions
* Attach the "AdministratorAccess" managed policy
* Enable MFA for this user as well
* Use this account for daily administrative tasks

Ongoing Security Practices

3. Implement Least Privilege Access

Use IAM Groups and Roles

* Create IAM groups for different job functions
* Assign users to appropriate groups
* Use IAM roles for applications and services
* Grant only the permissions necessary to perform specific tasks

Apply AWS Managed Policies Initially

* Start with AWS managed policies as templates
* Refine permissions over time to be more specific
* Move toward custom least-privilege policies

4. Use Temporary Credentials

For Human Users

* Require federation with an identity provider (like AWS IAM Identity Center)
* Avoid long-term access keys whenever possible
* Use temporary credentials that expire automatically

For Workloads and Applications

* Use IAM roles to provide temporary credentials
* Avoid embedding access keys in application code
* Leverage EC2 instance profiles, Lambda execution roles, etc.

5. Rotate Access Keys Regularly

For Long-Term Credentials

* Rotate access keys at regular intervals (every 90 days recommended)
* Delete unused access keys
* Monitor access key age using IAM credential reports

6. Enable Monitoring and Notifications

Set Up CloudTrail

* Enable AWS CloudTrail in all regions
* Log all API calls and user activity
* Store logs in a secure S3 bucket

Configure Root User Activity Alerts

* Set up CloudWatch alarms for root user activity
* Receive notifications when root user signs in or makes changes

Use AWS Config

* Enable AWS Config to track resource configurations
* Set up rules to detect non-compliant resources

7. Use IAM Access Analyzer

Generate Least-Privilege Policies

* Use IAM Access Analyzer to review access activity
* Generate policies based on actual usage patterns
* Identify overly permissive policies

Verify External Access

* Regularly check for resources shared with external entities
* Review public and cross-account access
* Validate that sharing is intentional

Validate IAM Policies

* Use policy validation features to ensure policies are secure
* Check for syntax errors and security warnings

8. Regular Security Audits

Review and Remove Unused Resources

* Periodically audit IAM users, roles, and policies
* Delete unused users and roles
* Remove unnecessary permissions
* Review group memberships

Update Security Credentials

* Ensure all users have MFA enabled
* Verify that access keys are rotated
* Check for inactive credentials

9. Implement Multi-Account Strategy

Use AWS Organizations

* Create separate accounts for different workloads or environments
* Implement Service Control Policies (SCPs) for guardrails
* Centralize billing and management

Define Permission Boundaries

* Set permissions guardrails at the organizational unit level
* Use permission boundaries to delegate permissions safely

10. Additional Security Measures

Enable AWS Security Hub

* Centralize security findings across AWS accounts
* Get automated security checks against best practices

Use AWS GuardDuty

* Enable intelligent threat detection
* Monitor for malicious activity and unauthorized behavior

Implement VPC Security

* Use security groups and network ACLs
* Enable VPC Flow Logs for network monitoring

Helpful Resources

Official AWS Documentation

* Getting Started Guide: https://docs.aws.amazon.com/accounts/latest/reference/getting-started.html
* IAM Best Practices: https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html
* Security Best Practices: https://aws.amazon.com/iam/resources/best-practices/
* AWS Well-Architected Framework (Security Pillar): https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/welcome.html

Additional Learning Resources

* AWS Security Documentation: https://docs.aws.amazon.com/security/
* AWS Prescriptive Guidance: https://docs.aws.amazon.com/prescriptive-guidance/latest/security-controls-by-caf-capability/identity-and-access-controls.html
* AWS re:Post: Community forum for AWS questions and answers
* AWS Skill Builder: Free and paid training courses

Important Reminders

* Never share your root user credentials
* Always use MFA for privileged accounts
* Regularly review and audit permissions
* Use temporary credentials whenever possible
* Monitor your AWS account activity
* Keep contact information up to date


