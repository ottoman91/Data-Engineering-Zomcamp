Introduction to Docker
================
Usman Khaliq
2023-05-13

-   <a href="#why-should-we-care-about-docker"
    id="toc-why-should-we-care-about-docker">Why Should we care about
    docker?</a>
-   <a href="#running-docker" id="toc-running-docker">Running Docker</a>
-   <a href="#dockerfile" id="toc-dockerfile">Dockerfile</a>

Video
[Link](https://www.youtube.com/watch?v=EYNwNlOrpr0&list=PL3MmuxUbc_hJed7dXYoJw8DoCuVHhGEQb)

-   Docker provides containers that are isolated from the rest of the
    system.

-   A data pipeline is just a fancy name for a process that inputs a
    data file etc. and then outputs another data artifact. In a data
    pipeline, there could be several other things that are processed.

-   A self serviced comtainer will have all of the softwares,
    configurations etc that it needs to run.

-   We can have several Docker containers running on the same host
    machine, which prevents us from running or installing any of the
    softwares on our own host machine from scratch.

-   We can easily take a Docker container and run it in a different
    environment, eg on an Ubuntu machine, on an AWS instance etc.

## Why Should we care about docker?

-   Easy for reproducibility

-   Run local experiments easily

-   Set up Integration Tests(CI/CD)

-   Running pipelines on the cloud (AWS Batch, Kubernetes jobs)

-   Spark

-   Serverless(AWS Lambda, Google Functions)

## Running Docker

-   Run `docker run hello-world` to check that Docker is running
    properly. (You might need to run Docker manually in Mac to start it
    first)

-   To run a docker container interactive, use the -it flag,
    e.g. `docker run -it ubuntu bash` will run the ubuntu bash.

The bash in the command above is a parameter, it basically tells docker
to interactively fire up the ubuntu container and to then run bash in
it.

-   A dangerous command: `rm -rf / --no--preserve-root`. Removes
    everything.

-   Lets run python 3.9 interactively: `docker run -it python:3.9`

-   `entrypoint` defines what will open when we run a container. So for
    instance if we run `docker run -it --entrypoint=bash python:3.9`,
    this will open up bash when we run the python3.9 docker container.

## Dockerfile

-   We need a dockerfile so that at the time of instantiating a docker
    container, we can define what all libraries and dependencies etc the
    docker container needs.

-   `FROM` : specifies the base image file that we need to build from

-   `RUN` : specifies if we need to install any packages or libraries in
    the base image

-   `ENTRYPOINT`: specifies the entrypoint when we run the image.

-   `WORKDIR`: Specifies the working directory where all the files will
    be copied

-   `COPY`: specify the source file and the destination file on the
    Docker image

-   `docker build -t test:pandas .`

`test` is the name of the image that we build, `pandas` is its
version(can be any number too), `.` tells docker to build the image in
the same directory where we have the Dockerfile.

-   `docker run -it test:pandas`. Run this command to run the Docker
    image that you just build.
