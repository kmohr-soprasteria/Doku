# Components of the TinyApplicationController

### RegistryOffice
All applications will automatically register at the RegistryOffice (RO).

**What is the purpose of RegistryOffice?**  
The RegistryOffice application is the entry point for all applications to get provisioned in the SDN application layer microservice architecture. It provides functionality to register and deregister an application from the MS environment. Its main purpose it to create accurate records of the registered applications and forward it to appropriate tiny application controllers for further formalities.  
It administrates the list of registered applications.

**Role in provisioning and deprovisioning an application to/from the ApplicationLayer**  
* The de-/registration services offered by the RegistryOffice (e.g. */v1/register-application*, */v1/deregister-application*) can be used by other applications to change their registration status. 
    * E.g. if a new application calls the register-application service, its application information is registered and related details are transported into the registry office. After successful registration the RO sends the registered application information to the TypeApprovalRegistry for type approval. 
    * On the other hand, a successful deregistration leads to the RO sending the deregistered application information to other applications that subscribed for the deregistration notification.  

* Other applications can use the RO notification services (e.g. */v1/notify-approval*) to subscribe for notifications about approval or registration status. If an applicationd has dependencies to other applications it needs to know if these applications services are available and can be used or not.

**Basic Services**  

|Service|Description|
|---|---|
|/v1/start-application-in-generic-representation | Starts application in generic representation|
|/v1/register-application | Adds the given application to the list of known applications|
|/v1/deregister-application | Removes the given application from the list of known applications|
|/v1/regard-updated-approval-status | Updates the approval status of an already registered application|
|/v1/list-applications | Provides a list of all registered applications|
|/v1/list-applications-in-generic-representation | The list of applications is provided in generic representation|
|/v1/inquire-application-type-approvals | Offers subscribing to notifications about new registrations|
|/v1/notify-deregistrations | Offers subscribing to notifications about withdrawn registrations|
|/v1/notify-approvals | Offers subscribing to notifications about new approvals|
|/v1/notify-withdrawn-approvals | Offers subscribing to notifications about withdrawn approvals|
|/v1/relay-server-replacement | Offers broadcasting of information about an updated serving application|
|/v1/relay-operation-update | Offers broadcasting of information about backward compatible operations|

![colorline_blue](https://user-images.githubusercontent.com/57349523/154715704-2e1a7c51-17c2-47af-a46a-85bd613f4a53.jpg)

### TypeApprovalRegister
The TypeApprovalRegister (TAR) stores already granted approvals.

**What is the purpose of TypeApprovalRegister?**  
When a new application wants to register at the RegistryOffice the RegistryOffice requests the of this application from the TypeApprovalRegistry. 
The actual approval is done by a human. After the human has decided about the approval, the related information is sent back to the RegistryOffice.  
The TypeApprovalRegister stores already granted approvals.

**What is the importance of documenting an approval status of an application by a Type approver?**
Only after the approval has been granted an application will be embedded into the MS environment and can be used by users and other applications. 
I.e. applications without approval are not (or no longer) available for usage. To ensure this functionality, the approvals have to be maintained 
in the type approval register.

|Service|Description|
|---|---|
| /v1/start-application-in-generic-representation | Starts application in generic representation |
| /v1/regard-application | Adds the application to the list of applications stored in the type approval register |
| /v1/disregard-application | Deletes the record of an application from the type approval register |
| /v1/document-approval-status | Creates or updates the approval status of an application |
| /v1/list-applications | Provides list of applications from the type approval register |
| /v1/list-approved-applications-in-generic-representation | Provides list of approved applications in generic representation |
| /v1/redirect-info-about-approval-status-changes | Offers subscribing to notifications about documentation of an approval status |



![colorline_blue](https://user-images.githubusercontent.com/57349523/154715704-2e1a7c51-17c2-47af-a46a-85bd613f4a53.jpg)

### ExecutionAndTraceLog
ExecutionAndTraceLog is logging all service activities

|Service|Description|
|---|---|

![colorline_blue](https://user-images.githubusercontent.com/57349523/154715704-2e1a7c51-17c2-47af-a46a-85bd613f4a53.jpg)

### OamLog
OamLog is logging all administrative activities


### AdministratorAdministration
AdministratorAdministration is authenticating OaM requests


|Service|Description|
|---|---|

![colorline_blue](https://user-images.githubusercontent.com/57349523/154715704-2e1a7c51-17c2-47af-a46a-85bd613f4a53.jpg)


### ApplicationLayerTopology
ApplicationLayerTopology represents interfaces and forwardings

|Service|Description|
|---|---|

![colorline_blue](https://user-images.githubusercontent.com/57349523/154715704-2e1a7c51-17c2-47af-a46a-85bd613f4a53.jpg)


### OperationKeyManagement
OperationKeyManagement keeps operation keys in synch

|Service|Description|
|---|---|


[<- Back to Specifying](../SpecifyingApplications/SpecifyingApplications.md) - - - [Up to Main](../Main.md) - - - [Ahead to ApplicationPattern ->](../ElementsApplicationPattern/ElementsApplicationPattern.md)
