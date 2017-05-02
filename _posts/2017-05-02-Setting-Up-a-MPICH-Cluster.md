---
layout: post
title:  "Setting Up a MPICH Cluster."
date:   2017-05-02 00:15:12 -0500
categories: Cluster-Computing
---
# Cluster

Using our cluster created [Jcluster][Jcluster_link].  
We need to install MPI (Message Pasing Interface).

# MPI

MPI is a standardized and portable message-passing system.

    sudo apt-get install mpich

MPI is useful in Distributed Computing Systems to do parallel programs.

## Example

On `/home/juser/forShare`, we must shared mpi files.

* Creating a `nodesfile` file with content:

      Jnode01:2  # this node use 2 processors
      Jnode02:3  # this node use 3 processors
      Jnode03:4  # this node use 4 processors
      Jnode04    # this node use 1 processors
      Jnode05

* Then, we write the `helloworldMPI.c` program (we use C language):

  {% highlight c %}
      #include <stdio.h>
      #include <mpi.h>

      int main(int argc, char** argv) {
        int myrank, nprocs;

        MPI_Init(&argc, &argv);
        MPI_Comm_size(MPI_COMM_WORLD, &nprocs);
        MPI_Comm_rank(MPI_COMM_WORLD, &myrank);

        printf("Hello from processor %d of %d\n", myrank, nprocs);

        MPI_Finalize();
        return 0;
      }
  {% endhighlight %}

* Then, compile it:

      mpicc helloworldMPI.c -o mpihello

* And run on `Jmaster`:

      mpirun -n 3 -f /path/to/nodesfile ./mpihello

![excution][mpi_exe]

[Jcluster_link]:   /blog/cluster-computing/2017/05/01/Setting-up-a-Beowulf-type-Cluster-in-linux-machines
[mpi_exe]:         /assets/clusterComputing/MPI/mpi_exe.png
