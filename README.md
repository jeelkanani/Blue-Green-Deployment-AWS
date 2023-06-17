# Blue-Green-Deployment-AWS

# In-place deployment

![image](https://github.com/jeelkanani/Blue-Green-Deployment-AWS/assets/80504844/991b84f8-9cb4-4f23-95b5-a94343de1888)


Let Our Application run on in place deployment and in future we need to update our application with newer version.


![image](https://github.com/jeelkanani/Blue-Green-Deployment-AWS/assets/80504844/cb01e36b-4b9e-49c7-8797-667939fa0e2b)


Now we are updating our application with a newer version but after updating users may face issues with the newer version so, in this case, we can not roll back in previous version. Only option remaing are to configuring whole application to start that's process literally time taking and giving bad user experience of our appilication.
so, overcome this issue use another deployment process for production.


# Blue-Green Deployment

![image](https://github.com/jeelkanani/Blue-Green-Deployment-AWS/assets/80504844/74860bee-76d9-41a1-a48c-4aaabccf0422)

Blue-green deployment overcomes in-place deployment issues. This deployment contains two environments 
1) Blue Env (Live)
2) Green Env 

Blue Env is live Env all our applications all traffic goes through Load Balancer this blue env.

![image](https://github.com/jeelkanani/Blue-Green-Deployment-AWS/assets/80504844/124a6b06-34f4-4bef-bc8c-1567854c967c)

In the future, we need to install a new version of our application then aws code deploys to create exactly the same replica set as blue env and install a new version on top of this machine.

![image](https://github.com/jeelkanani/Blue-Green-Deployment-AWS/assets/80504844/418095ff-b6b7-4537-832f-bb83d1dd5645)

after successfully deploy a new version of our application then Load Balancer points to the Green Env.

Benefits: we have still the previous version of our application so in case some problem occurred in our latest application so we directly point our load Balancer to the previous version of our application.


# Application Architecure

![image](https://github.com/jeelkanani/Blue-Green-Deployment-AWS/assets/80504844/2b377d20-a8fd-43b2-b38c-aebfa59b71f5)

first, we will create a pipeline using code pipeline after creating an s3 bucket for storing artifacts of code pipeline and use code deploy for creating green Env.

1) create two IAM Roles..... 
 ![image](https://github.com/jeelkanani/Blue-Green-Deployment-AWS/assets/80504844/0ca4da90-55bc-4193-858e-c3f59774232c)

2) create launch configuration.....
![image](https://github.com/jeelkanani/Blue-Green-Deployment-AWS/assets/80504844/5431a941-0748-4903-b007-d932c4e32937)

3) create auto scaling group.....
 ![image](https://github.com/jeelkanani/Blue-Green-Deployment-AWS/assets/80504844/64a91787-7be9-4e3e-9035-cedb1ddf9c1e)

4) Assign load balancer inside auto scaling group....
  ![image](https://github.com/jeelkanani/Blue-Green-Deployment-AWS/assets/80504844/34d3b050-6a40-43fd-b64b-e53dff225982)
  ![image](https://github.com/jeelkanani/Blue-Green-Deployment-AWS/assets/80504844/40897cca-02b6-44f2-ac33-ab2ae13c38ed)

5) now we see that automatically createing two intance...
  ![image](https://github.com/jeelkanani/Blue-Green-Deployment-AWS/assets/80504844/6c42d10f-8296-4033-9f81-2cc3d5f53b25)
  
6) Now create s3 bucket two store artifact of codepipeline...
  ![image](https://github.com/jeelkanani/Blue-Green-Deployment-AWS/assets/80504844/063e1b0f-4f26-40cc-8193-e5b0b09bfbcd)

7) create application using codedeploy and configuring deployment settings...
  ![image](https://github.com/jeelkanani/Blue-Green-Deployment-AWS/assets/80504844/e4ddf824-98b5-4640-9e4e-022926f46463)
  ![image](https://github.com/jeelkanani/Blue-Green-Deployment-AWS/assets/80504844/4489ff8d-5dcf-4db0-8001-b75524cf90de)
  ![image](https://github.com/jeelkanani/Blue-Green-Deployment-AWS/assets/80504844/b1a79baa-8d31-4de0-be3e-aab426875317)

8) create codepipeline.....
  ![image](https://github.com/jeelkanani/Blue-Green-Deployment-AWS/assets/80504844/c039c8e8-ba1c-4701-be19-e44f83d748e9)
  
  --) select where store artifact of our application in our case s3
   ![image](https://github.com/jeelkanani/Blue-Green-Deployment-AWS/assets/80504844/e2c7a002-4b02-493c-965b-bd5ecc521723)

9) now check our load balancing are prefectly work or not...
   ![image](https://github.com/jeelkanani/Blue-Green-Deployment-AWS/assets/80504844/dae6a728-57a0-4ce5-b712-8b9c67383092)

10) now show status of creating codepipeline...
   ![image](https://github.com/jeelkanani/Blue-Green-Deployment-AWS/assets/80504844/2d2d0144-48b6-44a5-b10f-08910e4d6403)

11) Here we can see that after creating pipeline codedeploy creating two more instace for green envirenment and installing new version top of them...
   ![image](https://github.com/jeelkanani/Blue-Green-Deployment-AWS/assets/80504844/3ebd59ea-37e1-4f6d-8a17-9b58b9e6cbda)
   ![image](https://github.com/jeelkanani/Blue-Green-Deployment-AWS/assets/80504844/dc7dac7a-9649-455a-999c-341c34746855)
   
12) after reroting we see that... 
    ![image](https://github.com/jeelkanani/Blue-Green-Deployment-AWS/assets/80504844/5fc7fc14-6a4a-4c91-83f6-2b64e74dd2e9)






