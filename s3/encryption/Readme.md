## Create a bucket

aws s3 mb s3://encryption-ms-01


### Create a file and Put Object with encryption SS3-S3

echo "Hello World!" > hello.txt
aws s3 cp hello.txt s3://encryption-ms-01


### Put Object with encryption

aws s3api put-object \
--bucket encryption-ms-01 \
--key hello.txt \
--body hello.txt \
--server-side-encryption aws:kms \
--ssekms-key-id 3f777025-6db0-4554-b278-123456789101c


### Put Object with SSE-C [not working]

export BASE64_ENCODED_KEY=$(openssl rand -base64 32)
echo $BASE64_ENCODED_KEY

export MD5_VALUE=$(echo -n $BASE64_ENCODED_KEY | md5sum | awk '{print $1}' | base64 -w0)
echo $MD5_VALUE

aws s3api put-object \
--bucket encryption-ms-01 \
--key hello.txt \
--body hello.txt \
--sse-customer-algorithm AES256 \
--sse-customer-key $BASE64_ENCODED_KEY \
--sse-customer-key-md5 $MD5_VALUE


### Put Object with SSE-C bia aws s3

openssl rand -out ssec.key 32


aws s3 cp hello.txt s3://encryption-ms-01/hello.txt \
--sse-c AES256 \
--sse-c-key fileb://ssec.key

aws s3 cp s3://encryption-ms-01/hello.txt hello.txt --sse-c AES256 --sse-c-key fileb://ssec.key