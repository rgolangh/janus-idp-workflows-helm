# Janus-IDP-Workflows helm repo

This chart will install Janus-IDP + Serverless Workflows.

It is under development and meant for non-prod environment for now

The chart main deployment is the Serverless operator (see sonata-serverless-operator.yaml), and
the Janus-IDP and its deps goes as dependencies under the Chart.yaml

There is also a starter serverless workflow under the default namespace.

## Installation

### Using OCP developer catalog

Add the helm chart resource to the catalog


```bash
cat <<EOF | oc create -f -
apiVersion: helm.openshift.io/v1beta1
kind: HelmChartRepository
metadata:
  name: janus-idp-workflows
spec:
  connectionConfig:
    url: https://rgolangh.github.io/janus-idp-workflows-helm/
EOF
```

After few seconds, 'Helm' section under the developer perspective will present that chart repository, ready to use. 
From the 'Helm Releases' view click the 'Create' button and 'Helm Release' , locate and use the workflows chart search bar.


### Using CLI
```bash
helm repo add janus-idp-workflows https://rgolangh.github.io/janus-idp-workflows-helm

helm install janus-idp-workflows janus-idp-workflows/janus-idp-workflows
```

