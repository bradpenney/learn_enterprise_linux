---
title: "Introducing Podman"
date: 2023-06-08T16:36:17-03:00
draft: false
---

Podman, short for *Pod Manager* is an enterprise-grade containerization tool.  It is largely associated with the RHEL family of distributions, however, it is a stand-alone project  - see [Podman.io](https://podman.io/) for tons of documentation - that runs on all enterprise-grade Linux distributions.

## Docker vs Podman
Docker has been the containerization standard for several years in enterprise computing.  However, Podman is a strong competitor with several significant advantages.  These can be summarized as:

|                                   | Docker                       | Podman                                   |
|:---------------------------------:|:----------------------------:|:----------------------------------------:|
| **Separate Daemon?**              | Uses Docker daemon           | Daemonless architecture                  |
| **Root Access?**                  | Runs containers as root only | Runs containers as `root` and non-`root` | 
| **Building Images**               | YAML-Based DockerFile        | YAML-Based Image File, Buildah tool      |
| **Monolithic??**                  | Yes                          | No                                       |
| **Orchestration?**                | Yes                          | Yes                                      |
| **Integrated into Linux Kernel?** | No                           | Yes                                      |

The biggest advantages that Podman enjoys is that it is *daemonless* - meaning that `root` access is not needed to run containers.  This is incredibly developer friendly in enterprise computing, as developers rarely have `root` access to servers.  Directly related to this daemonless architecture is that Podman is better integrated into the Linux kernel.  This has to do with the actual libraries in use and is beyond the scope of this article, but in short Podman is more Linux-kernel friendly.

The biggest disadvantage of Podman is that because Docker is so ubiquitous, it is easy to find a cookbook that includes Docker containers, and a developer will have to "translate" this into a Podman version.  However, as Podman and Docker are largely command-equivalent (at least in recent versions), this is becoming less and less of a challenge.

## Command-Equivalent to Docker

For developers who have used Docker in the past, it comes as a huge relief to know that Podman is command-equivalent in most regards.  This means that `podman run -p 80:80 nginx:latest` will produce exactly the same result as `docker run -p 80:80 nginx:latest` (all else being equal).  So, while there will be some minor migration pains, the process should be almost instant.

## A Quick Demo


