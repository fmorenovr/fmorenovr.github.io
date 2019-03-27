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
|1980| C++     	    | Bjarne Stroustrup    | Linux Applications                                                  |
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

```{r, engine='bash', count_lines}

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

Run the file:

    bash helloWorld.sh


