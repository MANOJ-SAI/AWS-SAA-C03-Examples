## Create a bucket

```sh
aws s3api create-bucket --bucket acl-example-ms-1 --create-bucket-configuration="LocationConstraint=us-west-2" 
```


## Turn of the Block public Access for ACLs

```sh
aws s3api put-public-access-block \
--bucket acl-example-ms-1 \
--public-access-block-configuration "BlockPublicAcls=false,IgnorePublicAcls=false,BlockPublicPolicy=true,RestrictPublicBuckets=true"
```

```sh
aws s3api get-public-access-block \
--bucket acl-example-ms-1
```


## Change the Bucket Ownership

```sh
aws s3api put-bucket-ownership-controls \
--bucket acl-example-ms-1 \
--ownership-controls="Rules=[{ObjectOwnership=BucketOwnerPreferred}]"
```


## Change ACLs to allow for a user in another AWS Account

```sh
aws s3api put-bucket-acl \
--bucket acl-example-ms-1 \
--access-control-policy file:///workspace/AWS-SAA-C03-Examples/s3/acls/policy.json
```

## Accesss Bucker from other Account

```sh
touch test.txt
aws s3 cp test.txt s3://acl-example-ms-1
aws s3 ls s3:acl-example-ms-1
```

## Cleanup

```sh
aws s3 rm s3://acl-example-ms-1/test.txt
aws s3 rb s3://acl-example-ms-1
```