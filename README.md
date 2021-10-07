# Deploying a website using Custom Helm Charts

## Introduction

This is a v.good practice project as how to deploy a nodeport based website.

It uses customize chart functions, variables, pipelines etc.

Some of the values are taken from the default creation of chart but re-written and cleaned-up to get more information as how powerful the helm chart is.

## Version

We are using Helm 3 and tested and verified it on Minikube

## Installation

To install the chart, simply copy the files into your machine, then goto that directory and finally run the command;

```
helm install <chart-name> . --namespace=qa-env --create-namespace --wait
```

Then to verify you can do a smoke test

```
helm test <chart-name>
```

Also to view info about the chart run;

```
helm list --namespace=qa-env
```

###### NOTE:

> You may get some warning about ingress version as this is a test case where we used some advanced method how to make use to chart functions, variable etc so please ignore it.



## Running it on Minikube

Simply search for the service as per your <chart-name> and copy the complete service name for e.g.

```
[developer@minikube web-chart]$ kubectl get services --namespace=qa-env
NAME                   TYPE       CLUSTER-IP      EXTERNAL-IP   PORT(S)          AGE
my-website-web-chart   NodePort   10.107.17.109   <none>        4444:30294/TCP   14m
```

Now use the minikube adminisrative command and deploy this as a service.

```
[developer@minikube web-chart]$ minikube service my-website-web-chart --namespace=qa-env
|-----------|----------------------|-------------|------------------------------|
| NAMESPACE |         NAME         | TARGET PORT |             URL              |
|-----------|----------------------|-------------|------------------------------|
| qa-env    | my-website-web-chart | http/4444   | http://192.168.100.182:30294 |
|-----------|----------------------|-------------|------------------------------|
🎉  Opening service qa-env/my-website-web-chart in default browser...
👉  http://192.168.100.182:30294
```

Then use the address to view the webpage.



Have fun !!