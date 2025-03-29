## Create a bucket 

```sh
aws s3 mb s3://bucket-policy-example-ms-1
```

## Create bucket policy

```sh
aws s3api put-bucket-policy --bucket bucket-policy-example-ms-1 \
--policy file:///workspace/AWS-SAA-C03-Examples/s3/bucket-policy/policy.json
```

# In the other account access the bucket

```sh
touch test.txt
aws s3 cp test.txt s3://bucket-policy-example-ms-1
aws s3 ls s3://bucket-policy-example-ms-1
```


## Cleanup

```sh
aws s3 rm s3://bucket-policy-example-ms-1/test.txt
aws s3 rb s3://bucket-policy-example-ms-1
```