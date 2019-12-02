---
layout: post
title:  "Useful Libraries in C."
date:   2016-04-20 12:15:12 -0500

tags:
  - Ubuntu
  - Hello world
  - C++
  - C
  - MPI
  - POSIX
  - Threads
  - OpenCV
  - OpenMPI
  - CV
  - OpenMP
  - Multi-processing

categories:
  - Programming-Language
---

Here you'll learn how to install and use some useful libraries in C language.

C is a programming language that is considered one of the best languages. It was created by Dennis Ritchie at 1972 in Bell Labs.

## Programming Language

Setup dependencies to install C, C++:

    sudo apt-get install build-essential

## Concurrent Computing:

POSIX Thread: Use threads

    sudo apt-get install libevent-pthreads-2.0-5

An example of hello world program:

```c
  #include <pthread.h>
  #include <stdio.h>
  #include <stdlib.h>
  #define NUM_THREADS	5

  void *PrintHello(void *threadid) {
    long tid;
    tid = (long)threadid;
    printf("Hello World! It's me, thread #%ld!\n", tid);
    pthread_exit(NULL);
  }

  int main(int argc, char *argv[]) {
    pthread_t threads[NUM_THREADS];
    int rc;
    long t;
    for(t=0;t<NUM_THREADS;t++){
      printf("In main: creating thread %ld\n", t);
      rc = pthread_create(&threads[t], NULL, PrintHello, (void *)t);
      if (rc){
        printf("ERROR; return code from pthread_create() is %d\n", rc);
        exit(-1);
      }
    }
    /* Last thing that main() should do */
    pthread_exit(NULL);
  }

  // gcc helloworld_threads.c -lpthread -o pthread
  // ./pthread
```

How to run:

    gcc mycode.c -lpthread

## Distributed Computing:

Message Passing Interface: Use Procesor

    sudo apt-get install mpich

An example of hello world program:

```c
  #include <mpi.h>
  #include <stdio.h>

  int main(int argc, char** argv) {
    // Initialize the MPI environment
    MPI_Init(NULL, NULL);

    // Get the number of processes
    int world_size;
    MPI_Comm_size(MPI_COMM_WORLD, &world_size);

    // Get the rank of the process
    int world_rank;
    MPI_Comm_rank(MPI_COMM_WORLD, &world_rank);

    // Get the name of the processor
    char processor_name[MPI_MAX_PROCESSOR_NAME];
    int name_len;
    MPI_Get_processor_name(processor_name, &name_len);

    // Print off a hello world message
    printf("Hello world from processor %s, rank %d"
           " out of %d processors\n",
           processor_name, world_rank, world_size);

    // Finalize the MPI environment.
    MPI_Finalize();
  }

  // mpicc helloworld_MPI.c -o mpi
  // mpiexec -n 4 ./mpi
```

How to run:

    mpicc -f archivo_ips.txt -np 4 mycode.c


## Parallel Computing:

Multi-Processing: 

    sudo apt-get install gcc-multilib

An example of hello world program:

```c
  #include <omp.h>
  #include <stdio.h>
  #include <stdlib.h>

  int main (int argc, char *argv[]) {
    int nthreads, tid;

    /* Fork a team of threads giving them their own copies of variables */
    #pragma omp parallel private(nthreads, tid) {

      /* Obtain thread number */
      tid = omp_get_thread_num();
      printf("Hello World from thread = %d\n", tid);

      /* Only master thread does this */
      if (tid == 0) {
        nthreads = omp_get_num_threads();
        printf("Number of threads = %d\n", nthreads);
      }
    }  /* All threads join master thread and disband */
  }

  // gcc helloworld_openMP.c -fopenmp -o openmp
  // ./openmp
```

How to run:

    gcc mycode.c -fopenmp 

## Graphic Computing:

Graphic Library: Produce Image

    sudo apt-get install freeglut3 freeglut3-dev libglew-dev libglfw3-dev libglm-dev 

An example of hello world program:

```c
  #include <GL/glut.h>
  //#include <GL/glu.h>
  //#include <GL/freeglut.h>

  //Drawing funciton
  void draw(void) {
    //Background color
    glClearColor(0,1,0,1);
    glClear(GL_COLOR_BUFFER_BIT );
    //Draw order
    glFlush();
  }

  //Main program
  int main(int argc, char **argv) {
    glutInit(&argc, argv);
    //Simple buffer
    glutInitDisplayMode(GLUT_SINGLE | GLUT_RGB );
    glutInitWindowPosition(50,25);
    glutInitWindowSize(500,250);
    glutCreateWindow("Green window");
    //Call to the drawing function
    glutDisplayFunc(draw);
    glutMainLoop();
    return 0;
  }

  // gcc helloworld_openGL.c -lGL -lglut -lGLU -o opengl
  // ./opengl
```

How to run:

    gcc mycode.c -lGL -lglut -lGLU -lGLEW -lfbxsdk -lglfw3 `pkg-config --libs glfw3`

## Vision Computing:

Computer Vision: Time Real Processing Image

## paquetes de instalacion y desintalacion

    sudo apt install libopencv-dev

An example of helloworld program:

```c
  #include "opencv2/opencv.hpp"

  using namespace cv;

  int main(int argc, char** argv) {
  
      //create a gui window:
      namedWindow("Output",1);

      //initialize a 120X350 matrix of black pixels:
      Mat output = Mat::zeros( 120, 350, CV_8UC3 );

      //write text on the matrix:
      putText(output,
              "Hello World :)",
              cvPoint(15,70),
              FONT_HERSHEY_PLAIN,
              3,
              cvScalar(0,255,0),
              4);

      //display the image:
      imshow("Output", output);

      //wait for the user to press any key:
      waitKey(0);

      return 0;
    }
    
    // g++ helloworld_openCV.cpp`pkg-config --cflags --libs opencv`-o opencv
    // ./a.out
```

How to run:

    gcc mycode.c `pkg-config --cflags --libs opencv` 

