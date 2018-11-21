# Google cloud

## Kubeneretes Engine

### Containerization

Multiple applications running on a simple VM, needs to handle the different
dependencies, share the resources, and handle the isolation of processes on the
server.

Can be solved by running the apps on their own VMs. They will still use the same
kernel and OS. This is were the idea of containerization comes in.

Containerization referes to an OS feature in which the kernel allow the
existence of multiple isolated user-space instances. This allows to run on the
same hardware, and kernel, but ... complete isolation of dependencies and
processes.

### Docker

Dockerfiles defines the container. This forces documentation of all
dependencies, and architecture. Each line in the dockerfile creates and caches
smaller shared images. This means that new images will build on the cached
images. This layered ... makes this very portable.

Google cloud has image registry. This means you can:
1. Build container image
2. Push it to your registry (gcloud docker -- push)
3. Run it

So, in conclusion containers are efficient and portable.

> App egnine is also able to serve containers.

### Kubernetes

When running multiple containers, orcehstration is very important. If you
don't, it's just the same as running lot's of VMs. This is where Kubernetes
comes into play.

Containers are put into Pods. A pod is grop of container deployed as an
unit on a node that share network, namespaces, and storage. The pod shares
internal IP, volumes (storage), and namespace. It runs on a node (a VM).

The nodes are running inside of a cluster. The master node manages all the nodes
in the same cluster.

> In google cloud they manage the master for you. You don't have to pay for this
> node.
