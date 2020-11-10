docker day 1
------------

* Class intro and expectations
* Intro to containers
* Why containers
* Connection to microservices and the 12 factor app
* Install Docker
* Run an image

intro to containers
-----------------------

Linux containers are an operating system level virtualization technology for providing multiple isolated linux environments on a single linux host. unlike virtual machines (vms), containers do not run dedicated guest operating systems.

A container is a standard unit of software that packages up code and
all its dependencies so the application runs quickly and reliably from
one computing environment to another.

To reiterate:

*A container is not a VM*

It is just another process on the machine
It uses namespaces and control groups (cgroups) to provide isolation.
Namespaces include network, process, user, IPC, mount, and others.

* [Evolution of containers](https://dzone.com/articles/evolution-of-linux-containers-future)

why containers?
---------------

By using containerization, the developer can assure that the application will run on any other machine regardless of any customized settings that machine might have that could differ from the machine used for writing and testing the code. It means that we can focus on writing code without worrying about the system that it will finally be running on. It also allows us to get a head start by using one of thousands of programs already designed to run in a Docker container as a part of their application.

* Move software reliably from one computing environment to the other. Solves the “works on my machine” problem.
* Lightweight compared to VMs.
* Faster startup times. Allows for “just-in-time” initiation.
* Allows for modular scaling when combined with Microservices
architecture.
* Ports and ips are isolated for each container in a way they don't interfere with other services on the machine.

*Links:*
* [When and why to user docker](https://www.linode.com/docs/guides/when-and-why-to-use-docker/)

twelve factor container
-----------------------

The twelve factor app is an influential collection of practical design principles which grew out of the experiences of the team at Heroku. See the original charter here: [12 factor app](https://12factor.net). In particular we will see how containers help with this design.

1. Codebase: one codebase tracked in revision control, many deploys
2. Dependencies: explicitly declare and isolate dependencies (Dockerfiles were made for this)
3. Config: strict separation of config from code
4. Backing services: foster loose coupling by treating backing services as attached resources
5. Build, release, run: strictly separate build and run stages
6. Processes: processes are stateless and share-nothing
7. Port binding: export services via port binding (Docker’s main communication method.
Supported by keywords like expose and can be easily mapped externally)
8. Concurrency: scale out via the process model
9. Disposability: processes are disposable, they can be started or stopped at a moment’s
notice (Docker containers are inherently disposable and can be easily duplicated or removed)
10. Dev/prod parity: Keep development, staging, and production as similar as possible (Docker
images are immutable)
11. Logs: treat logs as event streams, don’t manage log files (Docker logs to a stdout stream by
default. It’s up to you or your orchestration system to direct it)
12. Admin processes: admin and utility code ships with app code to avoid synchronization issues

*Links*
* [Tweleve factor container](https://medium.com/notbinary/the-twelve-factor-container-8d1edc2a49d4)
* [12 factor app](https://12factor.net)

install docker
--------------

Install and start docker so you can start playing with it

* [Install Docker Desktop on Mac](https://docs.docker.com/docker-for-mac/install/)
* [Install Docker Desktop on Windows](https://docs.docker.com/docker-for-windows/install/)

run a container
---------------

Run a container and learn what the commands and flags do

start a redis instance

    docker run --name my-redis -d --rm redis:alpine

exec into container

    docker exec -it my-redis /bin/ash

run a redis command

    redis-cli
    127.0.0.1:6379> set /my/key test
    127.0.0.1:6379> get /my/key
    127.0.0.1:6379> exit
    exit

stop the container

    docker ps
    docker stop my-redis
    docker ps

additional reading
------------------

* [Demystifying Containers – Part I](https://www.cncf.io/blog/2019/06/24/demystifying-containers-part-i-kernel-space/)
* [Demystifying Containers – Part II](https://www.cncf.io/blog/2019/07/15/demystifying-containers-part-ii-container-runtimes/)
* [Docker 101](https://www.docker.com/101-tutorial)
