-
- ![image.png](../assets/image_1654071252803_0.png){:height 382, :width 1057}
- ## Docker Tutorial for Beginners         [Youtube]( https://www.youtube.com/watch?v=pTFZFxd5hOI&list=RDCMUCWv7vMbMWH4-V0ZXdmDpPBA&index=7)
	- ### What is Docker?
		- A platform for building, running and shipping applications
		- #### Why you need docker?
			- if you are an application developer, you might meet such questions before, the software works well on your develop computer, but does't work well on other computer, the main reason is :
				- One or more files missing
				- Software version mismatch
				- Different configuration settings
		- #### How Docker works?
			- With Docker, we can easily package our application with everything you need and running it anywhere and any machine with docker.
			- For example: if your application is given version of Node/Mongo/App, all of these will included in the application package, now you can take this package and run it at any machine that with docker,
			- And also, if you have a new team member, they don't need to spent half day to setting up their machine and deploy application, they don't need to install and configure all these dependencies. They simply type "docker" and the docker itself will automatically download and run the dependencies inside and isolated the environment called the **container**.
			- The isolated docker environment allows multiple applications use different versions of software side by side.
	- ### Virtual Machines VS Containers
		- |**Items**|**Container**|**Virtual Machine**|
		  |Differents  |An isolated environment for running an application|An abstraction of a machine(Physical hardware)|
		  | || ![image.png](../assets/image_1654072738805_0.png)|
		  |Software  |docker|VirtualBox, VMware, Hyper-v(Windows only)|
		  |Problems/Benefits  |1. Allow running multiple apps in isolation [:br]2. Are Lightweight [:br]3. Use OS of the host  [:br]4. Start quickly [:br]5. Need less hardware resources|1. Each VM needs a full-blown OS [:br]2. Slow to start [:br]3. Resource intensive|
		-
	- ### Architecture of Docker
		- Docker uses a client server architecture, so it has a client component that talks to a server component using a restful api, the server also called the docker engine sits on the background and takes care of building and running docker containers.
			- ![image.png](../assets/image_1654075453663_0.png)
		- Technically a container is just a process like other processes running on your computer but it's a special kind of process
			- ![image.png](../assets/image_1654075482287_0.png)
		- Unlike virtual machines, containers full-blown operation system instead all containers on a host share the operating system of the host, all these containers share the kernel of the host.
		- Docker on Windows/Linux/Macos
			- ![image.png](../assets/image_1654076143249_0.png)
			- We cannot run a windows application on linux because under the hood this application needs to talk to the kernel of the underlying operating system. That means on a linux machine, we can only run linux containers because these containers need linux.
			- On a windows machine, we can run both windows and linux containers, because windows 11 is now shipped with a custom built linux kernel, this is in addition to the windows kernel that's always been in windows, it's not a replacement, so with this linux kernel, now we can run linux applications natively on windows. So on windows we can run both linux and windows containers.
			- Macos has its own kernel which is different from windows and linux kernel, this kernel don't have native support for continuous applications, so docker on mac uses a lightweight linux virtual machine to run linux containers.
	- ### Installing Docker
		- Getstarted [Docker Installation](https://www.docker.com/get-started/)
	- ### Development Workflow
		- #### Workflow within docker
			- 2. To start off, we take an application, it doesn't matter what kind of application it is or how it's built, we take the application and dockerlize it, which means we made a small change so that can run on docker, how?
			- 3. We just add a **Dockerfile** to it, a docker file is a plain text file that includes instructions that docker uses to package up this application into an image, this image contains everything our application needs to run:
				- 2. Cut down operating system
				  2. A runtime environment (eg Node or python)
				  3. Application files
				  4. Third-party libraries
				  5. Environment variables
			- 4. So we create a docker file and give it to docker for packaging our application into an image
				- ![image.png](../assets/image_1654088942275_0.png)
			- 5. Once we have an image, we tell docker to start a container using that image, so a container as I told you is just a process but it's a special kind of process because it has its own file system which  is provided by the image.
			- 6. So, our application gets loaded inside a container or a process and this is how we run our application locally on our development machine
			- 7. Instead of directly launching that application and running it inside a typical process, we tell docker to run it inside a container, an isolated environment.
			- 8. Now here's the beauty of docker, once we have this image, we can push it to a docker registry like docker hub, docker hub to docker like github to git, it's a storage for docker images that anyone can use.
			- 9. Once our application image is on docker hub, then we can put it on any machines running docker, this machine has the same image we have on our development machine, which contains a specific version of our application with everything it needs.
			- 10. We can start our application the same way we started it on our development machine, we just tell docker to start a container using this image.
				- ![image.png](../assets/image_1654089049873_0.png)
		- So with docker, we no longer need to maintain long complex release documents that have to be precisely followed, all the instructions for building an image of an application are written in a docker file, with that, we can package our application into an image and run it virtually anywhere.
			-
	- ### Docker in Action
		- #### Create An Example Application
			- 2. create directory
				- `mkdir hello-docker`
				- ![image.png](../assets/image_1654090819695_0.png)
			- 3. go inside this directory
				- `cd hello-docker`
				- ![image.png](../assets/image_1654090842277_0.png)
			- 4. open this directory in visual studio code
				- `code .`
				- ![image.png](../assets/image_1654090864600_0.png)
			- 5. in this directory, add a new file called **app.js**
				- ![image.png](../assets/image_1654090910545_0.png)
			- 6. we're going to write one line of javascript code, in the **app.js** file
				- `console.log("Hello Docker!");`
				- ![image.png](../assets/image_1654091038401_0.png)
			- 7.  go back to the terminal, and run the file **app.js**
				- `node app.js`
				- ![image.png](../assets/image_1654091137771_0.png)
		- #### Dockerlize this Example Application
			- 2. add another file to this project called **Dockerfile**
				- ![image.png](../assets/image_1654091434508_0.png)
			- 3. edit the Dockerfile, write the docker instructions for packaging our application
				- 2. start from a base image, this base image has a bunch of files we're going to take those files and add additional files to it, this is kind of like inheritance in programming. we can start from a linux image, and then install node on top of it, or we can start from a node image, this image is already built on top of linux, now how do I know these names, these images are officially published on docker hub.
				  here we can specify a tag,   using a column to specify which linux distribution we want to use, for this demo, I'm going to use **alpine**, which is a very small linux distribution, so the size of the image that we're going to download and build on top of is going to be very small .
					- `FROM node:alpine`
					- ![image.png](../assets/image_1654092768902_0.png)
					- #+BEGIN_QUOTE
					  if you go to [hub.docker.com](hub.docker.com), and search for node, you can see the official node image here, docker hub is a registry for docker images
					  #+END_QUOTE
					- #+BEGIN_quote
					  if you look at docker hub, you will see that there are multiple node images these images are built on top of different distributions of linux, so linux has different distributions or different flavors used for different purposes.
					  #+END_quote
				- 3. we start form that image and then we need to copy our application or program files, for that we use **COPY** instruction or **COPY** command, we are going to copy all the files in the current directory into the app directory into that image, so that image has a file system and in that file system we're going to create a directory called app.
					- `COPY . /app`
					- ![image.png](../assets/image_1654092990971_0.png)
				- 4. we are going to set the current working directory **WORKDIR**, all the instructions assume that we're currently inside the app directory.
					- `WORKDIR /app`
					- ![image.png](../assets/image_1654093289176_0.png)
				- 5. use the command instruction to execute file or program
					- `CMD node app.js`
					- ![image.png](../assets/image_1654093383970_0.png)
				- 6. we go back to the terminal and tell docker to package up our application, so we give the docker a  tag to identify, and then we need to specify where docker can find a docker file, so we are currently inside **hello docker** directory, and our dockerfile is right here, so we use a period to reference the current directory.
					- ![image.png](../assets/image_1654093998980_0.png)
				- 7. when the image is created, you can't find any new file in the application directory, because the image is not stored here, and in fact **image is not a single file**, how docker stores this image is very complex and we don't have to worry about it.
				- 8. back to the terminal, to see all the images on this computer, we type:
					- `docker image ls`
					- ![image.png](../assets/image_1654093970495_0.png)
				- 9. now we can run this image on any computer running docker, so on this machine, which is my development machine, I can say `docker run hello-docker`, and it doesn't matter which directory I'm in, because this image contains all the files for running our application
					- ![image.png](../assets/image_1654094209875_0.png)
				- 10. we can go ahead and publish this image to docker hub so anyone can use this image, then i can go on another machine like a test or a production machine and pull and run this image..
				- 11. he has a image on the docker hub
					- ![image.png](../assets/image_1654094328369_0.png)
				- 12. now we can take this image and run it on any computer
					- for example, we can to to website [play-with-docker](labs.play-with-docker.com),  and start a new virtual machine.
					- pull the image
					- ![image.png](../assets/image_1654094521515_0.png)
					- verify the image
					- ![image.png](../assets/image_1654094567395_0.png)
					- run the image
					- ![image.png](../assets/image_1654094642927_0.png)
-