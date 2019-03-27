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
      sudo apt-get install nodejs npm
      npm install [package]

* The Hello World program:

  ```javascript
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

## Perl (PL)

Important language to develop http servers, created by Larry Wall.

* To install:

      sudo apt-get install perl

* The Hello World program:

  ```perl
  #!/usr/bin/env perl

  use strict;
  use warnings;

  sub main{
    my @argv = @_;
    my $argc = (@argv);
    print("\n\tHola Mundo Perl !!\n\n");
    print("Numero de argumentos: ".($argc+1)."\n");
    print("Argumento[0] = $0\n");
    foreach my $i(0..($argc-1)){
      print("Argumento[".($i+1)."] = $argv[$i]\n");
    }
    return;
  }

  main(@ARGV);
  ```

* To run the file:

      perl helloWorld.pl

## PHP

Important language to develop web servers, created by Rasmus Lerdorf.

* To install:

      sudo apt-get install php7.0 composer
      composer install [package]

* The Hello World program:

  ```php
  #!/usr/bin/env php

  <?php
  class HelloWorld{
    public static function main($arguments, $count){
      print("\tHola Mundo PHP !!\n\n");
      print("Numero de argumentos: $count\n");
      foreach($arguments as $key => $value){
        print("Argumento[$key] = $value\n");
      }
      return;
    }
  }
  HelloWorld::main($argv, $argc);
  ?>
  ```

* To run the file:

      php helloWorld.php

## Python

A very important programming language, created by Guido van Rossum.

* To install:

      sudo apt-get install python python-pip
      pip install [package]

* The Hello World program:

  ```python
  #!/usr/bin/env python

  # -*- coding: utf-8 -*-
  import sys

  def main(argv):
    print("\n\tHola Mundo Python !!\n");
    argc = len(sys.argv);
    print("Numero de argumentos: %i" %(argc));
    for i in range(argc):
      print("Argumento[%i] = %s" %(i,sys.argv[i]));
    return;

  if __name__ == "__main__":
    main(sys.argv[1:]);
  ```


* To run the file:

      python helloWorld.py

## R

An important statistic language, created by Robert C. Gentleman.

* To install:

      sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E298A3A825C0D65DFD57CBB651716619E084DAB9
      sudo add-apt-repository 'deb https://cloud.r-project.org/bin/linux/ubuntu bionic-cran35/'
      sudo apt-get update
      sudo apt-get install r-base r-base-dev

* The Hello World program:

  ```r
  #!/usr/bin/env Rscript

  #library(stats);

  printf <- function(...){ invisible(cat(sprintf(...)))}

  main<-function(argsv){
    printf("\n\tHola Mundo R !!\n\n");
    argc<-length(argsv);
    argsv[4] = strsplit(argsv[4],"--file=")[[1]][2]
    if(argc>5){ printf("Numero de argumentos: %d\n",argc-4);}
    else{ printf("Numero de argumentos:",argc-3,"\n");}
    printf("Argumento[0] = %s\n",argsv[4]);
    if(argc>5){
      for(i in 6:argc){
        printf("Argumento[%d] = %s \n",i-5, argsv[i])
      }
    }
    return ();
  }

  mainf<-main(commandArgs(trailingOnly = FALSE));
  ```

* To run the file:

      Rscript helloWorld.R

## Ruby

Important to develop services, created by Yukihiro "Matz" Matsumoto.

* To install:

      sudo apt-get install ruby-full ruby-dev ruby gem
      gem install [package]

* The Hello World program:

```ruby
#!/usr/bin/env ruby

#require 'io/console';

def main(argv)
  argc = argv.length;
  print("\n\tHola Mundo Ruby !!\n\n");
  print("Numero de argumentos: #{argc+1}\n");
  print("Argumento[0] = #{File.basename(__FILE__)}\n");
  for i in 0...argc
    print("Argumento[#{i+1}] = #{argv[i]}\n");
  end
  return;
end

main ARGV;
```

* To run the file:

      ruby helloWorld.rb


