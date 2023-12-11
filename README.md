# Hello Nginx Config

Nginx config for simple hello project.

## Prerequisite
1. OpenShift 4.x cluster with admin access
2. OpenShift GitOps 1.11.x

## Setup

```shell
oc new-project hello
oc label namespace hello argocd.argoproj.io/managed-by=openshift-gitops
oc apply -f ./application.yaml
```

## Testing

```shell
curl --head https://$(oc get routes/hello-nginx-route -n hello -o jsonpath="{.spec.host}")
```

## See Changes

Update `base/kustomization.yaml` to change the image tag
to see argocd pick up change and deploy it.
