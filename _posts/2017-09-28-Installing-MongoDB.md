---
layout: post
title:  "Installing MongoDB and starts with NoSQL databases."
date:   2017-09-28 12:15:12 -0500
categories: database
---
# MongoDB

No relational database with data storage in JSON format.

* Install MongoDB, first download keys:

      sudo -i
      sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 2930ADAE8CAF5059EE73BB4B58712A2291FA4AD5
      echo "deb http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.6 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.6.list
      sudo apt-get update

* Then, install mongo

      sudo apt-get install -y mongodb-org

* Create the mongo service file:

      sudo nano /etc/systemd/system/mongodb.service

  Add these lines:

      [Unit]
        Description=High-performance, schema-free document-oriented database
        After=network.target

      [Service]
        User=mongodb
        ExecStart=/usr/bin/mongod --quiet --config /etc/mongod.conf

      [Install]
        WantedBy=multi-user.target

* Next, start the service:

      sudo systemctl start mongodb
      sudo systemctl status mongodb
      sudo systemctl enable mongodb

* Finally, start the client:

      sudo mongod -f /etc/mongod.conf

## Starts client

* When you have an error in language, in the file `.bashrc` add:

      export LC_ALL=C

## Manage the database

* Create index:

      db.dbname.createIndex( { razon_social: "text", ruc: "text" } )

* Get Indexes:

      db.dbname.getIndexes()

* Delete index:

      db.dbname.dropIndex(indexName)

## Backup

* Import:

      mongoimport --db dbname --collection colname --file outputfile

* Export:

      mongoexport --db dbname --collection colname --out  outputfile

* Export to CSV format:

      mongoexport --db dbname --collection colname --query '{"id_moduleiot":"C001","date": {$gte:"2017-11-01"}}' --type csv --fields "field1,field2,field3" --out data.csv

## Users

* Init the service on 27018:

      sudo mongod --auth --port 27018 --dbpath /var/lib/mongodb/

* Create a master-daster user:

      use admin
      db.createUser({
        user: "hyper-admin",
        pwd: "hyper",
        roles: [ "root"]
      })

* Create a new user with admin privileges:

      db.createUser({
        user: "super-admin",
        pwd: "super",
        roles: [
          {role: "clusterAdmin", db: "admin" },
          {role: "dbAdminAnyDatabase", db: "admin" },
          {role: "userAdminAnyDatabase", db: "admin" },
          {role: "readWriteAnyDatabase", db: "admin" }
        ]}
      )

* Create a new user with privileges only in mydb:

      use mydb
      db.createUser({
        user: "mydb-admin",
        pwd: "admin",
        roles: [
          {role: "userAdmin", db: "mydb" },
          {role: "readWrite", db: "mydb" }
        ]}
      )

* Create a new user with onlye-read privileges on mydb:

      db.createUser({
        user: "mydb-user",
        pwd: "user",
        roles: [
          {role: "read", db: "mydb" }
        ]}
      )

* Once created the service in `--auth` mode, we can connect to db using:

      mongo admin --port 27018 --username hyper-admin --password hyper --authenticationDatabase admin
      mongo admin --port 27018 --username super-admin --password super --authenticationDatabase admin
      mongo mydb --port 27018 --username mydb-admin --password admin --authenticationDatabase mydb
      mongo mydb --port 27018 --username mydb-user --password user --authenticationDatabase mydb

