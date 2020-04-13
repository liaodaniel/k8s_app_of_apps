# k8s_app_of_apps

Notes:

* Within Kustomize, base ref as branch name can't be used; argod will not resync.
* Auto-sync turned off, we can perform an app diff; local file yaml diff.
* Apps of apps pattern can be done, as long as there is an individual
  application CRD specifying a different path. They have to be applied on your own.

* Resource hooks are k8s resources with argocd annotations. These annotations are used to schedule them as part of the sync phase. Argocd will only proceed to the next part of the phase if the resources exit with code 0.
```
metadata:
  name: abc
  annotations:
	argocd.argoproj.io/hook: PreSync|Sync|Skip|PostSync|SyncFail

```
* Argocd is also capable of performing CI, https://github.com/argoproj/argo/blob/master/examples/README.md for info.
* Argocd works by polling out of the box (2-3 min intervals). However, argocd-events could potentially be used to run argocd sync on github webhook events.
