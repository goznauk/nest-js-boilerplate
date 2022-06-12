# NEST.JS BOILERPLATE



### Github Workflows:  ECR Publish
#### Create IAM Policy
- IAM > Policies > Create Policy
- Choose JSON and Copy & Paste this
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AllowPush",
            "Effect": "Allow",
            "Action": [
                "ecr:GetDownloadUrlForLayer",
                "ecr:BatchGetImage",
                "ecr:BatchCheckLayerAvailability",
                "ecr:PutImage",
                "ecr:InitiateLayerUpload",
                "ecr:UploadLayerPart",
                "ecr:CompleteLayerUpload"
            ],
            "Resource": "arn:aws:ecr:{YOUR-AWS-REGION}:{YOUR-AWS-ACCOUNT-ID}:repository/*"
        },
        {
            "Sid": "GetAuthorizationToken",
            "Effect": "Allow",
            "Action": [
                "ecr:GetAuthorizationToken"
            ],
            "Resource": "*"
        }
    ]
}
```
- Replace {YOUR-AWS-REGION} to your region, ex. ap-northeast-2
- Replace {YOUR-AWS-ACCOUNT-ID} to your id, ex. 123456781234
  - To find your ID, click the upper right side of your aws console, and there is account id like 1234-5678-1234
- `"Resource": "arn:aws:ecr:ap-northeast-2:123456781234:repository/*"`
- Click next, next and create, name is on your mind just like `ecr` or `ecr-seoul` or etc.

#### Create IAM User
- IAM > Users > Add users
- Username : `github` or any name is acceptable
- Type : Access key - Programmatic access
- Attach existing policies directly > Check IAM Policy you created just before (ex. `ecr`)
- Click next, next and create

#### Create Access Key
- IAM > Users
- Click the User you created just before (ex. `github`)
- Security Credentials > Access keys > Create access key
- Copy your access key and secret access key
- Set Github Secret as `AWS_ACCESS_KEY_ID`, `AWS_SECRET_ACCESS_KEY`



### Set config by
- [node-config](https://github.com/node-config/node-config)
- make json config files at `./config` folder









