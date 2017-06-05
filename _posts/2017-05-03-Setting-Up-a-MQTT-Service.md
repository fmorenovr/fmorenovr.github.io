---
layout: post
title:  "Setting Up a MQTT client using Mosquitto service."
date:   2017-05-03 00:15:12 -0500
categories: Protocols
---
# MQTT

MQTT is a machine-to-machine (M2M) "Internet of Things" connectivity protocol.

# Mosquitto

Mosquitto is an open source message broker that implements the MQTT (Message Queue Telemetry Transport) protocol.

## Mosquitto Install and Setup

To install, write this (on Ubuntu):

    sudo apt-add-repository ppa:mosquitto-dev/mosquitto-ppa
    sudo apt-get update
    sudo apt-get install mosquitto mosquitto-clients

To install in Raspbian Jessie:

    sudo wget http://repo.mosquitto.org/debian/mosquitto-wheezy.list
    sudo apt-get update
    sudo apt-get install mosquitto mosquitto-clients 

Initializing the service:

    sudo mosquitto -c /etc/mosquitto/mosquitto.conf

Once installed, you can subscribe and publish on a specific topic:

    mosquitto_sub -t '#' -d -v
    mosquitto_pub -t 'testtopic/' -m '{"valor" : 15.3}'

## MQTT Web Socket service

To configure a web socket listener on port 1884, in the `/etc/mosquitto/mosquitto.conf` file add:

    listener port 1884
    protocol websockets

## MQTT Managing connections number

he maximum number of client connections to allow. This is a per listener setting.  
Just add the line to allows 10 users:

    max_connections 10

## MQTT Managing User

`PASSWD` hasthe job of registering users and passwords.

* Create `/etc/mosquitto/passwd` file:

      sudo touch /etc/mosquitto/passwd

* Then Create the first user. Writing this you'll create an user and that ask to your for a password:

      sudo mosquitto_passwd -c /etc/mosquitto/passwd Master

* Once the passwd file is created, to add other users it is used -b (if we use -c it is overwritten):

      sudo mosquitto_passwd -b /etc/mosquitto/passwd idUser 123456

* Once created users, you can subscribe and publish on a specific topic:

      mosquitto_sub -t '#' -d -v -u idUser -P 123456
      mosquitto_pub -t 'testtopic/' -m '{"valor" : 15.3}' -u idUser -P 123456

* If you want to allow only users with password, you should modify `/etc/mosquitto/mosquitto.conf` file just adding this lines:

      password_file /etc/mosquitto/passwd
      allow_anonymous false

## MQTT Access Control List

`ACLFILE` has the job of filtering which users can subscribe to certain specific topics or to a general.

* Create `/etc/mosquitto/aclfile` file:

      sudo touch /etc/mosquitto/aclfile

* Anonymous clients, they only can read message published on topic with structure `free/+/+`:

      topic read free/+/+

* Simple user, it can read/write messages on topic with structure `free/+/+`:

      user freeuser
      topic free/+/+

* Master user, it can see all messages in all topics:

      user Master
      topic #

* An user whose only can read messages published on a topic like `userId/+`, where `userId` is his id on `aclfile`:

      pattern read %u/+

* An user whose only can write messages on a topic like `clientId/+`, where `clientId` is his id when the client make a connection:

      pattern write %c/+

* To add `aclfile` and anonymous connections, modify `/etc/mosquitto/mosquitto.conf` file just adding this lines: 

      allow_anonymous true
      acl_file /etc/mosquitto/aclfile

## TLS/SSL Security Connections

To add security connections, apart of identification on `aclfile`.  
* First, we generate certificates files:

      wget https://github.com/owntracks/tools/blob/master/TLS/generate-CA.sh
      bash generate-CA.sh

  or yo can get pressing [here][CA-url].

* Uncompress/download and run it, this will generate 6 files of which 3 are important to us: `ca.crt`, `myhostname.crt` and `myhostname.key`, where:

    * ca.crt       – The Certificate Authority public certificate.
    * myhostname.crt – Is the public certificate.
    * myhostname.key – Is the private key.


