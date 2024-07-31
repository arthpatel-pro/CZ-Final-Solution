Task 1: Simple Node Js Application Deployment on Docker container

Description:
  - Create a Dockerfile for a simple Node.js application that listens on port 3000. The
	Dockerfile should use a lightweight base image, install dependencies, copy the
	application code, and specify the command to run the application.
	
Deliverable: Dockerfile


Solution:
	The solution requires to have 1)dockerfile to create a container image and 2) Node js code to build and run the application. Below is a File tree you can find in the GitHub repo, It contains Dockerfile to create image and package.json and app.js contains simple node js code


	Task 1/
	├── Dockerfile
	├── package.json
	└── app.js

	I have used node:lts-alpine3.20 as a base image as alpine is best for ultra-lightweight containers, smaller in size and secure. It can help in reducing build and deployment time. The Dockerfile contains  a description of all commands for further information.
	
	Once you clone the repo to the local system, Need to run the below commands to build and run the container. (Please make sure Docker or Docker desktop is installed on the system.)
	1) Navigate to folder "Task 1"
	2) Run the below command to Build an image
		docker build -t simple-light-node-js:1.0 .
	3) Run the below command to list Images and verify the newly created image.
		docker images
	4) Run one of the below commands to run the Docker Container:
		docker run -d -p 80:3000 --name simple-light-node-js-container simple-light-node-js:1.0  			// http://localhost
		docker run -d -p 3000:3000 --name simple-light-node-js-container simple-light-node-js:1.0  		    // http://localhost:3000
	5) To access the application use the respective URLs mentioned next to the command in the above step.