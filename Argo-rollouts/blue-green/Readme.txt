1)  Create 2 service for active service and preview service 
     
      kubectl create -f service.yml

2) create a blue green deployment

    kubectl create -f bluegreen.yaml

3) check for the rollouts
  
  kubectl get rollouts

4) watch the rollouts
   
    kubectl argo rollouts get rollout  <name fo rollout>    --watch

5) change the image name

    kubectl argo rollouts set image  <rollout name>  <Container name>=image:[tag]

    kubectl argo rollouts set image rollout-bluegreen rollouts-demo=argoproj/rollouts-demo:yellow  

6)  a) enable promotion

        kubectl argo rollouts promote rollout-bluegreen
    
    b) Abort Rollout

        kubectl argo rollouts aboort 
