


working area---->index area/staggingarea---------->local Repo------------>Central Repo/Remote repository


git add:  working area---->index area/staggingarea

git commit:index area/staggingarea---------->local Repo

git push: local Repo------------>Central Repo/Remote repository

commands:

git add filesname

 git commit -m "commiting cloudwatch.md and docker.md"

 git remote add origin https://github.com/Bosugit/AWSDevopsTopics.git

git push -u origin master



if you want to create new branch:  git checkout -b 


from master branch to feature branch:

    git checkout -b feature-branch master