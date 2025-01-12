# bicep-deployment-stack
## create/update/delete deployment stack through command line
Note: cd infra

1) Create a deployment stack

az stack group create ^
   --name demoStack ^
   --resource-group rg-raptor-dev ^
   --template-file ./main.bicep ^
   --action-on-unmanage detachAll ^
   --deny-settings-mode none

2) Verify the deployment

az stack group show ^
  --resource-group rg-raptor-dev ^
  --name demoStack

az stack group show ^
  --resource-group rg-raptor-dev ^
  --name demoStack ^
  --output json


3) Delete the deployment stack and related resources

az stack group delete ^
  --name demoStack ^
  --resource-group rg-raptor-dev ^
  --action-on-unmanage deleteAll

5) To delete the deployment stack, but retain the managed resources:

az stack group delete ^
  --name demoStack ^
  --resource-group rg-raptor-dev ^
  --action-on-unmanage detachAll
  
## Miscellaneous commands

1) To list available experimental features : 
   azd config list-alpha

2) To enable a specific experimental feature : 
   azd config set alpha.deployment.stacks on

3) To show current configurations : 
   azd config show
