# Ecommerce-Serverless-aws
an example of how to build and run applications without having to manage infrastructure (Serverless Architecture) in the AWS cloud


## [1. Lets start first with cloning the repository](#1-let-start-first-with-cloning-the-repository)
## [2. To deploy run the following commands](#2-to-deploy-run-the-following-commands)
## [3. BACKEND](#%EF%B8%8F-backend)
## [4. FRONTEND](#-frontend)


# Application architecture

![arquitectura](https://epsagon.awsworkshop.io/images/welcome/architecture.png)





## Installing/Deploying the retail store

## 1. Let start first with cloning the repository

```bash
git clone https://github.com/epsagon/retail-store-workshop.git
cd retail-store-workshop  
```
*first of all add the lib in <requiriments.txt> `urllib3==1.26.6` is a Python library commonly used to make HTTP requests.*
## ⚙️ *BACKEND*

## 2. To deploy run the following commands. Make sure to replace `<REGION>` with your desired region. In our example we are using ```us-east-1```.

```plaintext
us-east-1
```

```bash
cd backend
sudo pip3 install boto3
npm install
npm install -g serverless
sls deploy --region <REGION> 
```
Upon successful deployment, we can see the following output:
___
*Note: If there are any errors, don't worry, try modifying line 15 of Serverless.yml. Check that you have `runtime: python3.9` and not <runtime: python3.7> or whatever you have set*

![imagen2](https://epsagon.awsworkshop.io/images/prerequisites/sls_deploy.png)

3. Make sure to copy the endpoint, because we can use it soon.
    Now let’s create some items in our stock
```bash 
python update_db.py 4 <REGION>
```
`update_db.py` script puts items (in this case 4) into our DynamoDB. Make sure to use the same region as before.

## 🔷 *FRONTEND*

3. "Change to the 'frontend' directory, globally install Yarn and 'scottyjs', then use Yarn to install the frontend project dependencies."
```bash 
cd ../frontend
npm install -g yarn scottyjs
yarn install
```
4.Now, let’s copy the endpoint to the file frontend/src/config.js:

![arquitectura](https://epsagon.awsworkshop.io/images/prerequisites/configjs.png)

5.Make sure to change only to hostname part, and leave the string ending with /dev.

  Now we can deploy our frontend:

```bash 
npm run build
scotty --nocdn --spa --source ./build -b <BUCKET_NAME> -r <REGION>

```
in this case we use
```bash 
npm run build
aws s3 cp ./build s3://catalog-shop-dev-serverlessdeploymentbucket-ijfqa9bzlgwu --recursive
```

Instead of `<BUCKET_NAME>` choose a unique name for the S3 bucket that will be created for the website. It can be any name! In the example, we are `using observability-workshop-ranrib`.

Type in the region as the same `<REGION>` you’ve used before

## 🛠 Tools
[![Amazon CloudFront](https://img.shields.io/badge/Amazon_CloudFront-FF9900?style=for-the-badge&logo=amazon-cloudfront)](https://aws.amazon.com/cloudfront/)
[![Amazon S3](https://img.shields.io/badge/Amazon_S3-FF9900?style=for-the-badge&logo=amazon-s3)](https://aws.amazon.com/s3/)
[![AWS Lambda](https://img.shields.io/badge/AWS_Lambda-FF9900?style=for-the-badge&logo=amazon-aws)](https://aws.amazon.com/lambda/)






## visualize ecommerce with Amazon CloudFront to deliver content with lower latency!

[![web-site](https://img.shields.io/badge/ver_sitio_web-FF9900?style=for-the-badge&logo=amazon-aws&logoColor=white&labelColor=24292E&logoWidth=40&logoHeight=40)](https://dclqwvpm3pyr3.cloudfront.net)








