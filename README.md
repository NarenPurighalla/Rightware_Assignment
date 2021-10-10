###### This is the README file for the tasks sent by Tiina Eronen for Rightware

All the tasks were done on a machine with Ubuntu 18.04 as the OS

After reading the instructions part of the document, I broke down the list of tasks into three.

The details of how each task is performed is written below

## Task-1

In this task, I was asked to create a Vagrantfile to initialize the docker container. The Vagrantfile is part of the repository under "Task1" folder.

I'm mindful that it was a very basic Vagrantfile which doesn't use many features, but since I was just asked to initialize the docker container without worrying about what the docker container should do, I went with this option.

The steps to check before running this vagranfile are:
  - to make sure that docker is installed in the system.
  - to make sure vagrant is installed in the system.

Then you can run the Vagrantfile using this command from the same location as the Vagrantfile
```console
vagrant up
```
The docker container should be running and it can be checked using:

```console
docker ps
```


## Task-2

In this task, I was asked to write a dockerfile that will install the necessary packages and expose its SSH and application interfaces and also be able to SSH to the container.

The Dockerfile required for this task is in the Task2 directory

These are the following steps:
  - Write the Dockerfile. Comments are provided in the dockerfile to make it easy
  - Build the image using:
    ```console
    docker build -t <name_of_the_image> .
    ```
  - After the image is built, run the docker container using:
    ```console
    docker run -d -t --name <name_of_the_container> <name_of_the_image>
    ```
  - Check if the container is running
    ```console
    docker ps
    ```
  - Check the IP Address of the container:
    ```console
    docker inspect <name_of_the_container> | grep 'IPAddress'
    ```
  - SSH to the container:
    ```console
    ssh sshuser@<IPAddress> #The password for this user is sshtask (you can change it from the DOckerfile)
    ```

## Task-3

In this task, I was asked to create a webapp in a docker container using ansible script and demo it

The Dockerfile, the ansible playbook and the ansible parameters file required for this task are in ansible_webapp directory.

For this task, I chose the "snake" game that runs on browser that can be cloned from https://github.com/epidemian/snake.git 
I took the libertry of cloning this because it was open source and no license was required to use and it was also a nice app that runs a small game instead of just printing "Hello World" on screen.

The ansible script can be run with:

```console
ansible-playbook deploy_snake.yaml --extra-vars "@deploy_snake_params.yaml"
```

Probably, better names can be given to the yaml files and the name of the image and the container but since I was in a hurry to finish these, I couldn't think for long

The IP Address of the container can be visible on the screen. Then you can type the IP Address:Port on your browser to be able to play the game by connecting to the docker container :)
