# Authenticate to a public registry: aws ecr-public get-login-password --region us-east-1 | docker login --username AWS --password-stdin public.ecr.aws
FROM public.ecr.aws/lambda/python:3.8-x86_64@sha256:8808c4978361e7eaf68d4de71af8d43c61159068205f37480e96a54b15885cfd

RUN yum update -y && yum install -y openssl
COPY *.py ${LAMBDA_TASK_ROOT}/
#COPY ../common_libs/*.py ${LAMBDA_TASK_ROOT}

COPY requirements.txt  ./
RUN  pip3 install -r requirements.txt --target "${LAMBDA_TASK_ROOT}"


CMD ["ssl_api_handler.lambda_handler"]