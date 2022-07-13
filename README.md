# customer-proc-api
 
Design & Solution:
#RAML
contains a single resource, customer, and allows the following:
•	List customers
•	Create a new customer
•	Update a customer
•	Deletes a customer

#Periodic Sync
The scheduler is used to periodically make pull requests to the data store in order to retrieve only the records that were modified since the last request. Salesforce CRM is queried for contacts that were recently modified and just prints them in the console.

#Retrieval and Update of customers details
*After creating new project followed below path to generate flows through RAML:
customer-proc-api -> Manage Dependencies -> Manage APIs -> Add new dependency from exchange -> select RAML -> Apply -> Scaffold api -> Apply and Close
*This approach helps to import any changes which is being published to exchange with respect to API.
*GET Method - Specifies generic flow to retrieve any object specified in getCustomer.json. Here in this usecase, contact object is used. However, any number of objects can be added in getCustomer.json and same code can be resued to fetch records.
*PUT Method - Above get call is resued to retrieve data and contact specific information received in request will be updated in Salesforce on the basis of requestId received in query parameter.
*POST Method- Contact specific information received in request will be created in Salesforce on the basis of requestId received in query parameter.
*DELETE Method - In order to delete any Id, firstly checked if that Id exists or not. Accordingly, generic flow is created to delete any object specified in deleteCustomer.json. Here in this usecase, contact object is used. However, any number of objects can be added in deleteCustomer.json and same code can be resued to delete records. If Ids are less or equal to 200, then they can be deleted using DELETE component directly. However, if large amount of Ids to be deleted then create job bulk api v2 is used to delete data in bulk.

RAML:
customer-proc-api
UserName- Poojaiqvia
Password- Iqvia@1234
