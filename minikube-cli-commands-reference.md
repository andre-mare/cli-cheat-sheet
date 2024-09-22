# Quick Reference: MiniKube CLI Commands

## What is minikube?
Minikube creates a local Kubernetes cluster on macOS, Linux, and Windows. A production Kubernetes cluster setup consists
of at least two master nodes and multiple worker nodes on separate virtual or physical machines. 

Minikube allows you to run a single-node Kubernetes cluster on your development machine. Both the master and worker 
processes are running on a single node. 

The docker runtime environment is pre-installed in the node.

## Minikube Commands Index
The Minikube Command Index section provides a list of all available Minikube commands, organized by function for easier 
navigation. The set of minikube commands were based minikube version: `v1.34.0`.

### Basic Commands:
* [`minikube start`](#minikube-start) - Initializes and starts a local Kubernetes cluster with options. ([Reference](https://minikube.sigs.k8s.io/docs/commands/start/))
* [`minikube status`](#minikube-status) - Displays the status of the Minikube cluster and its components. ([Reference](https://minikube.sigs.k8s.io/docs/commands/status/))
* [`minikube stop`](#minikube-stop) - Stops the running Minikube cluster and frees system resources. ([Reference](https://minikube.sigs.k8s.io/docs/commands/stop/))
* [`minikube delete`](#minikube-delete) - Deletes the Minikube cluster and removes associated resources. ([Reference](https://minikube.sigs.k8s.io/docs/commands/delete/))
* [`minikube dashboard`](#minikube-dashboard) - Opens the Kubernetes dashboard in the default web browser. ([Reference](https://minikube.sigs.k8s.io/docs/commands/dashboard/))
* [`minikube pause`](#minikube-pause) - Pauses all running Kubernetes pods in the Minikube cluster. ([Reference](https://minikube.sigs.k8s.io/docs/commands/pause/))
* [`minikube unpause`](#minikube-unpause) - Unpauses all previously paused Kubernetes pods in the cluster. ([Reference](https://minikube.sigs.k8s.io/docs/commands/unpause/))

### Images Commands:
* `minikube docker-env` - Configures environment to use Minikube's Docker daemon locally. ([Reference](https://minikube.sigs.k8s.io/docs/commands/docker-env/))
* `minikube podman-env` - Configures environment to use Minikube's Podman service locally. ([Reference](https://minikube.sigs.k8s.io/docs/commands/podman-env/))
* [`minikube cache`](#minikube-cache ) - Manages cached images for faster container deployments in Minikube. ([Reference](https://minikube.sigs.k8s.io/docs/commands/cache/))

### Configuration and Management Commands:
* [`minikube addons`](#minikube-addons) - Manages Minikube addons for enhanced cluster functionality. ([Reference](https://minikube.sigs.k8s.io/docs/commands/addons/))
* [`minikube config`](#minikube-config) - Manages Minikube configuration settings and preferences. ([Reference](https://minikube.sigs.k8s.io/docs/commands/config/))
* `minikube profile` - Manages multiple Minikube profiles for different environments. ([Reference](https://minikube.sigs.k8s.io/docs/commands/profile/))
* `minikube update-context` - Updates the Kubernetes context for the current Minikube cluster. ([Reference](https://minikube.sigs.k8s.io/docs/commands/update-context/))

### Networking and Connectivity Commands:
* [`minikube service`](#minikube-service) - Accesses a service in the Minikube cluster via a URL. ([Reference](https://minikube.sigs.k8s.io/docs/commands/service/))
* `minikube tunnel` - Creates a network tunnel to expose services in Minikube. ([Reference](https://minikube.sigs.k8s.io/docs/commands/tunnel/))

### Advanced Commands:
* `minikube mount` - Mounts a host directory into the Minikube VM. ([Reference](https://minikube.sigs.k8s.io/docs/commands/mount/))
* `minikube ssh` - Accesses the Minikube VM via SSH for troubleshooting. ([Reference](https://minikube.sigs.k8s.io/docs/commands/ssh/))
* [`minikube kubectl`](#minikube-kubectl) - Invokes kubectl commands using the Minikube context. ([Reference](https://minikube.sigs.k8s.io/docs/commands/kubectl/))
* `minikube node` - Manages Minikube cluster nodes and their configurations. ([Reference](https://minikube.sigs.k8s.io/docs/commands/node/))

### Troubleshooting Commands:
* `minikube ssh-key` - Displays the SSH key for accessing the Minikube VM. ([Reference](https://minikube.sigs.k8s.io/docs/commands/ssh-key/))
* [`minikube ip`](#minikube-ip) - Displays the IP address of the Minikube cluster. ([Reference](https://minikube.sigs.k8s.io/docs/commands/ip/))
* [`minikube logs`](#minikube-logs) - Retrieves logs from the Minikube cluster for debugging. ([Reference](https://minikube.sigs.k8s.io/docs/commands/logs/))
* [`minikube update-check`](#minikube-update-check) - Checks for updates available for the Minikube installation. ([Reference](https://minikube.sigs.k8s.io/docs/commands/update-check/))
* [`minikube version`](#minikube-version) - Displays the current Minikube version information. ([Reference](https://minikube.sigs.k8s.io/docs/commands/version/))

### Other Commands:
* `minikube completion` - Generates shell completion scripts for Minikube commands. ([Reference](https://minikube.sigs.k8s.io/docs/commands/completion/))
* `minikube help` - Displays help information for Minikube commands and usage. ([Reference](https://minikube.sigs.k8s.io/docs/commands/help/))
* `minikube options` - Displays global options available for Minikube commands. ([Reference](https://minikube.sigs.k8s.io/docs/commands/options/))


## Minikube Command Examples


### minikube addons

```shell
# Lists all available minikube addons as well as their current statuses
$ minikube addons list

# Disables the addon `dashboard` within minikube.
$ minikube addons disable dashboard

# Enables the addon `dashboard` within minikube.
$ minikube addons enable dashboard

# Enables the addon `metrics-server` within minikube.
$ minikube addons enable metrics-server

# Open the dashboard addon in a browser, since it exposes a browser endpoint.
$ minikube addons open dashboard
```

<b><a id="minikube-cache">minikube cache</a></b>

Add, delete, or push a local image into minikube. See the `~/.minikube/cache/images` directory.

```shell
# List all the available images from the local cache.
$ minikube cache list

# Add the latest version of the nginx image to the local cache.
$ minikube cache add nginx:latest

# Reload the latest version of the nginx image to the local cache.
$ minikube cache reload nginx:latest

# Delete the latest vesrion of the nginx image from the local cache.
$ minikube cache delete nginx:latest
```

<b><a id="minikube-config">minikube config</a></b>
```shell
# Set the memory field to 16GB in the minikube config file (~/.minikube/config/config.json)
$ minikube config set memory 16384

# Display values currently set in the minikube config file (~/.minikube/config/config.json)
$ minikube config view

# Unsets the memory field in the minikube config file (~/.minikube/config/config.json)
$ minikube config unset memory
```

<b><a id="minikube-dashboard">minikube dashboard</a></b>
```shell
# Access the Kubernetes dashboard running within the minikube cluster
$ minikube dashboard

# Display dashboard URL instead of opening a browser
$ minikube dashboard --url
```

<b><a id="minikube-delete">minikube delete</a></b>
```shell
# Deletes a local Kubernetes cluster
$ minikube delete

# Deletes a local Kubernetes cluster & delete all profiles
$ minikube delete --all

# Deletes a local Kubernetes cluster & delete the '.minikube' folder from your user directory.
$ minikube delete --purge
```

<b><a id="minikube-ip">minikube ip</a></b>
```shell
# Retrieves the IP address of the running cluster, and writes it to STDOUT.
$ minikube ip
```

<b><a id="minikube-kubectl">minikube kubectl</a></b>

Use kubectl inside minikube
```shell
# Retrieve all the pods
$ minikube kubectl -- get pods

# Creating a deployment inside kubernetes cluster
$ minikube kubectl  -- create deployment hello-minikube --image=k8s.gcr.io/echoserver:1.4

# Exposing the deployment with a NodePort service
$ minikube kubectl -- expose deployment hello-minikube --type=NodePort --port=8080

# Display help
$ minikube kubectl -- --help
```

<b><a id="minikube-logs">minikube logs</a></b>
```shell
# Gets the logs of the running instance, used for debugging minikube, not user code.
$ minikube logs

# Display the logs of the running instance and continously print new entries
$ minikube logs -f
```

<b><a id="minikube-pause">minikube pause</a></b>
```shell
# Pause the Kubernetes cluster
$ minikube pause
```

<b><a id="minikube-service">minikube service</a></b>
```shell
# List the kubernetes URLs for the services in the local cluster. This is the same as `kubectl get svc -A`
$ minikube service list
```

<b><a id="minikube-start">minikube start</a></b>
```shell
# Starts a local Kubernetes cluster 
$ minikube start

# Starts a local Kubernetes cluster with a profile name allowing multiple instances of minikube independently. (default "minikube")
$ minikube start --profile my-profile-name

# Starts a local kubernetes cluster and enable the metrics-server and dashboard addons at start-up.
$ minikube start --addons metrics-server --addons dashboard

# Starts a local kubernetes cluster with one of the drivers: virtualbox, parallels, vmwarefusion, hyperkit, vmware, docker, podman (experimental) (defaults to auto-detect)
$ minikube start --driver='hyperkit'

# Start a local kubernetes cluster in `debug` mode.
$ minikube start --v=7 --alsologtostderr

# Start a local kubernetes cluster and change the cluster version. (Supports any published Kubeadm build (>=1.8))
$ minikube start --kubernetes-version 1.16.1

# Start a local kubernetes cluster and choose a different container runtime (default:docker, cri-o, rkt)
$ minikube start --container-runtime=rkt

# Start a local kubernetes cluster and add configuration
$ minikube start --extra-config=kubelet.foo.bar=baz
```

<b><a id="minikube-status">minikube status</a></b>
```shell
# Gets the status of a local Kubernetes cluster.
$ minikube status
```

<b><a id="minikube-status">minikube stop</a></b>
```shell
# Stops a local Kubernetes cluster. This command stops the underlying VM or container, but keeps user data intact.
$ minikube stop
```

<b><a id="minikube-unpause">minikube unpause</a></b>
```shell
# Unpause the Kubernetes cluster
$ minikube unpause
```

<b><a id="minikube-update-check">minikube update-check</a></b>
```shell
# Print current and latest version number of minikube
$ minikube update-check
```

<b><a id="minikube-version">minikube version</a></b>
```shell
# Print the version of minikube
$ minikube version

# Print the version of minikube in yaml format
$ minikube version --output='yaml'

# Print the version of minikube in json format
$ minikube version --output='json'
```