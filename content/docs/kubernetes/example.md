---
title: "Basic Commands"
description: "Guides lead a user through a specific task they want to accomplish, often with a sequence of steps."
summary: ""
date: 2023-09-07T16:04:48+02:00
lastmod: 2023-09-07T16:04:48+02:00
draft: false
weight: 810
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---

## Baseline commands

`kubectl get pods` - check if the pods are starting correctly. You can add `| grep -c <deployment-name>` to count how many pods you have at a current time. You can also filter by label: \
`kubectl get pods -l 'labelname=labelvalue'`

`kubectl get deploy -o wide` - tells you which version it is getting from the repo, so you can be sure that you are deploying to the correct one. You can also check how many replicas are updated.

`kubectl get configmap <config-map-name>` (or `kubectl get cm` for lazy people like me) - check the config maps that exist. BUT they all already exist basically, so what you usually want to check is what’s inside them with: \
`kubectl describe cm <config-map-name>`.

Note that if you update the configmap, the values read by the pod don’t change automatically. The cm are read at the beginning of the deploy so in order to have it read you need to restart the pods.

`kubectl get quota` -  if you see your pods are not starting and your deployment is stuck, it might be because you ran out of quota. You can also check errors in the events


## Getting logs and events

If you need to check events:

`kubectl get events --sort-by='.metadata.creationTimestamp'`

And now logs:

`kubectl get logs -f <pod_name>`

Or for pods that have been restarted:

`kubectl get logs <pod_name> —previous`


## Creating Secrets

Secrets are objects that generally contain sensitive information, such as tokens or secrets. They behave similarly to a configmap but they are used only for sensitive information, so it’s not hardcoded in the application code.

Each secret can have several keys, and therefore, several passwords or other pieces of information. You can therefore have a secret called `credentials` where inside you have two keys `password` and `user` with each respective value. Don’t forget that when reading a secret in your pod.yaml configs you need to specify both the secret name and the key from which you need the value:

```
- name: ENV_VAR_NAME
    valueFrom:
      secretKeyRef:
        name: secret_name
        key: password # or whatever your key is
```


## Reading secrets:

`kubectl edit secret <secret—name>` and you can see the secret value there (but don’t edit it!)

but it will show you the secret info and the value encoded in base64. To read it back you must do:

`kubectl get secret <SECRET_NAME> "--template={{.data.password}}" | base64 --decode`

Note that if you do want to edit it like that, you need to convert it to base64 before that.

## Accessing other services:
From inside the cluster:

`curl <service-name>.<namespace-name>:<port>`

If the service you are trying to access is in the namespace as your pod currently is, then you can omit the namespace name and just do\
`<service-name>:<port>`

Or just use the internal ingress associated with the service. Get it with:

`kubectl get ingress`

## Going inside the pod

`kubectl exec -it <pod-name> bash` → if you have only one container in your pod, it will go inside that container. Otherwise, you will have to specify which container in that pod you are trying to access by using `-c <container-name>`.

`printenv` - run this command while inside the container to print all the environment variables that this is reading. It is particularly useful to verify if the config map and secrets are being correctly read in the pod.

`ping <url>` or `curl <url>` - some services are not accessible through your local machine, but only inside the cluster. You can run this inside a pod.

## Requesting without an ingress

`kubectl port-forward <pod-name> <local-port:pod-port>` - useful to do testing curls from your local machine

