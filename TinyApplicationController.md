# Components of the TinyApplicationController

### RegistryOffice
All applications will automatically register at the RegistryOffice (RO).

**What is the purpose of RegistryOffice?**  
The Registry office application is the entry point for all applications to get provisioned in the SDN application layer microservice architecture. It provides functionality to register and deregister an application from the MS environment. Its main purpose it to create accurate records of the registered applications and forward it to appropriate tiny application controllers for further formalities.  
It administrates the list of registered applications.

**Role in provisioning and deprovisioning an application to/from the ApplicationLayer**  
The de-/registration services offered by the RegistryOffice (e.g. /v1/register-application, /v1/deregister-application) can be used by other applications to change their registration status. 
* E.g. if a new application calls the register-application service, its application information is registered and related details are transported into the registry office. After successful registration the RO sends the registered application information to the TypeApprovalRegistry for type approval. 
* the other hand, a successful deregistration leads to the RO sending the deregistered application information to other applications that subscribed for the deregistration notification.  

Other applications can use the RO notification services (e.g. /v1/notify-approval, /v1/notify-withdrawn-approvals, /v1/notify-deregistrations) to subscribe for notifications about approval or registration status. If an applicationd has dependencies to other applications it needs to know if these applications services are available and can be used or not.

![colorline_blue](https://user-images.githubusercontent.com/57349523/154715704-2e1a7c51-17c2-47af-a46a-85bd613f4a53.jpg)

### TypeApprovalRegister
The TypeApprovalRegister stores already granted approvals

![colorline_blue](https://user-images.githubusercontent.com/57349523/154715704-2e1a7c51-17c2-47af-a46a-85bd613f4a53.jpg)

### ExecutionAndTraceLog
ExecutionAndTraceLog is logging all service activities

![colorline_blue](https://user-images.githubusercontent.com/57349523/154715704-2e1a7c51-17c2-47af-a46a-85bd613f4a53.jpg)

### OamLog
OamLog is logging all administrative activities

![colorline_blue](https://user-images.githubusercontent.com/57349523/154715704-2e1a7c51-17c2-47af-a46a-85bd613f4a53.jpg)

### AdministratorAdministration
AdministratorAdministration is authenticating OaM requests

![colorline_blue](https://user-images.githubusercontent.com/57349523/154715704-2e1a7c51-17c2-47af-a46a-85bd613f4a53.jpg)

### ApplicationLayerTopology
ApplicationLayerTopology represents interfaces and forwardings

![colorline_blue](https://user-images.githubusercontent.com/57349523/154715704-2e1a7c51-17c2-47af-a46a-85bd613f4a53.jpg)

### OperationKeyManagement
OperationKeyManagement keeps operation keys in synch

[<- Back to Specifying](../SpecifyingApplications/SpecifyingApplications.md) - - - [Up to Main](../Main.md) - - - [Ahead to ApplicationPattern ->](../ElementsApplicationPattern/ElementsApplicationPattern.md)