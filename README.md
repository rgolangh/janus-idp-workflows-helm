# Janus-IDP-Workflows helm repo

This chart will install Janus-IDP + Serverless Workflows.

It is under development and meant for non-prod environment for now

The chart main deployment is the Serverless operator (see sonata-serverless-operator.yaml), and
the Janus-IDP and its deps goes as dependencies under the Chart.yaml

There is also a starter serverless workflow under the default namespace.

## Installation

```bash
helm repo add janus-idp-workflows https://rgolangh.github.io/janus-idp-workflows-helm

helm install janus-idp-workflows janus-idp-workflows/janus-idp-workflows
```

