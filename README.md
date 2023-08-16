# Simple Website Hosting With S3

A static website showcasing different animals was created with HTML, CSS, and JavaScript.
The website was hosted on Amazon S3, and Amazon CloudFront was used as a content delivery network (CDN) for faster loading times.

## Architecture Design
![WebDeployWithS3](https://github.com/ella-adeka/WebHostingWithS3/assets/70539937/4792b316-0da2-44af-b38e-2e749092799c)

## Results
Website (on localhost)\
![image](https://github.com/ella-adeka/WebHostingWithS3/assets/70539937/d28629ba-6729-42f0-a58f-f3a09fbe37a2)

Bucket Policy\
```json
{
    "Version": "2008-10-17",
    "Id": "PolicyForCloudFrontPrivateContent",
    "Statement": [
        {
            "Sid": "AllowCloudFrontServicePrincipal",
            "Effect": "Allow",
            "Principal": {
                "Service": "cloudfront.amazonaws.com"
            },
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::BUCKET-NAME/*",
            "Condition": {
                "StringEquals": {
                    "AWS:SourceArn": "arn:aws:cloudfront::198602996340:distribution/DISTRIBUTION-ID"
                }
            }
        }
    ]
}
```

Website on Cloudfront\
![image](https://github.com/ella-adeka/WebHostingWithS3/assets/70539937/852025f2-365f-43ee-8eca-017efac7d157)
