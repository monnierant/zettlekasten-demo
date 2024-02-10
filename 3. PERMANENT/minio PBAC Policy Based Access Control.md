---
type: conclusion
topic: devops 
---

- Topic : #VeilleIT/devops 
- Tags : #minio

# Idea


## Read only bucket permission

For `secured-demo` bucket
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
         "Effect" : "Allow",
         "Action" : [ "s3:GetBucketLocation", "s3:GetObject", "s3:ListBucket" ],
         "Resource" : "arn:aws:s3:::secured-demo"
      }
    ]
}
```

> [!hint] 
> Create the `policy` then add it to the `group` and add `user` to the `group` 


# Links

Sources : [Access Management — MinIO Object Storage for Linux](https://min.io/docs/minio/linux/administration/identity-access-management/policy-based-access-control.html)

## West : Similar

## East : Opposite

## North : Theme / Question

- [[How to provide an easy and secure kind of repo for deploying manually applications to clients]]

## South : What does it lead to

