# openshift-prow-demo

This repository is used to document the steps I've taken in order to deploy Prow onto OpenShift 4

## Unorganized steps and notes

Create oauth toke on github

openssl rand -hex 20 -out hmac-token

oc create secret generic hmac-token --from-file=hmac=hmac-token

oc create secret generic oauth-token --from-literal=oauth=c090948b63a0ff78526d3e9dece69edb8d783679

https://github.com/kubernetes/test-infra/blob/master/config/prow/cluster/starter.yaml
  - cm_plugins - default
  - cm_config - default
  - crd_prowjobs.prow.k8s.io - current
  - deployment_hook - default
  - svc_hook - default
  - deployment_plank - default
  - deployment_sinker - default
  - deployment_deck - default
  - svc_deck - default
  - deployment_horologium - default
  - deployment_tide - default
  - svc_tide - default
  - Ingress_ ing - default
  - deployment_statusreconciler - default
  - sa_deck
  - rb-deck - default + testpods
  - role_deck - default + testpods
  - sa_horologium
  - role_horologium
  - rb_horologium
  - sa_plank
  - role_plank default + testpods
  - rb_plank default + testpods
  - sa_sinker
  - role_sinker default + testpods
  - rb_sinker default + testpods
  - sa_hook
  - role_hook
  - rb_hook
  - sa_tide
  - role_tide
  - rb_tide
  - sa_statusreconciler
  - role_statusreconciler
  - rb_statusreconciler
  

## References

  - Github page: https://github.com/kubernetes/test-infra/tree/master/prow
  - Documentation: https://jenkins-x.io/docs/reference/components/prow/
  - List of internal plugins: https://github.com/jenkins-x/test-infra/blob/master/prow/hook/plugins.go
  - Medium article 1: https://medium.com/@jdrawlings/serverless-jenkins-with-jenkins-x-9134cbfe6870
  - Medium article 2: https://medium.com/@vbehar/jenkins-x-pipelines-internals-part-1-from-github-webhook-event-to-tekton-pipeline-6927c6eb879c
