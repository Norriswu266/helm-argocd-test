# helm-argocd-test

## 嘗試直接寫yaml腳本建立app

```
apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  name: helm-argocd-test-app
  namespace: argocd # for argocd application management
spec:
  project: default
  source:
    repoURL: https://github.com/Norriswu266/helm-argocd-test
    targetRevision: main
    path: . # chart location
    helm:
      valueFiles:
        - values.yaml
  destination:
    server: https://kubernetes.default.svc #Target K8S endpoint, for example: https://ABCD1234.gr7.ap-northeast-1.eks.amazonaws.com
    namespace: demo-app # target k8s resource namespace (multi namespace from source should create another argocd applications)
```

## 要先config憑證 才有資格把app生出來



## 重點在於要產生app, 是需要下
```
kubectl apply -f app.yaml
```

## 最後指令

git add . && git commit -m "test" && git push && argocd app sync helm-argocd-test-app
