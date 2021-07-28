NOTE: Detailed docs for openfaas setup can be found on [openfaas/workshop](https://github.com/openfaas/workshop/blob/master/lab1.md) repository. This is a trimmed down version of the doc for personal use.

Step by Step progress to openfaas
---

OpenFaaS requires a Kubernetes cluster to operate. You can use a single-node cluster or a multi-node cluster, whether that's on your laptop or in the cloud.

The basic primitive for any OpenFaaS function is a Docker image, which is built using the faas-cli tool-chain.

---

# Pre-requisites:
Let's install Docker, the OpenFaaS CLI and setup Kubernetes.

For Windows

Use Windows 10 Pro or Enterprise only
Install Docker CE for Windows
> Please ensure you use the Linux containers Docker daemon by using the Docker menu in the Windows task bar notification area.

Install Git Bash
When you install git bash pick the following options: install UNIX commands and use true-type font.

> Note: please use Git Bash for all steps: do not attempt to use PowerShell, WSL or Bash for Windows.

OpenFaaS CLI
You can install the OpenFaaS CLI using the official bash script, brew is also available but can lag one or two versions behind.

For Windows, run this in Git Bash:

```sh
$ curl -sLSf https://cli.openfaas.com | sh
```

> If you run into any issues then you can download the latest `faas-cli.exe` manually from the [releases page](https://github.com/openfaas/faas-cli/releases). You can place it in a local directory or in the `C:\Windows\` path so that it's available from a command prompt.

We will use the `faas-cli` to scaffold new functions, build, deploy and invoke functions. You can find out commands available for the cli with `faas-cli --help`.

Test the `faas-cli`. Open a Terminal or Git Bash window and type in:

```sh
$ faas-cli help
$ faas-cli version
```

NEXT: [Setup Single Node Kubernetes Cluster](./kubernetes-cluster-setup.md)
