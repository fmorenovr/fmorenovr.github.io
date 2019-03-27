---
layout: post
title:  "Hello world from different Programing languages"
subtitle: Here you'll see different helloworld programs.
date:   2016-04-22 15:15:12 -0500
categories: Programming-Language
---

## Programming Languages Table

Here is a little information about programming languages.

|*Año* | *Lenguaje*     |       *Creador*        |  *Aplicacion*                                                         |
|----|--------------|----------------------|---------------------------------------------------------------------:|
|    | Machine Code |                      |                                                                     |
|1679| Binary Code  | Gottfried Leibniz    | Procesar Instrucciones y Codigos de texto (ASCII)                   |
|1950| Assembler    |                      | Hardware Manipulation                                               |
|1957| FORTRAN      | John W. Backus       | Scientific Computing                                                |
|1958| Lisp         | John P. McCarthy     |                                                                     |
|1972| ProLog       | Alain A. Colmerauer  |                                                                     |
|1972| C            | Dennis M. Ritchie    | All is possible                                                     |
|1978| SQL          | Donald D. Chamberlin | Database Management System                                          |
|1980| C++          | Bjarne Stroustrup    | Linux Applications                                                  |
|1982| Common Lisp  | Guy L. Steele        |                                                                     |
|1984| M            | Jhon W. Eaton        | Simulation and Numerical Analysis                                   |
|1984| Verilog      | Phil Moorby          | Hardware Design, Structure and Description                          |
|1987| Perl         | Larry Wall           | Integrate services as unique admin system, processing text          |
|1989| Bash         | Brian Fox            | Command Line Interface language                                     |
|1991| Python       | Guido van Rossum     | Artificial Intelligence, Image Processing, Computer Vision          |
|1993| Ruby         | 松本行弘             |                                                                     |
|1993| R            | Robert C. Gentleman  | Statistical Analysis, Data analysis and Data Mining                 |
|1993| JavaScript   | Brendan Eich         | Client Side Languag in Web Services                                 |
|1995| PhP          | Rasmus Lerdorf       | Server Side Language in Web Services                                |
|1995| Java         | James A. Gosling     | Aplicaciones Android OS                                             |
|2001| C#           | Anders Hejlsberg     | Windows Applications                                                |
|2009| Go           | Robert Pike          | All is possible                                                     |

## Bash

The name is Bourne-again shell, created by Brian Fox.

* The Hello World program:

  ```bash
  #!/usr/bin/env bash

  #source "";

  main() {
    printf "\n\tHola Mundo Bash !!\n\n";
    printf "Numero de argumentos: %i\n" "$(($#+1))";
    for((c=0; c<=("$#"); c++)); do  
      printf "Argumento[$c] = ${!c} \n";
    done
    return ;
  }

  main $@;
  ```

* To run the file:

      bash helloWorld.sh

## C

This is the core of all applications, created by Dennis M. Ritchie.

* To install:

      sudo apt-get install build-essentials

* The Hello World program:

  ```C
  #include <stdio.h>

  int main(int argc,char* argv[]){
    int i;
    printf("\n\tHola Mundo C !!\n\n");
    printf("Numero de argumentos: %i\n",argc);
    for(i=0;i<argc;i++){
      printf("Argumento[%i] = %s\n",i,argv[i]);
    }
    return 0;
  }
  ```

* To run the file:

      gcc helloWorld.c -o helloWorld  && ./helloWorld

### Converting to assembly

* Preprocessing (EXPAND MACROS):

      cpp archivo.c > archivo.i

* Compilation (FROM SOURCE CODE TO ASSEMBLY):

      gcc -Wall -S hello.i

* Assembly (FROM ASEEMBLY LANGUAGE TO MACHINE CODE):

      as hello.s -o hello.o

* Linking (CREATE THE FINAL EXECUTABLE):

      gcc hello.o

## CPP (C++)

This is the core of all applications, created by Bjarne Stroustrup.

* To install:

      sudo apt-get install build-essentials

* The Hello World program:

  ```CPP
  #include <iostream>

  using namespace std;

  int main(int argc,char* argv[]){
    int i;
    cout<<endl<<"\tHola Mundo C++ !!"<<endl<<endl;
    cout<<"Numero de argumentos: "<<argc<<endl;
    for(i=0;i<argc;i++){
      cout<<"Argumento["<<i<<"] = "<<argv[i]<<endl;
    }
    return 0;
  }
  ```

* To run the file:

      g++ helloWorld.c++ -o helloWorld && ./helloWorld

## CS (C#)

Created by Anders Hejlsberg.

