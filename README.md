# AWS Lambda - Image resize after upload to S3

Resizes the image and puts them into the same bucket in /resized folder by default.
Set izes in config.json

Neccesery role permissiions:

AWS CloudWatch logs permission (required for lambda):
```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": [
                "logs:*"
            ],
            "Resource": "arn:aws:logs:*:*:*",
            "Effect": "Allow"
        }
    ]
}
```
Permission to read from bucket:
```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": [
                "s3:GetObject"
            ],
            "Resource": [
                "arn:aws:s3:::app-praise-development/*"
            ],
            "Effect": "Allow"
        }
    ]
}
```
Permission to write to bucket:
```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": [
                "s3:PutObject"
            ],
            "Resource": [
                "arn:aws:s3:::app-praise-development/*"
            ],
            "Effect": "Allow"
        }
    ]
}
```
