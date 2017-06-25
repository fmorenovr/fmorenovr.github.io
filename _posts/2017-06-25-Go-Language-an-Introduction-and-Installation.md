---
layout: post
title:  "Go Language, an introduction and installation guide."
date:   2017-06-25 00:20:12 -0500
categories: programmingLanguages
---
## Golang

Go is an Open Source programming language developed by Google Inc.  
To install go version 1.7:

    wget https://storage.googleapis.com/golang/go1.7.linux-amd64.tar.gz

Unzip in `/usr/local` directory:

    sudo tar -C /usr/local -xzf go1.7.linux-amd64.tar.gz
    tar -C ./ -xzf go1.7.linux-amd64.tar.gz

Then, modify `/etc/profile` file, add this line:

    export PATH=$PATH:/usr/local/go/bin

also, add these lines in `/home/$USER/.profile` file:

    export GOPATH=$HOME/golangProjects
    export GOROOT=$HOME/go
    export PATH=$PATH:$GOROOT/bin

## Installing some libraries or dependencies for Golang

### Web Frameworks

#### BeeGo

BeeGo is a Web Framework to develop using Golang Web Applications or RESTful services, you can find more information pressing [here](https://beego.me/).  
You can install on local writting this on terminal:

    go get github.com/astaxie/beego
    go get github.com/beego/bee

Then, move the `bee` binary to `go/bin` directory.

#### Gorilla

Gorilla is a Web Framework to develop using Golang RESTful services, you can find more information pressing [here](http://www.gorillatoolkit.org/).  
You can install on local writting this on terminal:

    go get github.com/gorilla/mux

### DataBases Drivers

#### mgo

Is the MongoDB Driver for Golang. For more information or Doc press [here](https://labix.org/mgo).  
To install, write on terminal:

    go get gopkg.in/mgo.v2
    go get gopkg.in/check.v1

### Communitacion Protocols

#### MQTT Paho Golang

Is the MQTT library for Golang. For more information press [here](https://eclipse.org/paho/clients/golang/).  
To install, write on terminal:

    go get github.com/eclipse/paho.mqtt.golang

## GoMail

Is the SMTP library for Golang. For more information press [here](https://godoc.org/gopkg.in/gomail.v2).  
To install, write on terminal:

    go get gopkg.in/gomail.v2


