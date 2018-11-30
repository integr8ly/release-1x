# Manual Release Process - INTLY-7 test


The following components are needed to make up a integreatly release

- Component: Installer
    - **Location:** https://github.com/integr8ly/installation
    - **Role:** Setup and installation to run against an OpenShift cluster to install the required products and components
    - **Releasing:** 
        - create a release branch named `vx.x.x`
        - any bug fixes in the installer should be done against master and cherry picked to the release branch
        - once the release is complete, the last commit should be tagged with the release version and the branch deleted


- Component: Managed Service Broker
    - **Location:** https://github.com/integr8ly/managed-service-broker
    - **Role:** Open Service Broker API implementation that allows us to provision services in a different namespace than the one where the provisioned service
    was created. As much as possible, it will use CRs and operators to set up these services.
    - **Releasing:** 
        - tag the managed service repo against master with the version we want to release.
        - clone the repo and checkout the tag
        - run ```make build_and_push TAG=<release_version>```
        - update the version referenced from the integreatly installer against the release branch [https://github.com/integr8ly/installation]()
        - for each bug fix we will need to either update the tag or update the version retag and update the version referenced by the installer
        
        
- Component: Integreatly Web App
    - **Location:** https://github.com/integr8ly/tutorial-web-app
    - **Role:** Web Application that walks customers through the different types of integrations they can perform on the integreatly cluster
    - **Releasing:** 
        - follow the instructions here [https://github.com/integr8ly/tutorial-web-app#releasing]
        - update the version referenced in the integreatly installer release branch
        - for each bug fix we will need to either update the tag or update the version retag and update the version referenced by the installer      
