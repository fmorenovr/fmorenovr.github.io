---
layout: post
title:  "Create a REST service using Go Language and BeeGo Framework."
subtitle: Here you'll learn how to setup a REST API service with BeeGo Framework.
date:   2017-10-08 00:20:12 -0500
categories: frameworks
---
# Golang

Go is an Open Source programming language developed by Google Inc.  
You can see the installation [here](/programming-language/HelloWorld-Programming-Languages).

# Installing some libraries or dependencies for Golang

## Web Frameworks

### BeeGo

BeeGo is a Web Framework to develop using Golang Web Applications or RESTful services, you can find more information pressing [here](https://beego.me/).  
You can install on local writting this on terminal:

    go get github.com/astaxie/beego
    go get github.com/beego/bee

Then, move the `golangProjects/bin/bee` binary to `go/bin` directory.

### Gorilla

Gorilla is a Web Framework to develop using Golang RESTful services, you can find more information pressing [here](http://www.gorillatoolkit.org/).  
You can install on local writting this on terminal:

    go get github.com/gorilla/mux

## REST Service

REST(REpresentational State Transfer) is an architecture that use HTTP protocol which provide an API with methods like GET, POST, PUT, DELETE, etc.  
We use BeeGo framework and mgo driver to create a REST service on Golang using MongoDB:

* First, once installed go and beego framework binaries, creates a directory and write in shell:

      bee api myapi

  ![beego-api][newapi]

  The tree directory is like:
  
  ![beego-tree][treeapi]

* Second, you should download the database drivers, in my case is MongoDB.

## DataBases Drivers

### mgo

Is the MongoDB Driver for Golang. For more information or Doc press [here](https://labix.org/mgo).  
To install, write on terminal:

    go get gopkg.in/mgo.v2
    go get gopkg.in/check.v1

* Third, install mongoDB, you can see my example pressing [here][mongodbtuto] or see official doc [here](https://docs.mongodb.com/manual/).

  I use a Singleton Pattern to connect to database, like this:
  
  ```go
      type singletonMongoDBSession struct {
        session *mgo.Session
        errDial error
      }

      var instance *singletonMongoDBSession
      var once sync.Once

      func GetSessErrMongoDBSession(dialInfo string) (*mgo.Session, error){
        var instance *singletonMongoDBSession
        if dialInfo == "Dial"{
          instance = NewMongoDBSession()
        } else if dialInfo == "DialWithInfo"{
          instance = NewMongoDBSessionInfo()
        }
        return instance.session, instance.errDial
      }
      
      func NewMongoDBSession() (*singletonMongoDBSession) {
        once.Do(func() {
          sess, err := mgo.Dial(urldb)
          instance = &singletonMongoDBSession{session: sess, errDial: err}
        })
        return instance
      }
  ```
  Then, my model is like:
  
  ```go
      type Login struct{
        Username           string       `json:"username"`
        Password           string       `json:"password"`
      }

      var login Login

      func init(){}

      func VerifyLogin(object Login) (ObjectId bool, err error) {
        objlogin := loginRequest(object)
	      if objlogin == (Login{}) {
          fmt.Printf("\nNo se encontro Usuario !\n\n")
          return false, nil
        } else {
          return true, nil
        }
      }
  ```
  
  I modify some files and add directories to make more understandable how you can separates service or information.

  You can see my [restapi-BeeGo example][restapi-url], just pressing there :D .

# Another Packages for develop in Golang

## Communitacion Protocols

### MQTT Paho Golang

Is the MQTT library for Golang. For more information press [here](https://eclipse.org/paho/clients/golang/).  
To install, write on terminal:

    go get github.com/eclipse/paho.mqtt.golang

  To configure Mosquitto service, you can check my tuto pressing [here][mqtt-tuto].

## Mail Service

### GoMail

Is the SMTP library for Golang. For more information press [here](https://godoc.org/gopkg.in/gomail.v2).  
To install, write on terminal:

    go get gopkg.in/gomail.v2


[newapi]:          /assets/webApp/beego/beego-myapi.png
[treeapi]:         /assets/webApp/beego/beego-tree.png
[mongodbtuto]:     /database/Installing-MongoDB
[mqtt-tuto]:       /protocols/Setting-Up-a-MQTT-Service
[restapi-url]:     https://github.com/Jenazads/restfulapi-BeeGo
