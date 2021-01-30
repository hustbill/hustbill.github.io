---
title: "Kubernetes Dashboard - skip Auth"
date: "2020-04-09 03:27:34"
draft: false
categories: [DevOps]
hiddenFromHomePage: true
---
Ref this doc: [Bypassing authentication for the local Kubernetes Cluster Dashboard]([https://devblogs.microsoft.com/premier-developer/bypassing-authentication-for-the-local-kubernetes-cluster-dashboard/](https://devblogs.microsoft.com/premier-developer/bypassing-authentication-for-the-local-kubernetes-cluster-dashboard/)
)

open the downloaded file in your favorite text editor, I’ll use VS Code.
```bash 
code .\kubernetes-dashboard.yaml
```
Locate the container -> args section under the Dashboard-Deployment section (around line 116) and add the following command line arguments:
```yaml
--enable-skip-login
--disable-settings-authorizer
```
Your modified args section should look like the following
```yaml
spec:
      containers:
      - name: kubernetes-dashboard
        image: k8s.gcr.io/kubernetes-dashboard-amd64:v1.10.1
        ports:
        - containerPort: 8443
          protocol: TCP
        args:
          - --enable-skip-login
          - --disable-settings-authorizer        
          - --auto-generate-certificates
          # Uncomment the following line to manually specify Kubernetes API server Host
          # If not specified, Dashboard will attempt to auto discover the API server and connect
          # to it. Uncomment only if the default does not work.
          # - --apiserver-host=http://my-address:port
        volumeMounts:
        - name: kubernetes-dashboard-certs
          mountPath: /certs
``` 
Save your changes and exit the text editor then install the dashboard from a PowerShell prompt in the same directory as the kubernetes-dashboard.yaml file:

```bash 
kubectl apply -f .\kubernetes-dashboard.yaml 
``` 
The output should look something like this:
```bash 
secret "kubernetes-dashboard-certs" created
serviceaccount "kubernetes-dashboard" created
role.rbac.authorization.k8s.io "kubernetes-dashboard-minimal" created
rolebinding.rbac.authorization.k8s.io "kubernetes-dashboard-minimal" created
deployment.apps "kubernetes-dashboard" created
service "kubernetes-dashboard" created
``` 
