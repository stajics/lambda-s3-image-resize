# AWS Lambda - Image resize after upload to S3

original: https://cloudonaut.io/serverless-image-resizing-at-any-scale/

Resizes the image and puts them into the same bucket in /resized folder by default.
Set sizes in config.json ("concurrency": sizes.length() + 1 (not sure ???)):
  * `150x`  fixed width, height is scaled as needed
  * `50x50` scale image best into box
  * `x150` fixed height, width is scaled as needed
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
