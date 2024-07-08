### Page template

This page is a work in progress!

Come back later to check on it, or [contribute](https://github.com/ECV-Lab-KULeuven/ECV-Lab-KULeuven.github.io).



## HPC Resources

To create detailed tables for each cluster profile and the resources and time allowed for each partition, we can follow the logic in the configuration. Here are the tables:

!!! info overhead
    A HPC needs a little memory for the operating system and other services. This is called overhead. The overhead is the memory that is not available for the user.  This is why the maximum memory available to the user is less than the total memory of the node.

### Genius Profile

| Partition       |nCPUs| Max Memory | Max Time |
|-----------------|------------|----------|
| batch           | 36| 180 GB   | 72 h   |
| batch_long      | 36| 180 GB   | 168 h   |
| bigmem          | 36| 720 GB   | 72 h   |
| bigmem_long     | 36| 720 GB   | 168 h   |
| superdome       | 14| 5772 GB   | 72 h   |
| superdome_long  | 14| 5772 GB   | 168 h   |
> Numbers are for 1 node. 

### Wice Profile

| Partition                  | nCPUs | Max Memory | Max Time |
|----------------------------|----------|------------|----------|
| batch                      | 72       | 244 GB   | 72 h   |
| batch_long                 | 72       | 244 GB   | 168 h   |
| bigmem                     | 72       | 2016 GB   | 72 h   |
| dedicated_big_bigmem       | 72       | 2016 GB   | 168 h |
> Numbers are for 1 node. 

> TODO: GPUs