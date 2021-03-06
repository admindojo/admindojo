# admindojo
> hands-on sysadmin training right in your terminal

[![Build Status](https://travis-ci.org/admindojo/admindojo.svg?branch=master)](https://travis-ci.org/admindojo/admindojo)

admondojo is a game that helps you to become familiar with linux admin tasks like installing and configuring a database.

Your training will be as realistic as possible - you'll install and configure real applications right in the terminal. Once you're done your setup will get checked and rated. 
In tutor-mode a background tutor will check your work constantly and provides hints.


## Installation

### On your own VM/Server
Requirements:
- freshly installed Ubuntu VM/Container/Server
- sudo user

Note: Since you'll modify the system, please run admindojo on an unused system only. You should be able to reinstall/rebuild the system after each lesson.

To let you run the admindojo by just typing `admindojo` the setup adds an alias to your .bash_profile.
```sh
git clone https://github.com/admondojo/admindojo.git
cd admondojo
sudo ./setup.sh
admindojo
```

### Hassle free docker image

To use admindojo in a ready to use docker container, just `docker pull admindojo/admindojo`. The image contains the latest, ready to use, version of admindojo.
The container includes an SSH-Server. 

Just SSH to it:
- username: `sysadmin`
- password: `password`
- port: `22`

## Quick-Start
1. Type `admindojo start`
2. Choose a lesson
3. solve all listed tasks (type `admindojo tasks` to see them again)
4. type `admindojo end` to check if you solved all tasks properly

## Usage
type `admindojo`
```
 >admindojo

 Start the training
    admindojo start   (list, select and start lessons)

 In-game control
    admindojo tasks   (show tasks)
    admindojo end     (end game, show restult)

 Tutor mode:
 Guides you through your lesson. Checks every minute if you solved a task and shows hints.
    admindojo tutor   (start tutor)
```

Select your lesson:
`admindojo start`

![Select your lesson](https://github.com/admindojo/admindojo/raw/master/documentation/screenshot_input.png)

View your tasks:
`admindojo tasks`

![View your tasks](https://github.com/admindojo/admindojo/raw/master/documentation/screenshot_tasks.png)

## Interactive tutor mode
`admindojo tutor`

![Get your result](https://github.com/admindojo/admindojo/raw/master/documentation/screenshot_result.png)


## Contributing

Feedback and contribution is highly appreciated! 

The project is in a very early stage and so is the contribution setup. Please get in touch via github issue.

### function documentation
see `Functions.md` for full documentation of all functions.

### Development setup

To run a test for all lessons run `./admindojo.sh testing`. 
Run this on a fresh VM/CI only!

***Testing mode installs/executes all lesson tasks.***

### Testing admindojo in Docker
Run the Dockerfile `development\dockerfile` to setup admindojo in a docker container.
The container starts a SSH server, so it's possible to SSH into the container.
Modify cloned repository with your fork/branch:
````dockerfile
#Clone Repo
RUN git clone 'https://github.com/admindojo/admindojo.git'
````
Build image
````bash
 docker build -f "admindojo/development/dockerfile" -t admindojoimage .
````
Start container
````bash
docker run -d admindojotest --name admindojocontainer
````
Test inside container (or ssh into it)
````bash
docker exec -i --user sysadmin -t admindojocontainer /bin/bash
sysadmin@4460579660c7:~/admindojo$ source ~/.bash_profile
admindojo

````

#### generate documentation
Install [shdoc](https://github.com/reconquest/shdoc) first
```sh
make doku
```

## Meta

Initial work:
- Marvin Heimbrodt – [@6uhrmittag](https://twitter.com/6uhrmittag) – marvin@6uhrmittag.de

Distributed under the MIT license. See ``LICENSE`` for more information.

## Acknowledgments
Following texts, tools insipred or helped the development:

* [Lynis - Security auditing tool](https://github.com/CISOfy/lynis) - inspired the game mode
* [shdoc - Documentation generator for shell scripts](https://github.com/reconquest/shdoc) - used for documentation
* [Google Shell Style Guide](https://google.github.io/styleguide/shell.xml#Function_Names) - helped to improve code
* [ShellCheck - finds bugs in your shell scripts](https://google.github.io/styleguide/shell.xml#Function_Names) - awesome shell linter
