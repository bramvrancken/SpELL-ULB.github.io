# Beagle install 

Installing beagle from source can be a bit of a pain. Installing & compiling from source is difficult and always causes problems. 

> TODO: Explain how to install from source on HPC  

## Cheat with Singularity
!!! info "what is Singularity?"
    Ooh you don't know what singularity is? Have a read [here](./singularity.md)

The easiest way to install beagle is to use a container. The container is a self-contained environment that has all the dependencies installed. 

A central container repository has multiple versions of the BEAST-BEAGLE software that is compatible with CUDA (GPU). 

**[https://quay.io/repository/broadinstitute/beast-beagle-cuda](https://quay.io/repository/broadinstitute/beast-beagle-cuda)**

To use one of these containers, simply run: 
    
```bash
module load CUDA

singularity exec --nv \
-B $VSC_DATA:$VSC_DATA -B $VSC_STAGING:$VSC_STAGING -B $VSC_SCRATCH:$VSC_SCRATCH -B $VSC_HOME:$VSC_HOME -B $PWD \ 
docker://quay.io/broadinstitute/beast-beagle-cuda:v10.5.0_beta3 \
beast -beagle_info
```
    
!!! tip 
    All these `-B` statements are to bind the directories to the container. Meaning, the container can access the directories on the host machine.

!!! tip
    The `--nv` flag is to enable GPU support.

!!! tip 
    we specified `docker://` because the container is stored in a docker repository.

!!! warning
    The container is large, don't run this in your home directory.
    Better yet, set up a singularity cache directory.
    ```bash
    export APPTAINER_CACHEDIR=$VSC_SCRATCH/.apptainer >> ~/.bashrc
    ```
