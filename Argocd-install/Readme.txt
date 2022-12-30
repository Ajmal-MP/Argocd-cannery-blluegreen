#getting started 
1.installation Argocd

    kubectl create ns argocd

    # install core + UI, SSO, multi-cluster:
    kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
     
    # install core Argo CD components only: 
    kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/core-install.yaml

2.Install Argocd cli / latest

curl -sSL -o argocd-linux-amd64 https://github.com/argoproj/argo-cd/releases/latest/download/argocd-linux-amd64
sudo install -m 555 argocd-linux-amd64 /usr/local/bin/argocd
rm argocd-linux-amd64

3. Access The Argo CD API Server
   By default argocd-server svc type is Clusterip change it to LoadBalancer
    
   kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}'
                               or
   kubectl edit svc argocd-server -n argocd                             
                 - And add type: LoadBalancer
4. Login Using command line interface

   a) Get the secret passwd to Login
      kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
   
   b) Login
        argocd login <ARGOCD_SERVER>
             - where user name = admin
             - password = the out put geted from 4.a
   c) To change the passwd
        argocd account update-password          

5.Create Application from git repo
    a) set current name space to argocd  
        kubectl config set-context --current --namespace=argocd
    b) create Application
        argocd app create guestbook --repo https://github.com/argoproj/argocd-example-apps.git --path guestbook --dest-server https://kubernetes.default.svc --dest-namespace default
    
6. Sync (Deploy) The Application
     argocd app get guestbook
     argocd app sync guestbook


# Defining manifest file

1. upload a local application
   argocd app sync APPNAME --local /path/to/dir/