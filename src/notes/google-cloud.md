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

#### Configuration

Kubernetes is configured using YAML files.

> ReplicaSet: How many replicas of the pod should be running.

## Big Data and Machine Learning in the cloud

### Data pipelines

* Cloud storage (batch storage)
  Raw logs, database extracts, etc.
* Cloud Pub/Sub (stream)
  Events, metrics, etc.

#### Cloud DataFlow

You can have a unified data processing from both of these with Cloud Dataflow,
and store/retrieve the data with BigQuery. DataFlow can be used for ETL, Analysis,
orchestration, etc.

#### Cloud Dataproc

* Managed Hadoop MapReduce, Spark, Pig, and Hive service
* Create clusters in less tha 90sec avg.
* Scale clusters

#### BigQuery

Data Warehouse that supports industry standards (SQL, JDBC, ODBC). Fully managed
and serverless. Only pays for storage used. Hybrid of relational and dynamic
database. Every column is saved as a file. This allows horizontal expansion (??).

It's very fast when executing advanced queries, and also caches the
response. This means you only pay for each query once if data don't change.

Include lot's of public datasets.

BigQuery ML is a product that can give you a collection of data based on other
data. This can be used to e.g. recomendation.

Demo:
* GitHub: queryItSmart
* YouTube: An overview of Cloud IoT Core (Google I/O 18)

### ML

Cloud Datalab

* Notebook-interface
* Scalable

Machine Learning APIs

* Build your own models (TensoFlow, Cloud ML Engine)
* in-between: Cloud AutoML
* APIs: Vision API, Speech API, Translation API, Natural Language API, ...

#### AutoML

You have some things, label them, train model, evaluate.

#### Vision API

* Object recognition
* Facial sentiment & logos
* Extract text (OCR)
  Example: Giro app (classify invoices)
* Detect inappropiate content

#### Speech API

* Speech recognition
* Word hints
* Noise robustness
* Real-time results
* Over 100 languages

#### Translation API

* Text translation
* Auto language deteection
* Continoues updates
* Premium edition (beta)

#### Natural Language API

* Entity Recognition
* Sentiment Analysis
* Multi-language Support
* Syntax Analysis
