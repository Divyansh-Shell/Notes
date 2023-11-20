___
Asset Integrity Project, replace a 20+ years old stand alone application that no longer work at 64 bits PC/. The application is currently used mostly in the US market. Shell Technical Advisor (TA) uses the application to collect customer plants data; then, install the application at customer’s sites to be used as a daily equipment maintenance tool.

The system will bring the following benefits for the customers.

• Provides an output for customer value documentation such as, man hours saved, or defects rectified.

• Strengthens vendor / customer relationship with increased knowledge of customers and their lubrication program.

• Identify x-sell / up-sell opportunities

• Reduced customer churn / improved share of wallet

• Data mining / analytics

```
The service processes: Shell Technical Advisors (TA) walk the plant accompany by plant personnel to collect detail equipment information using Lube Planner iPad App. Then, the TA presents the data collection to the plant supervisor and work with him/her to ensure the data collected accuracy. They use the Data Manipulation features to update the data. Both TA and customer can create Routes. Customer’s technician will use the Routes Worksheet to perform their daily equipment maintenance routine.
```

Maintains its own data store PostgreSQL containing the Shell Product Information  not connected to Shell Lubricant Product DB 

TA--> Technical Advisor 
FP --> Focal Point 
GPC --> Global Product Catalogue 

The  business FP will be responsible for entering new Products and Update the Product in the system Manually 
Shell TA FP is responsible for updating the Lube Planner Database --> Manual Activity 
Shell TA can add new/non-Shell Product into the system (Lube Planner) using the iPad App developed during the MVP-1 phase of the application – manual activity

Devlopment -> Geopolitical Entity 
Discipline Engineering -> Equipment, Maintenance Plan  
Commercial -> Product 
Real Estate -> Site                                                                                                                                                                                       
Human Resources -> Employee Intereaction  

TA COMMENT ARE FOR A SITE BELONGS TO INDUSTRY HAVING (INDUSTRY_ID), LOCATED IN COUNTRY HAVING (COUNTRY_ID), HAVING THE LUBRICANT WITH LUBRICANT_ID USED FOR THE COMPONENT HAVING THE COMPONENT_ID,  HAVE INSTALLED EQUIPMENT(EQUIPMENT_ID ) INSPECTION COMMENDS BY TA FOR EQUIPMENT(COMMENT AND EQUIPMENT TABLE ) HAVING THE COMPONENTS WITH COMPONENT_ID WHICH IS RELATED TO THE SITE HAVING THE SITE_ID WHICH HAVE SURVEY PERFORMED HAVING THE SURVEY_ID WHICH WAS PERFORMED FOR A DURATIONAS DETAILED IN INTERVAL WITH INTERVAL_ID DONE BY THE OWNER HAVING THE USER_ID FROM USERS PERFORMED FOR AREA WITH AREA_ID THAT HAS THE SITE HAVING SITE_ID 

```
Shell LubePlanner is a software that allows a Shell employee to make lubrication and maintenance recommendations for industrial equipment at customer facilities. A customer can log into the web portal to view and edit the maintenance recommendations and to schedule routes to perform those maintenance tasks. Shell LubePlanner consists both iOS native and web components, for customers and Shell employees.
```

```
· MVP 1 – Develop an native iOS (iPAD) App for TA to use for Data Collection.

· MVP 2 – Develop a web-based App for TAs and Customers to perform mass Data Manipulation (i.e. Mass move and copy of data).
. MVP 3 – Develop Routing and Scheduling features as part of the web-based tool for customers to use for daily equipment maintenance routine
```


#Authentication_System 

Shell External Users --> Janrain/CIPM
Shell Internal Users --> SIMAAS/PINGID


IOS APP 


![[Pasted image 20231115144336.png]]

```
French Fries built on Swift -> interreacts with FF data source -> Uses the Azure Active Directory (ADD ->for the authentication and authorization services User Authentication and SSO and Application integration identity protection and MFA Role based authentication )

RETURNS THE TOKEN FROM THE AAD --> INTEREACTS WITH THE FIREBASE API USING THE REST FRAMEWORK INTEREACTS WITH THE BLOB STORAGE --> gRPC --> gRPC Server which intereacts with the FF data store(postgres) --> azure managed database 

Frameworks 
	UI KIT FRAMEWORK 
	SWIFTUI FRAMEWORK 
	COMBINE FRAMEWORK 

FIREBASE CRASHLYTICS FOR THE LOGS AND CRASHES 

SQLITE DATABASE USED FOR THE CACHE 
OFFLINE CAPABILTY SUPPORTED BY SQLITE 
CONFIDENTIAL DATA ALL PROTECTED BY APPLE DATA PROTECTION 
APP --> SAVES THE TOKENS FROM PING ID --> DEVICE KEYCHAIN 
ONLY SHELL EMPLOYEE WILL USE THE APP SO --> SSO WITH PING ID 
```


![[Pasted image 20231115145328.png]]

BACKEND SERVICES -> GOLANG 
	LubePlanner Backend APIs --> (french-fries -be - apis ): Backend Endpoints to the frontend client for consume 
	LubePlanner DB service --> (french-fries - dbservice): Access to the LubePlanner DB provides the site and reference data to the application

https/SSL for the secure API along with the authentication token 
Agile hub App center deploys the LubePlanner app in UAT and DEV env taken care by MADF 


```
Following section sketches the migration process planned. ***

a.     Customers who are ready to migrate to new version of the app will share their data as .mdf (MS Access) file

b.     This mdf file won’t contain any PII or CSI information

c.     They will share these files by sending unencrypted email to TA/PO

d.     TA/PO will store those files in Most Confidential SharePoint site having only business access

e.     TA/PO will use older version (32 bit) of Lube Planner application and extract the above .mdf data as flat file

f.      TA/PO will upload the flat/Excel file in the iOS App using some import feature of the app

g.     PO will extract the Shell lubricant product information from GPC***and manually upload it to the database, using similar import feature.

h.     PO will get the information for the 3rd party products by email and manually upload into LubePlannerdatabase using Application feature.

i.      PO will get the product update information by email and manually update it Lube Planner, but there is no fixed reconciliation period defined.
```

**Recipe – Technology Stack**|**React, Go, PostgreSQL, gRPC, iOS (native), React web frontend, Microservices backend**|**React, Go, PostgreSQL, gRPC, iOS (native), React web frontend, Microservices backend**

Microservices developed with
o    Go
o    PostgreSQL
o    gRPC
o    React


Three different Environments --> Development, Staging, Production 


Lube Analyst --> Full Priority 

