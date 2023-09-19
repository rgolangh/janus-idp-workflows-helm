# Janus-IDP-Workflows helm repo

This chart will install Janus-IDP + Serverless Workflows.

It is under development and meant for non-prod environment for now

The chart main deployment is the Serverless operator (see sonata-serverless-operator.yaml), and
the Janus-IDP and its deps goes as dependencies under the Chart.yaml

There is also a starter serverless workflow under the default namespace.

## Installation

[!Note]
Due to a janus CI probelm the 'latest' image doesn't work out of the box. Eithr change the 
the image ref to one of the `nighly-X` listed [here](https://quay.io/repository/janus-idp/backstage-showcase?tab=tags) in the deployement or directly under the `charts/` folder.

Prerequisites:
  - Running OpenShift cluster, storage needed.
  - oc
  - helm


```bash

git clone https://github.com/rgolangh/janus-idp-workflows-helm

cd janus-idp-workflows-helm

helm install janus-idp-workflows .

# output should look like that
8:18 $ helm install  janus-idp-workflows-white .
Release "janus-idp-workflows-white" has been upgraded. Happy Helming!
NAME: janus-idp-workflows-white
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
