# k8s_app_of_apps

Notes:

* Within Kustomize, base ref as branch name can't be used; argod will not resync.
* Auto-sync turned off, we can perform an app diff; local file yaml diff.
* Apps of apps pattern can be done, as long as there is an individual application CRD specifying a different path.
```
project: default
source:
  repoURL: 'https://github.com/liaodaniel/k8s_app_of_apps.git'
  path: clusters/apne1/barfoo
  targetRevision: HEAD
  kustomize:
    namePrefix: apne1
destination:
  server: 'https://kubernetes.default.svc'
  namespace: default

---
project: default
source:
  repoURL: 'https://github.com/liaodaniel/k8s_app_of_apps.git'
  path: clusters/apse2/foobar
  targetRevision: HEAD
destination:
  server: 'https://kubernetes.default.svc'
  namespace: default
syncPolicy: {}

```

