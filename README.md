# Kubernetes challenge

Deploy this application to [Minikube](https://github.com/kubernetes/minikube) and customise the environment variable to display your name.

```
$ curl $(minikube ip)
Hello Dan!
```

## Instructions

- Fork this repo
- Build the Docker image
- Write yaml files for a deployment, service, ingress and configmap
- Deploy your application to Minikube
- You should be able to `curl` Minikube's ip and retrieve the string `Hello {yourname}!`
- Commit your files to Github

## Notes

There's no need to push the Docker image to a Docker registry. You should be able to build and use the image from within Minikube.

You can expose Minikube's Docker daemon with:

```shell
$ eval (minkube docker-env)
```

### Deployment tips

Once you have minikube installed and have enabled Minikube's Docker daemon as instructed previously, don't forget to push your image to the Minikube's internal registry once you have built the Dockerfile.

```shell
$ minikube image load k8s-challenge:latest
```

In order to use the ingress resource you created, you will need to either install an Ingress controller on your minikube cluster or enable the included add-on.

```shell
$ minikube addons enable ingress
```

If you stumble across a nasty trailing space showing after the variable's name try defining the ConfigMap as oneliner and not multiline format.


```shell
.
.
data:
  NAME: Your_Name
```
