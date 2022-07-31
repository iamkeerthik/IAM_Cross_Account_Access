# IAM_Cross_Account_Access
A simple demo for AWS Cross account access with s3 bucket example



AWS IAM Cross Account Access

steps:

1. Prod account ID: 222255557777
   Dev account ID:  888844447777

2.create an IAM role in prod account with s3 access

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "s3:GetObject",
                "s3:PutObject",
                "s3:PutObjectAcl"
            ],
            "Resource": "arn:aws:s3:::AccountABucketName/*"

        }
    ]

}
```

3.Create a new inline policy in Dev account with sts-assume role

```json
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Action": "sts:AssumeRole",
    "Resource": "arn:aws:iam::222222222222:role/acc-to-read-prod-s3-bucket"
  }
}
```


4. Create a new user in Dev account and create developer group and attach newly created policy.

5. Login as a new user and switch role to access s3 bucket from another account.

