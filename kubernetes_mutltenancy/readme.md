# kubernetes multi-tenancy

Implementation of hard multi tenancy cluster is really challenging with the implementation of all aspects. we need to cover all the below aspects for this.

- Restricting the teams at namespace level
- With RBAC, limiting users and apps
-  Using Resource quota and limit ranges for controlling resources at namespace and pod level
- Implementing network policies
-  Having separate coredns for each and every team
- Controlling api requests at api server
- Implementing admission webhook controller using open policy agent(OPA)

## References
https://medium.com/itnext/multi-tenancy-in-kubernetes-332ff88d55d8