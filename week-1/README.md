## Installation of Docker
If you are on Windows, please follow this guide: 

https://docs.docker.com/desktop/setup/install/windows-install/

### System requirements for Windows
For unifromity, let us use WSL2 backend, x86_64. Also, check if your laptop is up to the hardware prerequisites to successfully run WSL (Windows 10 or 11).

Installation: https://learn.microsoft.com/en-us/windows/wsl/install

After installation, you may now proceed to downloading the Docker Desktop.

Installation: https://docs.docker.com/desktop/setup/install/windows-install/#system-requirements

## Containerization and Infrastructure as Code
If you have been checking out the syllabus of DataTalks as well as the Data Engineering for Beginners of freecodecamp, they all started their discussion on docker--or just containerization. 

The importance of it might flew pass some listeners, but here is a breakdown of its relevance in data engineering. 

> Containerization is a technology that allows developers to package an application and its dependencies, including libraries and runtime, into a single, self-contained unit called a container.

### Ano konek sa Data Engineering?
1. First and foremost, the most obvious answer, to reduce the "*it works on my machine*" problem. 
2. It isolates applications and their dependencies, preventing conflicts with other applications or the host system.
3. Containers are efficient, sharing the host operating system’s kernel and starting up quickly while consuming fewer resources.

Read more: https://rathi-ankit.medium.com/containerization-in-data-engineering-720b36f1c430#:~:text=Using%20containerization%20in%20data%20engineering,works%20on%20my%20machine%E2%80%9D%20problem.

### Now what about Infrastructure as Code (IaC)?
IaC is usually associated in the history of DevOps. Basically, it is a way of managing infrastructure like it was code. It gives us the benefits of using the code to create our own infrastrucure, like version control, faster and safer infrastructure deployments across different environments, and having up to date documentation of our infrastructure--basically, a blueprint.

Read more: https://www.xenonstack.com/insights/infrastructure-as-code-containers

Henceforth, the basis will be from the docker guide/docs itself.
### Build the app's image
To build the image, you'll need to use a Dockerfile. A Dockerfile is simply a text-based file with no file extension that contains a script of instructions. Docker uses this script to build a container image.

1. In the ```getting-started-app``` directory, the same location as the ```package.json``` file, create a file named ```Dockerfile``` with the following contents:

```
# syntax=docker/dockerfile:1

FROM node:lts-alpine
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "src/index.js"]
EXPOSE 3000
```

This Dockerfile starts off with a ```node:lts-alpine``` base image, a light-weight Linux image that comes with Node.js and the Yarn package manager pre-installed. It copies all of the source code into the image, installs the necessary dependencies, and starts the application.

2. Build the image using the following commands:

In the terminal, make sure you're in the ```getting-started-app ```directory. Replace ```/path/to/getting-started-app``` with the path to your ```getting-started-app directory```.

```
cd /path/to/getting-started-app
```

Build the image.

```
docker build -t getting-started .
```

The ```docker build``` command uses the Dockerfile to build a new image. You might have noticed that Docker downloaded a lot of "layers". This is because you instructed the builder that you wanted to start from the ```node:lts-alpine``` image. But, since you didn't have that on your machine, Docker needed to download the image.

After Docker downloaded the image, the instructions from the Dockerfile copied in your application and used ```yarn``` to install your application's dependencies. The ```CMD``` directive specifies the default command to run when starting a container from this image.

Finally, the ```-t``` flag tags your image. Think of this as a human-readable name for the final image. Since you named the image ```getting-started```, you can refer to that image when you run a container.

The ```.``` at the end of the ```docker build``` command tells Docker that it should look for the ```Dockerfile``` in the current directory.

### Start an app container
Now that you have an image, you can run the application in a container using the ```docker run``` command.

1. Run your container using the ```docker run``` command and specify the name of the image you just created:

```
docker run -d -p 127.0.0.1:3000:3000 getting-started
```

The ```-d``` flag (short for ``--detach``) runs the container in the background. This means that Docker starts your container and returns you to the terminal prompt.

The ```-p``` flag (short for ```--publish```) creates a port mapping between the host and the container. The ```-p``` flag takes a string value in the format of ```HOST:CONTAINER```, where ```HOST``` is the address on the host, and ```CONTAINER``` is the port on the container. The command publishes the container's port 3000 to ```127.0.0.1:3000``` (```localhost:3000```) on the host. Without the port mapping, you wouldn't be able to access the application from the host.

2. After a few seconds, open your web browser to http://localhost:3000. You should see your app.

3. Add an item or two and see that it works as you expect. You can mark items as complete and remove them. Your frontend is successfully storing items in the backend.

## So Why Care about Docker?
- Reproducibility
- Local experiments
- Integration tests (CI/CD)
- Running pipelines on the cloud (AWS Batch, Kunerbetes jobs)
- Spark
- Serverless

[You can watch this video](https://www.youtube.com/watch?v=EYNwNlOrpr0&list=PL3MmuxUbc_hJed7dXYoJw8DoCuVHhGEQb&index=7&t=387s)