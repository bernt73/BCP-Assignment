# BCP-Assignment
This repo is created to host the helm charts for the BC Platforms assignment

---
## This is developed to host the helm charts for the BC Platforms - Technical Specialist assignment.

### 1. Deployment of a simple web application on K3S using Helm

- I will be using a common Drupal web application and using Bitnami's Helm chart for it


### 2. Deployment of Keycloak in the same Helm chart

- I will be adding Keycloak into the helm chart as a subchart to handle the dependencies in a separate branch

---

### Pre-requisites

1. K3S
2. kubectl
3. Helm (and Bitnami’s repo has been added to Helm - if not, just run

   `helm repo add bitnami https://charts.bitnami.com/bitnami`)

*This has been tested on* :
- k3s v1.27.6
- kubectl v1.28.3
- helm v3.13.1


### 1. Instructions to run 

`helm install bc-drupal -f ./drupal/values.yaml ./drupal/`

Wait for a few minutes for the containers and services to be created.


### 2. To access the web interfaces, do either:

i. Port forward to the respective services by issuing the following commands:

- Ensure that your ports 9090 and 9092 are free.

- `kubectl port-forward -n default svc/bc-drupal 9092:82 &`
- `kubectl port-forward -n default svc/bc-drupal-keycloak 9090:80 &`

ii. Hit the web interfaces directly via their internal IP addresses (for troubleshooting purposes):

- Get the respective endpoints for **bc-drupal** and **bc-drupal-keycloak** using :

   `kubectl get endpoints` 
   
   and paste in the browser. 
- It should look something like [*ip-address*]:8080  


### 3. To remove the cluster

`helm delete bc-drupal`


---


### To-do list

1. Create the user accounts in Keycloak and Drupal respectively
2. Integrate Keycloak user authentication with Drupal (can follow the [link](https://www.drupal.org/docs/contributed-modules/drupal-oauth-openid-connect-login-oauth2-client-sso-login/keycloak-single-sign-on-login-using-drupal-as-oauth-client) here)
3. 
