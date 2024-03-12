# Release-UnUsed-ElasticIP-(AWS)

## Project Description:

## Overview :

<img width="695" alt="0 jpg" src="https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/392c61ca-cf17-4694-aeb7-e321cd2c4941">

What is Cloud9 ?

Cloud9 is an integrated development environment (IDE) provided by Amazon Web Services (AWS). It allows developers to write, run, and debug code directly in the cloud, eliminating the need for local development environments. Cloud9 supports various programming languages, including Python, JavaScript, PHP, Ruby, and more.

## Step-by-Step Implementation:
## Steps :
### Step 1:- Select an cloud9 service in aws console and create an environment for it. Given name for the environment , environment type , instance type , timeout and create it.

![2](https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/a8aaeac1-1660-4c30-8d4e-cc07c6270a98)

![3](https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/360be990-f712-4864-8841-115de938a1a5)

### After Creating Cloud9 Environment it will automatically create EC2.

![4](https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/14d20a60-551a-4e9b-93d3-08a5ca7303e0)

### For that instance we need to add a policy i.e.- EC2FullAccess. This we have done as follow (refer img)
![5](https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/3766c631-3676-4e20-abd8-60892a0faf23)


### after that we open Cloud9 IDE and we can see the access key and secret key credentials are taken from IAM Role by default.
![6](https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/330cc2e9-b693-4349-abcb-22e86b8d12a4)

### Now we create python file in cloud9 IDE. (we also check whether python is install or not)

## Note:- when we added policies in role refresh the cloud9 IDE otherwise the previous acces_key and secret_key will be in affect.

### BOTO-3 SDK is used in program So we need to Install boto3 in this enviroment.

### To install Boto3 Run the following command.

```
pip install boto3
```

### Then Create the python file to achive the output (i.e Release unused Elastic IP). Copy the following Code in file which you have created.(Check the proper indentations)

```
import boto3
client = boto3.client('ec2')
addresses = client.describe_addresses()['Addresses']
for eip in addresses:
    if ('AssociationId' not in eip) and ('NetworkInterfaceId' not in eip):
        print(eip['PublicIp'] + " is unused , releasing ")
        client.release_address(AllocationId=eip['AllocationId'])
    else:
         print(eip['PublicIp'] + " is used , not releasing")
```

### when we run the following code file you can see that unused IP's are releasing and used are still their as they are allocated to Instance.

![7](https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/2fc0b139-6f5d-4c16-8c94-60dace9ad596)


## Now we will automate this process as every time we can’t go and run the code. (So we will use Lambda and cloud Watch)

### Step2:- creating Lambda function (Fill all the mandatory sections and then click on create.) Refer-img
### 

![8](https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/e104776c-034d-4753-b107-3085dfd37004)

### After creating copy the same code and paste in lambda function code section with proper indentations. 

![9](https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/bef6bf6c-ccfe-4bc4-af4f-5c58052e1132)

### Then deploy and test the code it will show error as function is not authorised.

![10](https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/999c141c-4485-41a0-b481-3e52344d0b89)


### So Go To Configuration → permission → role name and add “ec2fullaccess” policy to it.(refer-img's)


![11](https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/4588c34f-b756-4dee-813a-4a87f6885099)

![12](https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/77c568ce-7bd3-4673-81e7-1f5fc5ea69ec)

### After this again try to test the code it will successfully get executed.

![13](https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/2cd17466-f9a4-47d9-a6f0-1147c6e92f04)

### Now its manual process so we will automate it by adding trigger from cloud-watch as we can see all the lambda logs in cloud watch.

## Adding trigger 

![14](https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/87739db5-5b3e-4581-b44a-25090b5dadd1)

### So we have sucessfully added trigger to Lmabda function so after 1 minute the unused ElasticIP will automatically get removed.


![15](https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/8b88fec6-8495-4601-b643-d7a5728d8556)
### Following elasticIp is in unused state.

![16](https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/87aa4b5b-9a63-4f9b-b99e-3c6a91fee335)

### After 1 min ElasticIP was removed as it was in unused state.


## Thank you.









