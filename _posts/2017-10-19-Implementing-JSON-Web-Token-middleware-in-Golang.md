---
layout: post
title:  "Implementing a JSON Web Token middleware in Golang."
date:   2017-10-19 00:20:12 -0500
categories: libraries
---
# Golang

Go is an Open Source programming language developed by Google Inc.  
You can see how install pressing [here](/frameworks/Create-a-REST-service-using-Go-Language-and-BeeGo-Framework).

Visit my github repository [goJweto](https://github.com/jenazads/gojweto).

# Installing some libraries or dependencies for Golang

* First, You should create your RSA key pairs.  
  Create `/tls-ssl/jwtkeys/` directory in your root path of your project:

      cd jwt/keys
      openssl genrsa -out rsakey.pem 2048
      openssl rsa -in rsakey.pem -pubout > rsakey.pem.pub

## How does it works?

A JSON Web Token is a compact URL-safe means of representing claims to be transferred between two parties.  
The claim in a JWT are encoded as a JSON object.

**How we login to server?**  
When you log to your server, server validate your info and response success or fail. If you success, return data.

![login-normal][normal-login]

**How cookies help us?**  
Other technique is using cookies, when you log to the server a cookie is created and stores in server, then when you request some data, the server search for cookies and response.

![login-cookie][cookie-login]

**Why use JWT ?**  
But this method is insecure and is not scalable.  
For example, when you work with a lot of servers, when you create a cookie it could happen that cookie was stores in other server that you request and return error.

For this reason, JWT is more useful.  
Because it implements a secure method to response with a secure way.  
How it works ?

![login-jwt][jwt-login]

You can find more info pressing [here- Official Doc](https://jwt.io/) or [here - sample](http://robmclarty.com/blog/what-is-a-json-web-token).
## Web Libraries

### JWT-GO

JWT (JSON Web Token) is a Golang implementation.  
Install it:

      go get github.com/dgrijalva/jwt-go/

* Once installed, You should download my library:

      go get github.com/jenazads/gojweto/

* Then, you should use for differents Web Frameworks in Go.
        
    * First, generate the token string:
      
            tokenString, _ := gojweto.CreateHS256Token(Username)
            tokenString, _ := gojweto.CreateRS256Token(Username)

    * Using in Go net/http package:
      
      * Add `examples/goJwetoHandler.go` in your controllers directory.
      
      * Then, in your muxServe add:
      
        ```go
          muxHttp.HandleFunc("/setToken", setTokenHandler)
          muxHttp.HandleFunc("/login", LoginHandler)
          muxHttp.HandleFunc("/profile", gojweto.MiddlewareGoJwetoHeaders(WithAuthHandler, NoAuthHandler))
        ```

    * Using in BeeGo:
    
      * Add `examples/goJwetoBeeGoController.go` in your controllers directory.
        
      * And, in other controllers, add your new controller instead beegoController.
      
        ```go
            import (
              "encoding/json";
              "restfulapi-beego/models";
              //"github.com/astaxie/beego";
            )

            type AlertController struct {
	            //beego.Controller
	            GoJwetoController
            }
        ```

[normal-login]:   /assets/internet_services/JWT/rest-work.jpg
[cookie-login]:   /assets/internet_services/JWT/cookie-work.jpg
[jwt-login]:      /assets/internet_services/JWT/jwt-work.jpg
