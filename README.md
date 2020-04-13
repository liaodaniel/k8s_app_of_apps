# k8s_app_of_apps

Notes:

* Within Kustomize, base ref as branch name can't be used; argod will not resync.
* Auto-sync turned off, we can perform an app diff; local file yaml diff.
* Apps of apps pattern can be done, as long as there is an individual
  application CRD specifying a different path. They have to be managed on your own.

* Resource hooks are k8s resources with argocd annotations. These annotations are used to schedule them as part of the sync phase. Argocd will only proceed to the next part of the phase if the resources terminate successfully.
```
metadata:
  name: abc
  annotations:
	argocd.argoproj.io/hook: PreSync|Sync|Skip|PostSync|SyncFail

```

