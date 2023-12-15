# Ecommerce-Serverless-aws-


Esperando una descripcion
indices
## [1. Lets start first with cloning the repository](#1-let-start-first-with-cloning-the-repository)
## [2. To deploy run the following commands](#2-to-deploy-run-the-following-commands)
## [3. BACKEND part](#3-backend-part)

![arquitectura](https://epsagon.awsworkshop.io/images/welcome/architecture.png)


#*********************************************************************



# Other tittle
sample text............

............................................................
............................................................
.....................................................


## Installing/Deploying the retail store

## 1. Let start first with cloning the repository

```bash
git clone https://github.com/epsagon/retail-store-workshop.git
cd retail-store-workshop  
```
*antes que nada agregar la lib en <requiriments.txt>  `urllib3==1.26.6` es una biblioteca de Python utilizada comúnmente para realizar solicitudes HTTP.*
## ⚙️ *BACKEND part*

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
*Note: si hay algun error no se preocupe, intente modificando la linea 15 del Serverless.yml. Verifique que tenga   `runtime: python3.9` y no <runtime: python3.7>*

![imagen2](https://epsagon.awsworkshop.io/images/prerequisites/sls_deploy.png)

3. Make sure to copy the endpoint, because we can use it soon.
    Now let’s create some items in our stock
```bash 
python update_db.py 4 <REGION>
```
`update_db.py` script puts items (in this case 4) into our DynamoDB. Make sure to use the same region as before.

## 🔷 *FRONTEND part*

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
en este caso usamos
```bash 
npm run build
aws s3 cp ./build s3://catalog-shop-dev-serverlessdeploymentbucket-ijfqa9bzlgwu --recursive
```

Instead of `<BUCKET_NAME>` choose a unique name for the S3 bucket that will be created for the website. It can be any name! In the example, we are `using observability-workshop-ranrib`.

Type in the region as the same `<REGION>` you’ve used before

## 🛠 Herramientas
[![chartjs](https://img.shields.io/badge/Chart.js-FE777B?style=for-the-badge&logo=chart.js&logoColor=white)](https://www.chartjs.org/docs/latest/)
[![BootStrap](https://img.shields.io/badge/Vue.js-42B883?style=for-the-badge&logo=vue.js&logoColor=white)](https://vuejs.org/)
[![BootStrap](https://img.shields.io/badge/BootStrap-7952B3?style=for-the-badge&logo=bootstrap&logoColor=white)](https://getbootstrap.com/)


## visualizalo!

[![web-site](https://img.shields.io/badge/ver-sitio_web-pink?style=for-the-badge&logo=github&logoColor=white)](https://alicenon.github.io/mini-crud-cat/)



[![Logo](https://alicenon.github.io/portafolio/assets/img/portfolio/crud-cat-1.png)](https://alicenon.github.io/mini-crud-cat/)
