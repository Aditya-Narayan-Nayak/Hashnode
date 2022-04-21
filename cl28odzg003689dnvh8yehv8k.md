## How to Test Kubescape without having K8s Cluster?


- Log In to https://www.katacoda.com/


- Then Goto Learn -> Kubernetes -> Lunch a Multinode K8s Cluster

-Start the scenario

- Follow the instruction and get your Kubernetes Cluster

- Once You Get the cluster running 

- install Kubescape from the following command
```
curl -s https://raw.githubusercontent.com/armosec/kubescape/master/install.sh | /bin/bash
```

- Run Kubescape on the cluster using the following command 
```
kubescape scan --submit --enable-host-scan
```
Hurry You Got the Kubescape Result

After scanning is finished you will get a link copy and paste the link into the web browser you will find the UI version Of kubescape

I Hope You Enjoyed it!







