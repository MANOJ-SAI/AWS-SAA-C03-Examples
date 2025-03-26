## Create a bucket

```md
aws s3 mb s3://class-storage-example-ms-01
```

## Create a file

```md
echo "Hello World!" > hello.txt

aws s3 cp hello.txt s3://class-storage-example-ms-01 --storage-class STANDARD_IA
```


## Cleanup

```md
aws s3 rm s3://class-storage-example-ms-01/hello.txt

aws s3 rb s3://class-storage-example-ms-01
```

