# Openshift introduction 

- Redhat opensource container platform
- Developing and hosting enterprise applications
- openshift is Redhat PAAS
- openshift takes care of managing underlying infrastructure
- openshift is having 4 flavours 

# Terminology
Project ---> namespace 
Machinepool

# Rosa commands 
rosa list machinepool -c mkto-poc-mct3

## Set max-replicas
## If your cluster is spread across 3 AZs, it will be good to provide max-replicas that is a multiple of 3
## DO NOT provide a very high number for max-replicas, since scaling down is not that easy
rosa edit machinepool --cluster=mkto-poc-mct3 Default --enable-autoscaling --min-replicas=3 --max-replicas=12


# Openshift flavours 

openshift origin (opensource)
    - Based on top of docker containers and kubernetes cluster manager with added developer and operational centric tools that enable rapid application development, deployment and life cycle management.
    - Docker, kubernetes and Tools(scm, pipeline, registry, software defined networking, API centric, Governance)
openshift online Application development and hosting service)
openshift dedicated(Managed private clusters on AWS/Azure/Google clouds)
openshift enterprise

# openshift architectural overview 

Components:
    - Openshift container registry
        Containers, images, deployments, services 
    - Openshift webconsole (with openshift authentication and authorization)
    - Openshift CI/CD 
      Built in integration with SCM 
    - etcd

# Openshift setup 
    - how to setup minishift?
    - All In one | SingleMaster, Multiple Nodes | Multiple master and nodes
    - All in one solution with minishift 

# Openshift management with webconsole and CLI 
    - How to interact with openshift? webconsole/ CLI / REST API 
    - webconsole port number is 8443, home page displays service catalog
    - CLI (oc tool)

## oc commands
* oc login <https://mycluster.mycompany.com>
* oc login -u developer -p developer 
* oc logout 
* oc whoami -t (generate bearer token)
* oc get projects 
* oc get users 
* oc get pods -o wide --field-selector spec.nodeName=ip-10-158-232-234.us-west-2.compute.internal
* oc adm drain <node_name> --ignore-daemonsets=true
* oc delete node <node_name>



## REST API commands 
> curl https://localhost:8443/oapi/v1/users \
    -H "Authorization: Bearer <TOKEN>"

## Management interfaces object 
    - openshift project equals to namespace

# Openshift concepts - projects 
    - Users (Regular developer/ system admin / service accounts)
    - Internally uses oAuth Server (Allow all/ Deny all) (/etc/openshift/master/master-config.yaml)

# Build and deploy - Concepts 
    - Application deployment
    - build strategies

# Redhat on cloud 
    - ARO (Redhat openshit on Azure)
    - ROSA (Redhat openshift on AWS)


