## Create a new S3 bucket

```md
aws s3 mb s3://checksum-example-ms-01
```

## Create a file that will we do a checsum on

```md
echo "Hello World!" > myfile.txt
```

## Get a checsum of a file for md5

```md
md5sum myfile.txt
# 8ddd8be4b179a529afa5f2ffae4b9858  myfile.txt
```


## Upload created file and check its etag
```md
aws s3 cp myfile.txt s3://checksum-example-ms-01
aws s3api head-object --bucket checksum-example-ms-01 --key myfile.txt
```

## Lets upload a file with different kind of checksum

```sh
aws s3api put-object \
--bucket="checksum-example-ms-01" \
--key="myfile.txt" \
--body="myfile.txt" \
--checksum-algorithm="SHA1" \
--checksum-sha1="YTBiNjU5Mzk2NzBiYzJjMDEwZjRkNWQ2YTBiM2U0ZTQ1OTBmYjkyYg=="
```