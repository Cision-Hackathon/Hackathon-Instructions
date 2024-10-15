# Hackathon Q4 2024: Effortless Edge! 💥
Here you'll find all the information needed to improvise, adapt and overcome.

## :calendar: Dates
- **Kick-Off**: Nov 4-6, 2024 (In your time zone)
- **Pitching/judging**: Nov 6th, 2024

## 📜 Rules of Engagement ##
1. You are free to do product ideation, user persona investigation/use cases, backlog creation, mockups of screens and diagrams of systems before the hackathon begins. These are great things to do with your team so everyone has a clear idea of what the hack will be about.
2. You can setup your infrastructure before the hackathon and get permissions to systems and services you may need. (This is highly suggested)
3. No writing of code before the hackathon. You can think, but no doing before the Monday bell rings and you come out fighting.

## :clipboard: How to Participate
1. **Team Up**: Form a team or go it on your own. (Create your teams in the signup link in #2)
2. **Sign up**: Sign up [here](https://forms.office.com/r/bejtfTpSwG)
3. **Pregame**: See below - do that **_BEFORE_** the hackathon 
4. **Hack**: Build something awesome.
5. **Present**: Show and tell on pitch day.

## 🕹️ Pregame
1. **Join Cision-Hackathon github**: If you can see this, then you are a member here in Cision-Hackathon. If you can't see this then raise your hand. I kid. If a member of your team can't see this then ask devops to add them to the Cision-Hackathon team. You will need their github user name.
2. **Look over sandbox-cision-001**: We are all sharing [sandbox-cision-001](https://console.cloud.google.com/home/dashboard?authuser=0&project=sandbox-cision-001) so you will need to get in there and make sure you have what you need turned on for your hackathon project. Please create a [GO](http://go.ticket.cision.com/) ticket for any missing features by ASAP so Devops has time to get it turned on for you.
3. **Think through your project** - who you are serving, how you will be serving them, how you will be delivering that value - _before_ the hackathon. You can even use the project features here in github to write them all down and create an ordered backlog for your team.
4. **Setup all of your infrastructure** - You want to ensure you have your GCP project, service account/permissions, GCP services and GKE kubernetes argo deploy all setup before kickoff. You don't want to be waiting for approvals just to get started or fumbling with foundational infrastructure. (If any of those terms sounded foreign, check out the FAQ below.)
   
## :question: FAQs

## DevOps related FAQs ##
### I need to create some infrastructure for my project. How do I do that? 
For each of these types of changes follow this procedure to help DevOps help you:
1. Create a PR with your changes in the repos described below and let the devops team know in the DevOps channel for your BU.
2. Provide them a link to your PR and explain what it is for.  

#### **Create your actual infrastructure**: ####
You can create infrastructure in GCP using the Terraform for Teams repository [here](https://github.com/Cision-DevOps/terraform-for-teams/tree/main/teams/gcp/dev). Create a folder with the name of your project in the dev folder. In there you can see examples of creating various types of infrastructure like PostGres databases, Redis, GCP storage etc... Search around and find things you need and add it to your folder. Use the [sandbox-cision-001](https://console.cloud.google.com/home/dashboard?authuser=0&project=sandbox-cision-001) project in those variables. Remember we are all sharing a single GCP project, so please be nice and don't delete anyone elses databases or other infrastructure.
* Create a namespace in GKE for your hackathon project that starts with "hack-" so they are easy to find
* Your SA needs to be associated with your namespace

#### **Create a service account for your project**: ####
Create your [service account](https://github.com/Cision-DevOps/gcp-infra-live/tree/main/terraform/service-acounts/app) for your project in **gcp-infra-live**. This will provide your application permissions in GCP and GKE. You will want to connect it to sandbox-cision-001, so you have access there.

## Service related FAQ ##

### **Pushing your services to GKE** ###
Once you have created the services you want to deploy to GKE (If that is where you are headed) you need to build a docker contanier and create the kubernetes deployment, service and ingress for it in [Kubernetes Argo Deploy](https://github.com/Cision-Hackathon/kubernetes-argo-deploy/tree/main/ccs-usa-gke). (If it is external to GKE) 
You can see examples of that in any of the folders, but this pattern is also followed in each of our github divisions, so if you have a use case that isn't shown there just look in the other divisions Github repositories. The basic overview though is:
* kustomization - Ties all of your files together
* Configmap - where you have configuration values you want to use in your deployment
* Deployment - The actual deployment where you start serving your docker images in pods in GKE
* ServiceAccount - Where you map the service account you created earlier to a named service account for your deployment
* Service/Ingress - Exposing your deployment
* A note on ingress - if you need to expose your ingress to people outside of the VPN you need an [external ingress](https://cision.atlassian.net/wiki/spaces/K8S/pages/25384681532/External+DNS+DNS+Self+Management)


Happy Hacking! :sparkles:
