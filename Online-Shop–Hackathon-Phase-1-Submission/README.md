# Online_Shop_Application

## Git and GitHub Learning;
- First of all forked the online_shop repository and then cloned the repository to my local using below command
  
  ```
  git clone git@github.com:DevOpsWithG/online_shop.git
  ```
- Created a New branch feat/exposewith3000 to change default port from `5173` to `3000` and feat/dockerfile to add Dockerfile
  ```
  git checkout -b feat/exposewith3000
  git checkout -b feat/dockerfile 
  ```
- Pushed then new changes to my github repository using
  ```
  git push origin feat/exposewith3000
  git push origin feat/dockerfile
  ```
- Then on GitHub Created pull request to merge these changes with main branch (Hakathon branch)
  ![image](https://github.com/user-attachments/assets/c62d4ffb-28c9-4a8d-be99-f1860df47a29)

- Other basic commands used while performing git task
  
  ```
  git checkout feat/dockerfile
  git branch
  git switch feat/exposewith3000
  git status
  git add <file-name> or  git add .
  git commit -m "message"
  ```

## Linux Learning;
- Used some basic commands to create new directory, new files, list the files and directories etc
  ```
  mkdir hackathon
  cd hackathon 
  ls
  vim Dockerfile
  vim vite.config.js
  ```

## Docker Learning ;
- Created a docker file by understanding the code like application build using which code language, How application is building like npm run build, npm run dev understood from package.json
  ```
  FROM node:hydrogen-alpine3.21

  WORKDIR /app

  COPY . .

  RUN npm install && npm run build

  EXPOSE 3000

  CMD ["npm" , "run" , "dev" ]
  ```
- Then build docker image using this docker file (v1.0.4 updated version with 3000 port earlier versions are with 5173 port)
  ```
  docker build -t online-shop:v1.0.4 .
  ```
- Once image is build, ran application using below command
  ```
  docker run -d online-shop:v1.0.4
  ```
- Then tested and exposed it external world using AWS cloud by modifiying security group of instance with 3000
  ![image](https://github.com/user-attachments/assets/e03cd8a2-efb5-40e9-a5e8-8e8e653ff36c)

- Then I pushed this working docker imager to my dockerhub
  Before we push local image to docker hub repository we need to tag it so i used below commands
  
  ```
  docker tag online-shop:v1.0.4 ganesh51/online-shop:v1.0.4
  docker push ganesh51/online-shop:v1.0.4
  ```
- Verified it by logging to docker hub
  ![image](https://github.com/user-attachments/assets/b1933a63-c5a5-4842-9b08-ae89fa3e97f0)

### Continuing Learning with Shubham Bhaiya! . . .
