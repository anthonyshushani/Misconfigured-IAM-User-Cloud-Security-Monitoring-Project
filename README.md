# Misconfigured-IAM-User-Cloud-Security-Monitoring-Project

This project simulates how a misconfigured IAM user with excessive privileges can be exploited — and how AWS security tools like CloudTrail and GuardDuty can detect and log suspicious behavior.

🎯 Objective
To demonstrate:

The security risk of granting full AdministratorAccess to a single IAM user

How threat actors might exploit that access via AWS CLI

How AWS CloudTrail logs and GuardDuty findings detect this misuse

🧪 Simulation Steps
Created a misconfigured IAM user named misconfigured-user

Granted it full AdministratorAccess

Generated access keys for CLI use

Configured AWS CLI on a local terminal using the misconfigured user's credentials

Simulated attacker behavior with AWS CLI:

aws s3 ls – listed S3 buckets

aws ec2 describe-instances – enumerated EC2 instances

aws iam list-users – attempted privilege recon

aws iam list-roles – explored role privileges

Monitored the environment using:

✅ CloudTrail: Captured API events from the misconfigured user

✅ GuardDuty: Looked for potential threat findings like IAM reconnaissance

📊 Logged Activity Examples
json
Copy
Edit
"eventName": "ListBuckets"
"eventSource": "s3.amazonaws.com"
"userName": "misconfigured-user"
"sourceIPAddress": "173.x.x.x"
json
Copy
Edit
"eventName": "DescribeInstances"
"eventSource": "ec2.amazonaws.com"
"userAgent": "aws-cli/2.27.x ..."
⚠️ Key Takeaways
Granting full access to individual IAM users is a critical vulnerability

CLI activity is traceable using CloudTrail logs

GuardDuty enhances visibility by flagging suspicious behavior patterns

IAM roles and least-privilege access should be enforced to reduce risk

🛡️ Next Steps (Mitigation)
Revoke access keys of misconfigured users

Enable MFA on root accounts and IAM users

Use IAM roles instead of user-based admin access

Set up budget alerts and logging alerts for unusual activity
