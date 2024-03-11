# Release-UnUsed-ElasticIP-(AWS)

## Project Description:

## Overview :

![1](https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/d6a029e7-f8fa-4dc8-8a01-fac57a473faa)

What is Cloud9 ?

Cloud9 is an integrated development environment (IDE) provided by Amazon Web Services (AWS). It allows developers to write, run, and debug code directly in the cloud, eliminating the need for local development environments. Cloud9 supports various programming languages, including Python, JavaScript, PHP, Ruby, and more.

## Step-by-Step Implementation:
## Steps :
### Step 1:- Select an cloud9 service in aws console and create an environment for it. Given name for the environment , environment type , instance type , timeout and create it.

![2](https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/a8aaeac1-1660-4c30-8d4e-cc07c6270a98)

![3](https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/360be990-f712-4864-8841-115de938a1a5)

### After Creating Cloud9 Environment it will automatically create EC2.

![4](https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/14d20a60-551a-4e9b-93d3-08a5ca7303e0)

### For that instance we need to add a policy i.e.- EC2FullAccess.
![5](https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/3766c631-3676-4e20-abd8-60892a0faf23)











### Creating Source and Designation s3 Buckets :

1. Navigate to the S3 Console.
2. Follow the Outlined Steps below.


<img width="1792" alt="1" src="https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/c8d11929-7406-415d-b6da-ad2509d97368">



- Create two buckets (1-Source and 2- Destination Bucket) with unique name and keep all the other setting to default while creating bucket.

  
<img width="1791" alt="2" src="https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/d2d1ad44-6356-44c3-8ae6-fcc401361338">


3. As you can see above , I have created two buckets one is Source bucket and another one is Destination bucket.

### Step 2 :
### Creating the SNS Notification :

1. Navigate to the SNS console.
2. Follow the Outlined Steps below.


<img width="1792" alt="3" src="https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/8767ece3-0892-41ba-8563-9e07c72781bf">


- Select Standard give some unique name and then scroll down and create Topic.(Keep all others things default)


<img width="1792" alt="4" src="https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/c6442af8-8385-4578-b04e-d5b5d2cd9206">


- After creating topic then go to subscription and create it.
  

<img width="831" alt="5" src="https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/f6741cd0-10e9-4638-b3a2-1ec6142d7352">


<img width="830" alt="6" src="https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/f25eaad6-5828-4605-8b50-640c488f7384">


<img width="832" alt="7" src="https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/99141dcc-0bb4-41c7-977c-395589d95b2f">



3. Scroll down and Click "Create subscription" <br>
4. After this , you will receive some mail for Subscription Confirmation and you have to confirm that.<br>
5. You can use any other protocols also like SQS, HTTP, SMS etc .,<br>


<img width="471" alt="8" src="https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/74a97056-134e-4802-b396-713a846172cc">


<img width="472" alt="9" src="https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/eba7acf1-c7fb-4158-b987-f5b556c14ac9">




### Step 3 :
### Creating the Lambda :

1. Navigate to the Lambda Console.
2. Follow the Outlined steps below.

<img width="831" alt="10" src="https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/fd1f9db1-31fc-402e-b4da-760881f3c769">



<img width="829" alt="11" src="https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/4e5544a2-118b-4973-a31d-c7d20b304128">

3. Now replace the default code with the image-resizing-s3.py and deploy the changes , Don't test the code now we have to do some more actions before testing.
4. After that , We have to give some permission for our Lambda Function to do our process (resizing) , For that navigate to the IAM Console and follow the below steps.


<img width="830" alt="12" src="https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/8a7b6586-5154-429b-802a-0e354b3eb563">

<img width="829" alt="13" src="https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/62162585-0b0a-48bf-8881-c5fce93b263a">


<img width="830" alt="14" src="https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/fc524c4c-6cf8-4f23-821a-698527c62c12">


<img width="833" alt="15" src="https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/a7838e65-4a6c-44fb-92dc-f8e07091628b">


<img width="832" alt="16" src="https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/b847c9e1-c973-4c6b-ade9-8ca64212f954">


<img width="831" alt="17" src="https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/d9fada45-7819-4c3c-abd5-270b997729bb">


<img width="836" alt="18" src="https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/eceb7b6f-8f20-4ac6-828e-19a5779676ed">

5. Now navigate to the Lambda Console and follow the steps below.


<img width="830" alt="19" src="https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/f5964f96-4976-48c3-a968-59e01d438f71">


<img width="834" alt="20" src="https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/21be1aa0-f862-4e5a-99c8-e49fdc79c87f">


<img width="829" alt="21" src="https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/79e9e252-436d-49c0-9e9f-0c4c35d553d3">


6. Now we have to trigger the function.


<img width="833" alt="22" src="https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/b6761d0d-8b2e-4b96-8150-90fc142ee9d8">


<img width="832" alt="23" src="https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/54562e6e-c453-4a1f-a948-fa3ec318df26">


<img width="832" alt="24" src="https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/89ee0f93-0602-4bd1-a1aa-578dbbb3dda3">


7. Now we have to go to code section , and scroll down to  layers.<br>
8. We have to add layer .<br>
9. May be you can think , why ?<br>
10. It's because for resize the image we upload in our source S3 bucket , We need a python library called pillow in our code to resize the image . We can manually add Pillow library also, But it's very time consuming and you have to do lot more , Instead of manually adding pillow library we are going to use layers for Some easy action.<br>
11. Follow the outlined Steps below.


<img width="830" alt="25" src="https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/c40cfad4-2ded-4819-a209-edd99532e889">

<img width="831" alt="26" src="https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/15aa09b1-8264-4c08-86e9-b40a9233c2bc">

12.You can copy the arn from below.

```
arn:aws:lambda:ap-south-1:770693421928:layer:Klayers-p39-pillow:1
```

13. After done all the actions above , now we can test our code.

<img width="830" alt="27" src="https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/a8ba51aa-73ca-40c4-a035-63ede3dffcc7">


<img width="830" alt="28" src="https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/b9f7438d-3242-4984-995e-282a9c83c251">

14. It will show some results like below , It runs successfully but return some error because we still not upload the images in S3 yet.


<img width="833" alt="29" src="https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/61224fd9-8a6d-4a16-a183-fb7bdea3b058">


### Step 4 :
### Results :

1. Navigate to the S3 Console.
2. Upload Some images in  Source Bucket.


<img width="830" alt="30" src="https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/89b351ad-74c7-4eb1-9526-cba7ac56170d">



<img width="829" alt="31" src="https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/61f63edd-a519-4e74-bb2a-66004abdd6c4">


<img width="831" alt="32" src="https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/95f173fe-75cb-425f-ae08-884a53b771da">


<img width="830" alt="33" src="https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/ac345aeb-45b0-47e0-8448-cc6993589cb6">


<img width="832" alt="34" src="https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/4fbffc99-cc99-4f9b-815d-f68a03a035ac">


<img width="832" alt="35" src="https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/b8e3d64d-c97b-4b86-bb94-88f5daae9f7f">


<img width="539" alt="36" src="https://github.com/KadlagV-05/Image-Resizing-Using-S3-SNS-Lambda/assets/118795133/af8e54cd-f28c-487d-bf92-f1364dd0b578">

### It Successfully resized the Image and sends me the Notification.


