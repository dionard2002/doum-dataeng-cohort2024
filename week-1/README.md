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
