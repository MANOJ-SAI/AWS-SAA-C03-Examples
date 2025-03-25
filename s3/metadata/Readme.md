## Create a bucket

```md
aws s3 mb s3://metadata-example-ms-01
```

### Create a new file

```md
echo "Hello World!" > hello.txt
```


### Upload file with metadata

```md
aws s3api put-object --bucket metadata-example-ms-01 --key hello.txt --body hello.txt --metadata Universe=world
```


### Get Meta data through head object 

```md
aws s3api head-object --bucket metadata-example-ms-01 --key hello.txt
```

## Clean the created buckets

```md
aws s3 rm s3://metadata-example-ms-01/hello.txt

aws s3 rb s3://metadata-example-ms-01
```