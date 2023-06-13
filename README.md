# Blue-Green-Deployment-AWS

# In-place deployment

![image](https://github.com/jeelkanani/Blue-Green-Deployment-AWS/assets/80504844/991b84f8-9cb4-4f23-95b5-a94343de1888)


Let's Our Application run on in place deployment and in future we need to update our application with newer version.


![image](https://github.com/jeelkanani/Blue-Green-Deployment-AWS/assets/80504844/cb01e36b-4b9e-49c7-8797-667939fa0e2b)


Now we are updating our application with newer version but after updating user may be face issue with newer vesion so in this case we can not roll back in previous
version. Only option remaing are to configuring whole application to start that's process literally time taking and giving bad user experience of our appilication.
so, overcome this issue use another deployment process for production.


# Blue-Green Deployment

![image](https://github.com/jeelkanani/Blue-Green-Deployment-AWS/assets/80504844/74860bee-76d9-41a1-a48c-4aaabccf0422)

Blue-green deplyment overcome in-place deploment issue. In this deployment contains two envirenment 
1) Blue Env (Live)
2) Green Env 

Blue Env is live Env all our application all traffic goes through Load Balancer this blue env.

![image](https://github.com/jeelkanani/Blue-Green-Deployment-AWS/assets/80504844/124a6b06-34f4-4bef-bc8c-1567854c967c)

In future we need to install new version of our application then aws codedeploy create exactly same replicaset as blue env and install new version top of this machine.

![image](https://github.com/jeelkanani/Blue-Green-Deployment-AWS/assets/80504844/418095ff-b6b7-4537-832f-bb83d1dd5645)

after sucessfully deploy new version of our application then Load Balancer point to the Green Env.

Benifits: we have still previou version of our application so in case some problem occured in our latest application so we directly point our load Balancer to privous version of our application.


