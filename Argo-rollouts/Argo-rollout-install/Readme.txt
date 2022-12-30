Installation

Controller Installation
    kubectl create namespace argo-rollouts
    kubectl apply -n argo-rollouts -f https://github.com/argoproj/argo-rollouts/releases/latest/download/install.yaml

Kubectl Plugin Installation
    curl -LO https://github.com/argoproj/argo-rollouts/releases/latest/download/kubectl-argo-rollouts-linux-amd64
    
    chmod +x ./kubectl-argo-rollouts-linux-amd64 

    sudo mv ./kubectl-argo-rollouts-linux-amd64 /usr/local/bin/kubectl-argo-rollouts

    ===> for cheking ==> kubectl argo rollouts version

                        output
                        ------
                        kubectl-argo-rollouts: v1.3.2+f780534
                          BuildDate: 2022-12-15T16:01:35Z
                          GitCommit: f780534ebd66a4047c813ddd7841be93b122c3e6
                          GitTreeState: clean
                          GoVersion: go1.18.9
                          Compiler: gc
                          Platform: linux/amd64