* Then, copy the `ca.crt`, `myhostname.crt` and `myhostname.key` to `/etc/mosquitto/certs` directory:

      sudo cp ca.crt /etc/mosquitto/ca_certificates
      sudo cp myhostname.crt /etc/mosquitto/certs
      sudo cp myhostname.key /etc/mosquitto/certs

* Then, modify `/etc/mosquitto/mosquitto.conf`:

      # MQTT simple
      listener 1883
      protocol mqtt

      # MQTT with TLS/SSL
      listener 2883
      protocol mqtt
      cafile   /etc/mosquitto/ca_certificates/ca.crt
      certfile /etc/mosquitto/certs/myhostname.crt
      keyfile  /etc/mosquitto/certs/myhostname.key
      tls_version tlsv1.2

      # Websockets simple
      listener 1884
      protocol websockets

      # WebSockets with TLS/SSL
      listener 2884
      protocol websockets
      cafile   /etc/mosquitto/ca_certificates/ca.crt
      certfile /etc/mosquitto/certs/myhostname.crt
      keyfile  /etc/mosquitto/certs/myhostname.key
      tls_version tlsv1.2

* Now, making connections tests:

  1. On port 1883 without TLS/SSL security:

      * Anonymous client (remember that we have `allow_anonymous true`) and without TLS/SSL:

             mosquitto_sub -t '#' -d -v -p 1883
             mosquitto_pub -t 'testtopic/' -m '{"valor" : 15.3}' -p 1883

      * User with password client:

             mosquitto_sub -t '#' -d -v -u idUser -P 123456 -p 1883
             mosquitto_pub -t 'testtopic/' -m '{"valor" : 15.3}' -u idUser -P 123456 -p 1883

  2. On port 2883 with TLS/SSL security:

      * Anonymous client (remember that we have `allow_anonymous true`):

            mosquitto_sub -t '#' -d -v -p 2883 --cafile /etc/mosquitto/ca_certificates/ca.crt
            mosquitto_pub -t 'testtopic/' -m '{"valor" : 15.3}' -p 2883 --cafile /etc/mosquitto/ca_certificates/ca.crt

      * User with password client:
            
            mosquitto_sub -t '#' -d -v -u idUser -P 123456 -p 2883 --cafile /etc/mosquitto/ca_certificates/ca.crt
            mosquitto_pub -t 'testtopic/' -m '{"valor" : 15.3}' -u idUser -P 123456 -p 2883 --cafile /etc/mosquitto/ca_certificates/ca.crt

* Now, for only admit connections with certification we need to add to `/etc/mosquitto/mosquitto.conf` file, below of all port with TLS/SSL:

      require_certificate true
      use_identity_as_username true

* So, using `ca.crt` file we generate certs for a registered client, for example `Master` client:

      bash generate-CA.sh client Master
      sudo cp Master.key /etc/mosquitto/certs/
      sudo cp Master.crt /etc/mosquitto/certs/

* Now we can connect using our client certs:

    * Anonymous client (remember that we have `allow_anonymous true`):

          mosquitto_sub -t '#' -d -v -p 2883 --cafile /etc/mosquitto/ca_certificates/ca.crt --cert /etc/mosquitto/certs/Master.crt --key /etc/mosquitto/certs/Master.key
          mosquitto_pub -t 'testtopic/' -m '{"valor" : 15.3}' -p 2883 --cafile /etc/mosquitto/ca_certificates/ca.crt

    * User with password client:
          
          mosquitto_sub -t '#' -d -v -u idUser -P 123456 -p 2883 --cafile /etc/mosquitto/ca_certificates/ca.crt --cert /etc/mosquitto/certs/Master.crt --key /etc/mosquitto/certs/Master.key
          mosquitto_pub -t 'testtopic/' -m '{"valor" : 15.3}' -u idUser -P 123456 -p 2883 --cafile /etc/mosquitto/ca_certificates/ca.crt --cert /etc/mosquitto/certs/Master.crt --key /etc/mosquitto/certs/Master.key

## Files

Get a configuration pack example [here][example-url].


[CA-url]:       /files/generate-CA.zip
[example-url]:  /files/mosquitto-example.zip
