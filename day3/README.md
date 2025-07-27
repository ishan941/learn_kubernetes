ishanshrestha@Ishans-MacBook-Air ~/development/learnkube % mkdir day3 && cd day3

ishanshrestha@Ishans-MacBook-Air ~/development/learnkube/day3 % touch deployment.yaml

ishanshrestha@Ishans-MacBook-Air ~/development/learnkube/day3 % touch service.yaml

ishanshrestha@Ishans-MacBook-Air ~/development/learnkube/day3 % kubectl apply -f deployment.yaml
deployment.apps/hello-app created

ishanshrestha@Ishans-MacBook-Air ~/development/learnkube/day3 % kubectl apply -f service.yaml
service/hello-app-service created

ishanshrestha@Ishans-MacBook-Air ~/development/learnkube/day3 % kubectl get deployments

NAME READY UP-TO-DATE AVAILABLE AGE
hello-app 2/2 2 2 9s
hello-node 2/2 2 2 22m

ishanshrestha@Ishans-MacBook-Air ~/development/learnkube/day3 % kubectl get pods
NAME READY STATUS RESTARTS AGE
hello-app-57669678fc-2c5dg 1/1 Running 0 14s
hello-app-57669678fc-86rpv 1/1 Running 0 14s
hello-node-7b5bd4c5b4-kgscx 1/1 Running 0 22m
hello-node-7b5bd4c5b4-wpgxz 1/1 Running 0 22m
my-nginx 1/1 Running 0 3m52s

ishanshrestha@Ishans-MacBook-Air ~/development/learnkube/day3 % kubectl scale deployment hello-app --replicas=5
deployment.apps/hello-app scaled

ishanshrestha@Ishans-MacBook-Air ~/development/learnkube/day3 % kubectl get pods

NAME READY STATUS RESTARTS AGE
hello-app-57669678fc-2c5dg 1/1 Running 0 27s
hello-app-57669678fc-86rpv 1/1 Running 0 27s
hello-app-57669678fc-czgj2 1/1 Running 0 6s
hello-app-57669678fc-mdtsf 1/1 Running 0 6s
hello-app-57669678fc-zp22v 1/1 Running 0 6s
hello-node-7b5bd4c5b4-kgscx 1/1 Running 0 22m
hello-node-7b5bd4c5b4-wpgxz 1/1 Running 0 22m
my-nginx 1/1 Running 0 4m5s

ishanshrestha@Ishans-MacBook-Air ~/development/learnkube/day3 % kubectl set image deployment/hello-app web=nginx:alpine
deployment.apps/hello-app image updated

ishanshrestha@Ishans-MacBook-Air ~/development/learnkube/day3 % kubectl rollout status deployment/hello-app
deployment "hello-app" successfully rolled out

ishanshrestha@Ishans-MacBook-Air ~/development/learnkube/day3 % kubectl get pods -o wide

NAME READY STATUS RESTARTS AGE IP NODE NOMINATED NODE READINESS GATES
hello-app-5f4b5f999f-6lntj 1/1 Running 0 62s 10.42.0.18 colima <none> <none>
hello-app-5f4b5f999f-h74lb 1/1 Running 0 58s 10.42.0.19 colima <none> <none>
hello-app-5f4b5f999f-pjn5b 1/1 Running 0 58s 10.42.0.20 colima <none> <none>
hello-app-5f4b5f999f-tgdj6 1/1 Running 0 62s 10.42.0.17 colima <none> <none>
hello-app-5f4b5f999f-vt75h 1/1 Running 0 62s 10.42.0.16 colima <none> <none>
hello-node-7b5bd4c5b4-kgscx 1/1 Running 0 23m 10.42.0.8 colima <none> <none>
hello-node-7b5bd4c5b4-wpgxz 1/1 Running 0 23m 10.42.0.7 colima <none> <none>
my-nginx 1/1 Running 0 5m23s 10.42.0.10 colima <none> <none>

ishanshrestha@Ishans-MacBook-Air ~/development/learnkube/day3 % kubectl rollout undo deployment/hello-app
deployment.apps/hello-app rolled back

ishanshrestha@Ishans-MacBook-Air ~/development/learnkube/day3 % kubectl port-forward service/hello-app-service 8080:80

Forwarding from 127.0.0.1:8080 -> 80
Forwarding from [::1]:8080 -> 80
Handling connection for 8080
Handling connection for 8080
E0727 13:45:17.749042 45369 portforward.go:424] "Unhandled Error" err="an error occurred forwarding 8080 -> 80: error forwarding port 80 to pod aa01a08861227e1835509035bf41918392c0639922c8e3a0f7938414a5dc0bbc, uid : container not running (aa01a08861227e1835509035bf41918392c0639922c8e3a0f7938414a5dc0bbc)"
E0727 13:45:17.749039 45369 portforward.go:424] "Unhandled Error" err="an error occurred forwarding 8080 -> 80: error forwarding port 80 to pod aa01a08861227e1835509035bf41918392c0639922c8e3a0f7938414a5dc0bbc, uid : container not running (aa01a08861227e1835509035bf41918392c0639922c8e3a0f7938414a5dc0bbc)"
error: lost connection to pod

ishanshrestha@Ishans-MacBook-Air ~/development/learnkube/day3 % kubectl get pods

NAME READY STATUS RESTARTS AGE
hello-app-57669678fc-2xrwd 1/1 Running 0 34s
hello-app-57669678fc-86hjc 1/1 Running 0 35s
hello-app-57669678fc-gjfmk 1/1 Running 0 30s
hello-app-57669678fc-pwcsc 1/1 Running 0 35s
hello-app-57669678fc-pzxsb 1/1 Running 0 30s
hello-node-7b5bd4c5b4-kgscx 1/1 Running 0 24m
hello-node-7b5bd4c5b4-wpgxz 1/1 Running 0 24m
my-nginx 1/1 Running 0 6m6s

ishanshrestha@Ishans-MacBook-Air ~/development/learnkube/day3 % kubectl port-forward service/hello-app-service 8080:80
Forwarding from 127.0.0.1:8080 -> 80
Forwarding from [::1]:8080 -> 80
Handling connection for 8080
Handling connection for 8080
