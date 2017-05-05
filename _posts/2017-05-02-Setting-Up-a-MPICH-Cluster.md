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
      #include <mpi.h>
      #include <stdio.h>

      int main(int argc, char** argv) {
          // Initialize the MPI environment
          MPI_Init(NULL, NULL);
          // Get the number of processes
          int world_size, world_rank, name_len;
          MPI_Comm_size(MPI_COMM_WORLD, &world_size);
          // Get the rank of the process
          MPI_Comm_rank(MPI_COMM_WORLD, &world_rank);
          // Get the name of the processor
          char processor_name[MPI_MAX_PROCESSOR_NAME];
          MPI_Get_processor_name(processor_name, &name_len);

          // Print off a hello world message
          printf("Hello world from processor %s, rank %d out of %d processors\n", processor_name, world_rank, world_size);

          // Finalize the MPI environment.
          MPI_Finalize();
      }
  {% endhighlight %}

* Then, compile it:

      mpicc helloworldMPI.c -o mpihello

* And run on `Jmaster`:

      mpiexec -np 3 -f /path/to/nodesfile ./mpihello

![excution][mpi_exe]

[Jcluster_link]:   /blog/cluster-computing/2017-05-01/Setting-up-a-Beowulf-type-Cluster-in-linux-machines
[mpi_exe]:         /assets/clusterComputing/MPI/mpi_exe.png
