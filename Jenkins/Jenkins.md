
Interview explaination:

For CI process we are using jenkins,For CD process we are using ArgoCD.

And here we are using Docker as an agent the entire pipeline will be run in Docker container which is already installed jdk and maven.

Here we are using webhooks if any pull request in github,it notifies the jenkis and jenkins build will be trigger.


stage1:Checkout

   so in this stage checkout the code from the git repository
   
Stage2:Build and test   

      in this project build the project and create a JAR file, mvn clean package
	  
Stage3: Static code Analysis

    here we are using sonar qube to identify any vunatilbites in the code,if any findings it send the email notification,if it ok it move to next stage


Stage4: Build and Push Docker Image

    based on the dockerfile ,we are build the docker image and that image pushed into docker registry.
	  
	  docker build -t ${DOCKER_IMAGE} .
	    dockerImage.push()
	
	The entiere above ci process/
	
	
	The below is Cd process
	
	
stage5:update and deployment file

  here anothe reposotry we are maitaining for the kubenets manifest files.
  
  And we are replacing the newsly created image ,in the deployment.yml file.
  
  and will do commit on this deployment.yml file and pushed into the branch.
  
  
  so ARgocd contionuyly look up any changes in this git reposotry ,so it will synnch or it will do the changes in kubeners cluster with the recent changes.
  
  This is totaly about CI/Cd process.
  
  
*********************************************************************************************************************************************

code snippet:

pipeline{
    agetnt{
        docker{

        }
    }
    stages{
        stage('checkout'){
            steps{}
        }
        stage('Build and test'){
            steps{

                sh 'cd springbootapp && mvn clean package'
            }
        }
        stage('static code analysis'){
            steps{

                sh ''
            }
        }
        stage('Build and push the docker image'){
            enviornment{
                docker credential information
            }

            steps{

            }
            

        }
        stge('update deployment file'){

            steps{
                ...
              sh

                 sed replace the image tag in deployment.uyml file
                    git commit

                    git push 
              .....
            }
        }
    }
}
  
*******************************************************************************************************************************************************************


which jenkin version is used

what are the plugins is used.

     docker pipeline,sonar qube scanner,Maven Integration plugin,JUnit Plugin,
	 
	 Kubernetes Continuous Deploy Plugin: Provides the ability to deploy applications to Kubernetes clusters from Jenkins.
	 
	 Kubernetes CLI Plugin:                Allows running Kubernetes CLI commands within Jenkins Pipeline scripts.
	 
	 

current version of jenkins.
     2.440(3 months before)


***********************************************************************************************************************************************************************














****************************************************************************************************************************************************************************
That we have used docker as agent in our jenkins project ,we found very useful interms of cost and also interms of efficency and spinning and teraring down docker containers.



we will have git repossitory,let say we talking about java code.


Jenkins which is resposible for watching the commits on this repository or respobile for pull requests on this reposotory.
whenever pull requests created your jenkins piplines will be trigered.



let say java developer who commit the code in git repository ,now how does your jenkis get notified?


there are multiple ways to trigger jenkin pipelines but most efficent way is to use webhook.


webhook---->instead of watching jenkins your repostory,jenkins will not watch your repository.what happens git will send notfication to your jenkins.


in your github settings,there is action setting webhook,there is action like commit,pull request github hook will trigger.


Now whever developer createa a pull request it will send request to jenkins,ask jenkins to trigger pipeline.


while maven build if anyfailures you can send email notfiication ,in aws we can



if the build pass we can intergreate any security related tools,scanning tools here we are using sonar qube,if any security vunalribiltiy finding again sending email notification.

If no security vunarabilities you can proceed with docker image.to create docker image docker agent here.docker pipeline plugin.or docker build shell command to create docker image..

Send this docker image to a container registry.here container registry mean anything either dockerhub or ecr.





why webhooks are efficient ,if not webhooks, jenkings   pooling continuosly and build triggers,continuolsy build triggers to your git.




what type of jenkins file are you folloing.
alway go with declaritve jenkisn file.Declarive pipline are eassy to colllabrate.


what agent you are using in jenkisnfile?

here we are using docker agent which is very lightin weight,if you are using docker agent you no need to install any maven,or java or python


The above all things continuous integration.  at the end of this process you are image is ready.


Now CD continuos delivery:

for this peopel are used to ansible playooks or shell scripts.And they include cd also same in CI pipeline.


the problem is not scalble.ansible and shell script are not designed for continuos devliery.

So they are looking for contuos delivery tool that is in the gitops based tool ARgo CD.


in argocd:
similar to your sosurce code git reposotry ---------->pod.yml,service.yml,deploy.yml

if you are not using git source of truth for application manifest files then devops engineer directly go the kubenet cluster ,and he wil directly do modified pod.yml.in this case no verification ,no auditing ,code review.

so for this reason better to use git for applciation mainfest files.




Now you are created new image version in CI pipeline,how you will argocd/gitops tools come to know that there is new image in pod.yml or hemlchatt will be updated by the new image.

step1
ARgoImageupdater--->contiuosly monitory the docker hub registry

step2
ARgoImageupdater------->will notify and direclty update the pod.yml or hemlchart with newly created image..




ARgo CD is sitting in kubernet cluster,and its kubenrets controller and it will always maintain the state between your git repostotry and kubernets cluster.





explaination to inteviewer:


we have git reposotry where we have application source code let say java application.

And as soon as java developer pull the request to this git repostory we have cinfigured webhooks,usign the webhooks we triggering the jenkins pipeline.

we are used declaritve pipelines because declaritve pipeliens are easy pipline and colaborate.

As part of this jenkis pipelines there are multiple stages some of the are 

1.Build stage 
    |
	|sucess
	|
	|
	|--unit test cases
	
2.static code anlysis

3.SAST/DASt tools  security sonar qube.if any fails sendig email notifications.

4.Docker image

5.push the docker image into docker hub


cd process:

once the image opushed into containe regsitry,

we have k8s clsuter ,inside k8s cluster we have deployed to CD tools one is ARgoimage updater,ARGOCD.


the first tool ARgo image updater,it will contionuly monitor the image regsitry as soon as new image is created ,it will pick the new image and will updaste the new image in another git reposotory we have.

and this git reposotry for purly for image manfest files that is our helmchart or pod.yml


and other controle argocd ,it takes the new image and update to the kubernet cluster.

This is about the continuouly delivery process.
	   



stages:

Checkout----->Build and Test------>Static code Analysis------>Build and push Docker images--->update deployment file







*********************************************


can jenkinsfilename is anything answer is yes.

Can jenkinsfile path anywhre answer is yes,that path should be metnion .

by default sonar server port is 9000





**************************************************

just reminer what plugins we are used jenkins
Docker Pipeline plugins in jenkins
sonar Qube scanner

mange jenins:-->Manage credentials-->system-->global credentails-->






*********************************************************

in 3 tier application ,fronend and backend ubuntu and datbase is oracle running on centos,in this case maintianing the worker nodes are very difficult so we are using docker contaiers with multi stage and multi agents.

     stage('Back-end')
{
   agent{
     docker { image 'maven:3.8.1'}
}

}

 stage('front-end')
{
   agent{
     docker { image 'node:16'}
}

}


     



docker typically runs on a docker deamon process that runs on single source of truth of the docker.


by default docker deamon is not accessible to other users, so im installed docker as root ,only root user can access it.

if you want to  access other users also you need to give access.





doing myself in my local:

1.Create Ec2 instance t2 large

2.Need to install jenkins

3.Docker instllation

4

