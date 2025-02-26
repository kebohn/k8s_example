# K8s Example with Minikube (Linux)

## Prerequisites

- Install minikube

  ```bash
  curl -LO https://github.com/kubernetes/minikube/releases/latest/download/minikube-linux-amd64
  sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64
  ```

- Install Docker Engine from here: https://docs.docker.com/engine/install/
  
- If you don't want to preface the docker command with sudo, create a Unix group called docker and add users to it:

  1. Create the docker group.
    ```bash sudo groupadd docker```
  2. Add your user to the docker group.
    ```bash sudo usermod -aG docker $USER```
  3. Run the following command to activate the changes to groups:
    ```bash newgrp docker```
  5. Verify that you can run docker commands without sudo.
    ```bash docker run hello-world```

- Install k9s:

    ```bash wget https://github.com/derailed/k9s/releases/download/v0.25.18/k9s_Linux_x86_64.tar.gz -O /tmp/k9s_Linux_x86_64.tar.gz```
    ```bash sudo tar xvf /tmp/k9s_Linux_x86_64.tar.gz -C /usr/bin/ k9s```

## Setup

- Create alias for kubectl

  ```bash alias kubectl="minikube kubectl --"```
  
- Run Bash scripts:

  1. Build Docker Image
    ```bash bash scripts/build_and_push.sh```
  2. Apply k8s deployemnt
     ```bash bash scripts/k8s_deployment.sh```
  3. Use minkube tunnel in detached mode to allow external ip access
     ```bash screen -S minikube-tunnel```
     ```bash minikube tunnel```
  4. Detach from screen with Ctrl + A, then D
  5.(Optional) Reattach with:
    ```bash  screen -r minikube-tunnel```
     
