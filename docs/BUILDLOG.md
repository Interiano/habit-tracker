Sprint 0
The setup:
1. aws account
2. tools installed
3. git repo
4. Terraform backend
5. AWS Budget

verify each:
aws --version
terraform -version
node --version
git --version

Create IAM admin:
create IAM admin user in console = AdministratorAccess policy - enable MFA
I have a AdminAccess policy already but it's attached to a different system
It's important to recognize what I have since following Least-Prev.

How to check w/ CLI:
# list what's on your user
aws iam list-attached-user-policies --user-name YOUR_USERNAME

# read the actual JSON of a managed policy
aws iam get-policy-version \
  --policy-arn arn:aws:iam::aws:policy/IAMFullAccess \
  --version-id v1

aws configure
    access key + secret
aws sts get-caller-identity
    confirm it's IAM user, not root <--

I accidently changed the secret accest key and had to remake it. 
The guide I had claude make me used Linux commands, so random.
I had to delete a redundant policy key and the altered key. It's fine.
I just had to apply the new key to get to be able to use AWS CLI

create remote Terraform state backend
state lives in S3 (versioned) dynamodb lock table 
I did these commands with AWS CLI, JSON code

I put together the dynamodb and applied versioning
To Do for 8/28/26:
4. 
5. 

