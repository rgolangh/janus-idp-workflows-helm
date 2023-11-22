# Janus-IDP-Workflows helm repo

This chart will install Janus-IDP + Serverless Workflows.

It is under development and meant for non-prod environment for now

The chart main deployment is the Serverless operator (see sonata-serverless-operator.yaml), and
the Janus-IDP and its deps goes as dependencies under the Chart.yaml

There is also a starter serverless workflow under the default namespace.

## Installation

### Installing on k8s
The default `values.yaml` work on OCP. Use the additional values-k8s.yaml when installing on k8s:

#### Installing from source chart repo
```console
helm install janus-idp-workflows charts/janus-idp-workflows -f charts/janus-idp-workflows/values.yaml  -f charts/janus-idp-workflows/values-k8s.yaml
```

#### Install from a released chart

```console
helm repo add janus-idp-workflows https://rgolangh.github.io/janus-idp-workflows-helm

helm install janus-idp-workflows janus-idp-workflows/janus-idp-workflows
```

Note: the installation defaults to Openshift. To override and use k8s use this:

```console
helm install janus-idp-workflows janus-idp-workflows/janus-idp-workflows \
    --set-json='{"backstage":{"route":{"enabled":false}},"global":{"openshift":false},"serverless-knative":{"kubernetes":{"enabled":true},"openshift":{"enabled":false}}}
'
```

## Development
```console
git clone https://github.com/rgolangh/janus-idp-workflows-helm

cd janus-idp-workflows-helm/charts/jaunus-idp-workflows

helm dependencies build
helm install janus-idp-workflows . -f values.yaml -f values-k8s.yaml
```


Output should look like that
```console
$ helm install janus-idp-workflows .
Release "janus-idp-workflows" has been upgraded. Happy Helming!
NAME: janus-idp-workflows
LAST DEPLOYED: Tue Sep 19 18:19:07 2023
NAMESPACE: default
STATUS: deployed
REVISION: 1
NOTES:
This chart will install Janus-IDP + Serverless Workflows.

It is under development and meant for non-prod environment for now

To get Jauns-IDP's route location:
    $ oc get route janus-idp-workflows-white-backstage -o jsonpath='https://{ .spec.host }{"\n"}'

To get the serverless workflow operator status:
    $ oc get deploy -n sonataflow-operator-system 

To get the serverless workflow status:
    $ oc get sf starter 

```

The chart notes will provide more information on:
  - route location of backstage
  - the sonata operator status
  - the sonata workflow deployed status
