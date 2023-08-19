```groovy
pipeline {
    agent any

    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/EmAdd9/Shopping-Cart.git'
            }
        }
        stage('Kubernetes Deployment') {
            steps {
                sh "echo 1234 | sudo -S kubectl get nodes"
                sh "echo 1234 | sudo -S kubectl apply -f deploymentservice.yml"
                sh "echo 1234 | sudo -S kubectl get pods"
                sh "echo 1234 | sudo -S kubectl get svc"
            }
        }
    }
}
```

**Pipeline Output:**

```
+ echo 1234
+ sudo -S kubectl get nodes
NAME               STATUS   ROLES                  AGE   VERSION
ip-172-31-32-8     Ready    <none>                 95m   v1.20.0
ip-172-31-39-189   Ready    control-plane,master   98m   v1.20.0
[Pipeline] sh
+ echo 1234
+ sudo -S kubectl apply -f deploymentservice.yml
deployment.apps/spring-boot-k8s-deployment configured
service/springboot-k8ssvc unchanged
[Pipeline] sh
+ sudo -S kubectl get pods
+ echo 1234
NAME                                          READY   STATUS              RESTARTS   AGE
spring-boot-k8s-deployment-767bb67c99-6ndpx   0/1     ContainerCreating   0          0s
spring-boot-k8s-deployment-784fc786b6-cjv94   1/1     Running             0          5m5s
spring-boot-k8s-deployment-784fc786b6-hhvxq   1/1     Running             0          4m59s
[Pipeline] sh
+ echo 1234
+ sudo -S kubectl get svc
NAME                TYPE           CLUSTER-IP       EXTERNAL-IP   PORT(S)          AGE
kubernetes          ClusterIP      10.96.0.1        <none>        443/TCP          98m
springboot-k8ssvc   LoadBalancer   10.100.140.150   <pending>     8070:30636/TCP   50m
[Pipeline] }
[Pipeline] // stage
[Pipeline] }
[Pipeline] // node
[Pipeline] End of Pipeline
Finished: SUCCESS
```

---

The provided Jenkins pipeline script performs steps related to Git checkout and Kubernetes deployment, while the output shows the execution of each step along with the corresponding command outputs.
