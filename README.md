# aws-matter-pki-template
English follows Chinese | 中文在前，英文在后
利用AWS解决方案简化 Matter PKI 部署。
原仓库地址为https://github.com/aws-samples/aws-private-ca-matter-infrastructure
本仓库包含创建 Matter PAA 和 PAI 的 Cloudformation 模板和相应的lambda代码。
具体操作步骤如下：
1. 创建S3桶存放仓库文件，桶名为 <AWS_ACCOUNT_ID>-matter-cfn-deployment-assets，请用实际的 account id 替换<AWS_ACCOUNT_ID>。
2. 上传本仓库中的所有文件到第一步创建的存储桶根路径下。
3. 打开Cloudformation服务，创建新堆栈，选择PAAStack.yaml的Amazon S3 URL。
   a. 如果想PAA证书只包含证书CN字段，选择PAAStack-Subject-CN-Only.yaml文件。
   b. 如果想PAA证书只包含CN字段，且创建 Non-VID Scoped PAA，选择PAAStack-Subject-CN-Only-Non-Scoped-VID.yaml文件。
4. 继续创建新堆栈，选择PAIStack.yaml的Amazon S3 URL。
   a. 如果想PAI证书只包含证书CN字段，选择PAIStack-Subject-CN-Only.yaml文件。
5. 上传DAC证书签名请求文件到创建PAI证书堆栈时指定的S3存储桶，上传s3 uri 格式为：s3://<创建PAI堆栈指定的DAC证书存储桶>/arn:aws:acm-pca:<region>:<account>:certificate-authority/<PAI UUID>/<PID>/xxx.csr。
6. 在DAC证书csr文件同目录下即可看到生成的DAC证书文件。


---
leverage AWS solution to simplify the Matter PKI setup
The original github repository is https://github.com/aws-samples/aws-private-ca-matter-infrastructure.
This repository contains Cloudformation templates and corresponding lambda codes for creating Matter PAA and PAI.
The specific steps are as follows:
1. Create an S3 bucket to store the repository files. The bucket name is <AWS_ACCOUNT_ID>-matter-cfn-deployment-assets. Please replace <AWS_ACCOUNT_ID> with the actual account id.
2. Upload all files in this repository to the root prefix of the bucket created in the first step.
3. Open the Cloudformation service, create a new stack, and select the Amazon S3 URL of PAAStack.yaml.
    a. If you want the PAA certificate to only contain the certificate subject CN field, select the PAAStack-Subject-CN-Only.yaml file.
    b. If you want the PAA certificate to contain only the CN field and create a Non-VID Scoped PAA, select the PAAStack-Subject-CN-Only-Non-Scoped-VID.yaml file.
4. Continue creating a new stack and select the Amazon S3 URL for PAIStack.yaml.
    a. If you want the PAI certificate to contain only the certificate CN field, select the PAIStack-Subject-CN-Only.yaml file.
5. Upload the DAC certificate signing request file to the S3 bucket specified when creating the PAI certificate stack. The upload s3 uri format is: s3://<DAC certificate bucket specified when creating the PAI stack>/arn:aws:acm-pca: <region>:<account>:certificate-authority/<PAI UUID>/<PID>/xxx.csr.
6. You can see the generated DAC certificate file in the same directory as the DAC certificate csr file.
