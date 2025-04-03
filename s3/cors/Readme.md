# Create Website 1

## Create a bucket policy

```sh
aws s3 mb s3://cors-example-ms-01
```


## Change block public access

```sh
aws s3api put-public-access-block \
--bucket cors-example-ms-01 \
--public-access-block-configuration "BlockPublicAcls=true,IgnorePublicAcls=true,BlockPublicPolicy=false,RestrictPublicBuckets=false"
```


## Create a bucket policy

```sh
aws s3api put-bucket-policy --bucket cors-example-ms-01 --policy file:///workspace/AWS-SAA-C03-Examples/s3/cors/bucket-policy.json
```


## Turn on static Webite hosting

```sh
aws s3api put-bucket-website --bucket cors-example-ms-01 --website-configuration file:///workspace/AWS-SAA-C03-Examples/s3/cors/website.json
```


## Upload out index.html and include a resource that would be cross-origin

```sh
aws s3 cp /workspace/AWS-SAA-C03-Examples/s3/cors/index.html s3://cors-example-ms-01
```


## View the website and see if the index.html is there.

It is for us-west-2
http://cors-example-ms-01.s3-website.us-west-2.amazonaws.com


Other regions might use a hyphen
http://cors-example-ms-01.s3-website-us-west-2.amazonaws.com



# Create Website 2

## Create a bucket

```sh
aws s3 mb s3://cors-example-ms-02
```

## Change block public access

```sh
aws s3api put-public-access-block \
--bucket cors-example-ms-02 \
--public-access-block-configuration "BlockPublicAcls=true,IgnorePublicAcls=true,BlockPublicPolicy=false,RestrictPublicBuckets=false"
```


## Create a bucket policy

```sh
aws s3api put-bucket-policy --bucket cors-example-ms-02 --policy file:///workspace/AWS-SAA-C03-Examples/s3/cors/bucket-policy2.json
```


## Turn on static Webite hosting

```sh
aws s3api put-bucket-website --bucket cors-example-ms-02 --website-configuration file:///workspace/AWS-SAA-C03-Examples/s3/cors/website.json
```


## Upload our javascript file

```sh
aws s3 cp /workspace/AWS-SAA-C03-Examples/s3/cors/hello.js s3://cors-example-ms-02
```

## Create API Gateway with mock response and then test the endpoint

```sh
curl -X POST https://oo85wt8zt9.execute-api.us-west-2.amazonaws.com/prod/hello -H "Content-Type: application/json"
```

## Set CORS on our bucket

```sh
aws s3api put-bucket-cors --bucket cors-example-ms-01 --cors-configuration file:///workspace/AWS-SAA-C03-Examples/s3/cors/cors.json
```