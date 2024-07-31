Task 1: Simple Node Js Application Deployment on Docker container

Description:
  - Create a Dockerfile for a simple Node.js application that listens on port 3000. The
	Dockerfile should use a lightweight base image, install dependencies, copy the
	application code, and specify the command to run the application.
	
Deliverable: Dockerfile


Solution:
	Solution require to have 1)dockerfile to create a container image 2) Node js code to build and run application. Below is File tree you can find in GitHub repo, It contains dockerfile to create image and package.json and app.js contains simple node js code


	Task 1/
	├── Dockerfile
	├── package.json
	└── app.js

	I have used node:lts-alpine3.20 as a base image as alpine is best for ultra-lightweight containers , smaller in size and secure. It can help in reducing build and deployment time. Dockerfile contains  description of all commands for further information.
	
	Once you clone repo to local system, Need to run below commands to build and run container. (Please make sure Docker or Docker desktop installed on system.)
	1) Navigate to folder "Task 1"
	2) Run Below command to Build image
		docker build -t simple-light-node-js:1.0 .
	3) Run Below command to list Images and verify newly created image.
		docker images
	4) Run one of below command to run the Docker Container:
		docker run -d -p 80:3000 --name simple-light-node-js-container simple-light-node-js:1.0  			// http://localhost
		docker run -d -p 3000:3000 --name simple-light-node-js-container simple-light-node-js:1.0  		    // http://localhost:3000
	5) To access application use respective URLs mentioned next to command in above step.