* To install:

      sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF
      echo "deb https://download.mono-project.com/repo/ubuntu stable-bionic main" | sudo tee /etc/apt/sources.list.d/mono-official-stable.list
      sudo apt install mono-devel

* The Hello World program:

  ```CPP
  using System;

  namespace HelloWorld{
    public class mainClass{
      public static void Main(string[] args){
        int argc = args.Length;
        string currentFile = new System.Diagnostics.StackTrace(true).GetFrame(0).GetFileName();
        System.Console.WriteLine("\n\tHola Mundo C# !!\n");
        System.Console.WriteLine("Numero de argumentos: {0}", argc+1);
        System.Console.WriteLine("Argumento[0] = {0}", currentFile);
        for (int i = 0; i < argc; i++){
          System.Console.WriteLine("Argumento[{0}] = {1}", i+1, args[i]);
        }
      }
    }
  }
  ```

* To run the file:

      mcs helloWorld.cs -out:helloWorld && ./helloWorld

## Golang (Go)

This is the new core for a lot of applications, created by Robert Pike.

* To install:

  * To install go latest:

        wget https://storage.googleapis.com/golang/go1.9.1.linux-amd64.tar.gz

  * Unzip in `/usr/local` directory:

        sudo tar -C /usr/local -xzf go1.9.1.linux-amd64.tar.gz
        tar -C ./ -xzf go1.9.1.linux-amd64.tar.gz

  * Then, modify `/etc/profile` file, add this line:

        export PATH=$PATH:/usr/local/go/bin

  * Also, add these lines in `/home/$USER/.profile` file:

        export GOPATH=$HOME/golangProjects
        export GOROOT=$HOME/go
        export PATH=$PATH:$GOROOT/bin

  * Finally, reboot or execute this:

        source .profile
        sudo source /etc/profile

* The Hello World program:

  ```go
  package main

  import (
    "os";
    "fmt";
  )

  func main() {
    fmt.Printf("\n\tHola Mundo Go !!\n\n");
    fmt.Printf("Numero de argumentos: %d\n", len(os.Args));
    for i,e := range os.Args {
      fmt.Printf("Argumento[%d] = %s\n", i, e);
    }
    return ;
  }
  ```

* To run the file:

      go build -o helloWorld helloWorld.go && ./helloWorld

## Java

Its a one important programming language in software development, created by James A. Gosling.

* To install:

      sudo add-apt-repository ppa:webupd8team/java
      sudo apt-get update
      sudo apt-get install oracle-java8-installer
      sudo apt-get install oracle-java8-set-default

* The Hello World program:

  ```java
  class HelloWorld {
    public static void main(String[] args) {
      int argc = args.length;
      System.out.println("\n\tHola Mundo Java !!\n");
      System.out.printf("Numero de argumentos: %d\n", argc+1);
      System.out.printf("Argumento[0] = %s\n", "nombre del archivo");
      for(int i =0; i<argc; i++) {
        System.out.printf("Argumento[%d] = %s\n", i+1, args[i]);
      }
    }
  }
  ```

* To run the file:

      javac helloWorld.java
      java HelloWorld

## JavaScript (JS)

Another important programming language, created by Brendan Eich.

* To install (also, you can run in web browser):

      curl -sL https://deb.nodesource.com/setup_6.x -o nodesource_setup.sh
      nano nodesource_setup.sh
      sudo bash nodesource_setup.sh
      sudo apt-get install nodejs

* The Hello World program:

  ```js
  #!/usr/bin/env nodejs

  var path = require('path');

  function main(argv){
    var argc = argv.length;
    console.log('\n\tHola Mundo Javascript !!\n');
    console.log(`Numero de argumentos: ${(argv.length-1)}`);
    console.log('Argumento[0] = ' + path.basename(argv[1]))
    for (i=2; i< argc; i++){
      console.log(`Argumento[${i-1}] = ${argv[i]}`);
    }
    return;
  }

  main(process.argv)
  ```

* To run the file:

      nodejs helloWorld.js

## M (Octave/MATLAB)

An important programming languages to many applications in numeric fields, created by Jhon W. Eaton.

* To install:

      sudo apt-get install octave liboctave-dev

* The Hello World program:

  ```octave
  #!/usr/bin/env octave

  #pkg install control-1.0.0.tar.gz
  #pkg install control

  a=3;

  function []=main(argcs,argvs)
    printf("\n\tHola Mundo M !!\n\n");
    printf("Numero de argumentos: %i\n",argcs+1);
    printf("Argumento[0] = %s\n",program_name());
    for i = 1:argcs
      printf("Argumento[%i] = %s\n",i,argvs{i});
    end
    return;
  end

  main(nargin(),argv())
  ```

* To run the file:

      octave helloWorld.m


