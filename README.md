# lamda-testing


having issue with the incorrect binary or executable version, and you must ensure that you have compiled your Go function code specifically for the Linux environment, which is the runtime environment for AWS Lambda.

 Go binaries compiled for macOS or Windows will not work in Lambda

  Make sure you compile your Go code using the appropriate target architecture and operating system, such as GOOS=linux GOARCH=amd64 before creating the deployment package. for example GOOS=linux GOARCH=amd64 go build main.go


# Getting Started
* go mod tidy
* GOARCH=amd64 GOOS=linux go build main.go
* zip function.zip main
* aws lambda create-function --function-name (attach func name without bracket) --runtime go1.x --role arn:aws:iam::635281925770:role/lambda-2 --handler main --zip-file fileb://function.zip (and most importantly you need to write the go version here also)
* aws lambda invoke --function-name (your function name without bracket) --cli-binary-format raw-in-base64-out --payload '{"What is your name?": "kim", "How old are you?": "20"}' output.txt

So practically the output.txt will be created and it will output "{"Answer:":"kim is 20 years old!"}" in the situation here which is the determinant base on the output after my payload func here.