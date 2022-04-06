---
title: "Welcome to Jekyll!"
date: 2019-04-18 15:34:30 -0400
categories:
  - blog
tags:
  - Processes
  - Jekyll
  - update
---

**Last Updated: 2022-04-01 10:45**

*[AOM]: Account Operations Manager
*[BAU]: Business As Usual
*[BB]: Billing Block
*[BoM]: Bill of Material
*[C&C]: Credit and Collection
*[CBN]: Customer Base Number
*[CM ]: Client Manager
*[CEP]: Contract Evaluation Package
*[CMO]: Contract Management Operations
*[CMS]: Customer Master Sheet
*[CoA]: Certificate of Acceptance
*[CO]: Change Order
*[COS]: Customer Operations Specialist
*[COSD]: Change Order Service Desk
*[CPA]: Country Participation Agreement
*[CSM]: Client Service Manager
*[CSSA]: Contract ID
*[DCC]: Device Control Centre
*[DOA]: Dead on Arrival
*[DOS]: Deal Output Sheet
*[dMPS]: Direct Managed Print Service
*[dTC]: Delivery Technical Consultant
*[EOL]: End of life
*[FIS]: Fleet Implementation Sheet
*[FOCA]: Front Office Contract Administrator
*[GSOW]: Global Statement of Work
*[GTC]: Global Trade Checklist
*[HP-ADM]: Hewlett Packard – Account Delivery Manager
*[HPAC]: HP Access Control
*[HP-GP]: Hewlett Packard – Global Procurement
*[HP-PM]: Hewlett Packard – Project Manager
*[HP-TC]: Hewlett Packard – Technical Consultant
*[H&S]: Health and Safety
*[HW]: Hardware
*[ICM]: Integrated Contract Management
*[LSOW]: Local Statement of Work
*[MAI]: Manage As Is
*[MIS]: Management Information System
*[MPS]: Managed Print Service
*[MS]: Managed Services
*[MSA]: Master Services Agreement
*[MSS]: Managed Supplies Service
*[NPS]: Non-Proliferation
*[OC]: Office Communicator
*[OPG]: Order Processing Guide Line
*[OA]: Order Acceptance
*[OAC]: Order Acceptance Checklist
*[OSA]: On-Site Administrator
*[PAT]: Portable Appliance Testing
*[PM]: Project or Programme Manager
*[P&L]: Profit and Loss
*[PN]: Product Number
*[PPS]: Personal Printing Systems
*[PPU]: Pay per Use
*[PO]: Purchase Order
*[POC]: Proof of Concept
*[RA]: Risk Assessment
*[RAMS]: Risk Assessment Method Statement
*[RM]: Remote Monitoring
*[RMA]: Remote Monitoring Appliance
*[RPL]: Restricted Parties List
*[RRC]: Revenue Recognition Checklist
*[RTM]: Route to Market
*[SAL]: Shipping Authorization Letter
*[SAID]: ???
*[SCID]: Sales contract ID
*[SDM]: Service Delivery Manager
*[SLA]: Service Level Agreement
*[SOW]: Statement of Work
*[SSOW]: Site Statement of Work
*[SC CO]: Supply Chain Customer Operations
*[SCOAH]: Supply Chain Operations and Analytics Hub (back office team)
*[SOTAT]: Sales Order Turn Around Time
*[SW]: Software
*[TAT]: Turn Around Time
*[T&C’s]: Terms & Conditions
*[TC]: Technical Consultant
*[TCV]: Total Contractual Value
*[TL]: Team Lead
*[TM]: Transition Manager
*[TPM]: Transition Project Manager
*[T&T]: Transition and Transformation
*[VAS]: Value Added Service
*[VAL]: Vendor Authorisation Letter
*[WO]: Work Order

# E2E dMPS Process

A dMPS project is broadly divided into following phases:
* [Pursuit Handover](#pursuit-handover)
* [Kickoff](#kickoff)
* [Planning](#planning)
* [Ordering](#ordering)
* [Deployment Preparation](#deployment-preparation)
* [Deployment](#deployment)
  - [Hardware Deployment](#hardware-deployment)
  - [Software Deployment](#software-deployment)
* [Lease Activation](#lease-activation)
* [BAU Handover](#bau-handover)

In addition there are sub processes that may get triggered from time to time:

* [Dead on Arrival Process](#doa-process)
* [Change Order Process](#change-order-process)
* [New Vendor Setup in Procure 360](#new-vendor-setup-in-procure-360)

These sub processes are referenced in main processes as well.

## Pursuit Handover

For any dMPS deal the very first step is with pursuit team to get a signed contract but before the deal is handed over to delivery there are certain steps that must be in place and T&T TM must ensure that these steps have been completed or an exception has been agreed and signed-off by Market T&T TL.

!!! tip Some Key topics for discussion during handover


    * Purchase Order (PO is now mandatory – unless email received from customer confirming a PO is not required for invoice to be paid) or, approval is obtained from T&T TL to proceed without a PO.  This should be obtained from Sales/Pursuit and provided to PM during Handover
    * 3rd parties
    * MIS solutions (BoM – to be bought or leased)
    * Confirm if Legacy devices are being removed
    * Hard disk wipe – for legacy devices
    * SLA of the project – check the value of the SAL covers the project (compared to DOS files)
    * Coterminous/non coterminous
    * Penalties
    * Maintenance kit support
    * Non standard HW ordering from HP partner
    * MAI devices
    * OSA’s
    * Check End of Support Life & EOL dates for the devices in scope
    * Case Exchange
    * RMC involvement, confirmed process outlined and how we are engaging with them
    * RMMC name is documented by the Pursuit Team

```plantuml!
@startuml
!theme cerulean
'_____________________
|T&T|
|PURSUIT|
start
partition Handover {
:SSOW signed-off<
:Complete H/W Design;
if (is Software in scope?) then (Yes)
:Engage pre-sales TC;
:Arrange for a demo device;
:Complete a High Level Design;
:Complete a POC;
:Complete a Low Level Design;
else (No)
endif
:Raise request for PM allocation;
Note #lightblue
* [[https://app.smartsheet.com/b/form/bf90a50ff5bf44a1818b29dc2da0cea4 Country PM Request Form]]
* [[https://app.smartsheet.com/b/form/58a1c69240ed46429215a829f5e09e33 Global PM Request Form]]
endNote
:Book a Handover meeting with allocated PM;
:Prepare Handover presentation;
Note #orange
* It is important that PO from customer
is available before the HO.
* If the PO is Not required, a Note from
the customer confirming this will be required.
* Make sure [[https://hp.sharepoint.com/:o:/r/sites/NorthernEurope2/Transition%20Managers/Handover%20Info.one?d=w20332c840217495fab3b26d58d410dbc&csf=1&web=1&e=sK2N9l One Note]] fields are all available.
endnote
:Provide Handover/
'_____PURSUIT TO T&T HANDOVER________
|T&T|
while (Is HO missing information?) is (Yes)
:Reject HO;
|PURSUIT|
:Amend / Update HO Presentation;
endwhile (No)
|T&T|
}
:Kickoff>
@enduml
```

!!! caution If software is in scope...
    Solutions are component parts of an MPS deal which are in addition to print devices.  They can include management tools such as WebJet Admin (WJA) and Digital Send Software (DSS) or pull print hard/software supplied by companies such as LRS, Papercut etc.  

    Deals which include a _Solution_ should:

    * Have a POC during the sales cycle to show the solution and how it may work in principal in the customer environment, typically a test environment.
    * Have a pilot either during the sales cycle or during transition to test and prove the actual solution design performs as expected in a live customer environment prior to full deployment across the estate.

## Kickoff

!!! tip Some topics to cover with the customer during kick-off:
    * Delivery Process
    * Delivery Access
    * Engineer clearance
    * H&S requirements including induction
    * Names/Vehicle Reg – required in advance
    * Escort required
    * RAMS required
    * Label Template
    * Supplies contact for each site/device

```plantuml!
@startuml
!theme cerulean
|T&T|
:Pursuit Handover<
'_____KICKOFF________
fork
partition "Internal Parallel Activities" {
:Remind Contract Admin (CA) that the dummy FIS
for the contract supplies has been created
especially if there are MAI (Manage As Is)
or Asset Transfer devices in scope;
:Raise request to get FOT Agent assigned - [[https://app.smartsheet.com/b/form/340b5532476e47b386e05b98aa732fd7 Link]];
:Raise request to get SDM assigned - [[https://hp.sharepoint.com/sites/SDMOpsRepository/Lists/SDM%20Allocation%20Request/AllItems.aspx Link]];
}
fork again
partition Kickoff {
:Prepare a high level plan using H/W design;
:Prepare Kick-off presentation;
:Arrange kick-off with customer;
:Make customer aware of the
site survey form;
if (Is Software in scope?) then (Yes)
:Establish timeframe for when relevant
server etc will be in place;
:Establish all information required by customer
to provide remote access to dTC;
:Provide the required information to customer;
:Request remote access to Customer network for dTC;
else (No)
endif
}
end fork
:Planning>
@enduml
```
## Planning

```plantuml!
@startuml
!theme cerulean
:Kickoff<
'_____DEPLOYMENT PLANNING________
partition Planning {
:Confirm deployment plan for sites;
:Confirm H/W requirements for initial sites;
:Provide the Site Survey form
for completion to customer;
if (IS Printer label in scope?) then (Yes)
	:Explain Printer Label template to customer
	and request confirmation on final design;
	else (No)
endif
}

:Create a change FIS file with
device and request information
such as IP Address,Hostname etc.
and request customer confirmation;

Note
This information should either be available on
Hardware design file or must be requested
directly from Customer.
endNote
:Receive completed site survey;
:Update Order forecast on
[[https://app.smartsheet.com/sheets/mxJx2Xw6WW7V2CwmcWHMG44qWmHFV8J5P4PpjwH1?view=grid Constraint Impact sheet]]
for each SKU;
:Ordering>
@enduml
```

## Ordering

### Hardware Ordering

Hardware ordering has a financial impact on HP and needs to be planned carefully to ensure HP is able to release the invoice and recognize revenue as quickly as possible, and minimize storage costs.

!!! tip
    This means some projects will require multiple hardware orders which reflect the detailed deployment schedule/device roll out.

    * ex.  A deployment of 1 site with 50 devices and no solution may take a week to deploy.  In this case one hardware order would be sufficient
    * ex.  A deployment of 5 large sites, with 250 devices per site and a pull print solution could take 15 weeks or more to deploy.  In this case at least 5 hardware orders should be considered.  Once all the devices on a hardware order are deployed and accepted by the customer, the invoice must be released, by requesting the removal of the Billing Block and HP can start to recognize the revenue.


```plantuml!
@startuml
!theme cerulean
!pragma useverticalif on
'_____H/W ORDERING________
:Planning<
partition Ordering {
fork
if (SOW?) then (Yes)
	if (Are requested devices on \nSOW and pricing files?) then (Yes)
		if (HP Direct?) then (Yes)
			:Place order using Order Tool
			Link to latest version
			of [[https://hp.sharepoint.com/teams/MPS_EMEA_HWOrder/Shared%20Documents/Forms/AllItems.aspx?viewid=bbbcfa87%2De645%2D4cea%2D9eeb%2D67641aed03b1 Order Tool and Training]];
		(No) elseif (Reseller?) then (Yes)
			:Place the order request
			with FOCA (Front Office Contract Admin);
		else (No)
		endif
	else (No)
	'_____CHANGE ORDER________
	:Trigger [[#change-order-process Change Order Process]]>
	detach
	endif
(No) elseif (CO) then (Yes)
:Place the order request
with CO Service desk.;
else (No)
endif
fork again
'_____S/W ORDERING________
if (Is Software in scope?) then (Yes)
:Engage dTC;
:Confirm with dTC the firmware
and other requirements for pre-staging;
	If (SOW?) then (Yes)
    :Check CEP file to make sure
    group email address (**nordicsmpslicenses@hp.com**)
    for license delivery has been provided.;
    :Place the order request with
		FOCA (Front Office Contract Admin);
	(No) elseif (CO?) then (Yes)
		:Place the order request
		with CO Service desk.;
	else (No)
	endif
else (No)
endif
endfork
'_____INSTALLATION PARTNER PO________
:Inform Installation partner of the
requirements for device install
and request quote;
Note #green
Confirm with dTC the firmware and other requirements for pre-staging;
If software is in scope ensure those requirements are included also included.
endNote
:Raise a PO request for the quote;

Note #orange
Complete the [[https://hp.sharepoint.com/teams/pps_mps_Ops_WF/Lists/MPS_Req/All%20Items%20%20New.aspx sharepoint form]]
endNote
If (Third Party Vendor on HP Systems?) then (yes)
else (no)
:Tigger [[#new-vendor-setup-in-procure-360 New Vendor Setup in Procure 360]] Process >
endif

:Update the Teams [[https://hp.sharepoint.com/:x:/r/teams/NWEPSS-POApproval/Shared%20Documents/General/PSS%20NWE%20PO%20PR%20Approval%20Requests%20FY22%20Template.xlsx?d=w2600f4af5582480ba0e481507eca4718&csf=1&web=1&e=2f0Umc PO Tracker]];
}
:Deployment Preparation>
@enduml
```

### Software Ordering

For solution orders the PM should reach out to the CA directly with the details on what needs to be ordered and the respective DS link with all the documentation. CA should raise a ticket and provide you a link to the ticket whete you can trace the progress of order placement and where eventually a tracking number will appear (if applicable).

So long as all the pricing and documentation is in place and correct, then the order should go through fine – in case of any issues work with the CA.

Solution hardware is tracked through SOS team – request an update from the SOS Team – ipg.solutions.sos@hp.com

Solution license keys requested - Request SOS Team & Global Procurement to cc PM when they provide the license keys from the Smartbuy PO to SP to the customer.

Technical meeting - review high throughput devices. Identify very high-volume devices which could run out of toner before they are active in remote monitoring - the factory cartridges are standard not the high yield, e.g. M4555 CE390A standard cartridge is 10K, CE390X is 24K. DO NOT order buffer stock as for BASE+CLICK contracts, any advance toners will be at HP's cost unless the customer agrees to pay through a Change Order.  You can place a buffer order if you are Level Pay, with approval.

Once the first solution is deployed you will receive a SAID number for the solution – this is required for placing break/fix requests for solution issues. This needs to be passed onto the SDM during handover to BAU.

## Deployment Preparation

```plantuml!
@startuml
!theme cerulean
:Ordering<
'_____TRACK ORDER ON SANDY________
partition "Deployment Preparation" {

while (Is order delivered?) is (No)
:Logon to [[https://oss.hpcloud.hp.com/os/landing Sandy]];
:check order status;
Note #green
Alternatively a report can be scheduled on
Sandy through Adhoc report to
get the information in an excel through
email at a desired frequency.
endNote
:Update Order forecast on
[[https://app.smartsheet.com/sheets/mxJx2Xw6WW7V2CwmcWHMG44qWmHFV8J5P4PpjwH1?view=grid Constraint Impact sheet]]
for each SKU;
endwhile (Yes)

:Update changeFIS file with Serial Numbers from Sandy;
:Provide the updated file to Installation Partner;

}
:Deployment>
@enduml
```
## Deployment

### Hardware Deployment

!!! note What exactly is Staging?
    **“Staging”** is the process of unpacking the printers, testing them and pre-configuring them prior to final delivery to the customer site.  Details of what is to be included in staging should be passed to the partner by the PM through the completion of an Installation and Delivery (I&D) Guide and Work Instructions. The assigned HP Technical Consultant (TC) should assist in defining the default device configuration to be applied to the devices with the customer.

    !!! Info
        Where there is a solution, staging by the installation partner is mandatory.


```plantuml!
@startuml
!theme cerulean
:Deployment Preparation<
'_____H/W DEPLOYMENT________
if (MAI or Asset Transfer?) then (yes)
partition "Manage As Is" {
    :Using design file, check provided Model
    and Serial Number are correctly
    mapped using [[http://east.austin.hp.com/tracking/ Serial Number Checker]];
    note #orange
    There have been instances where design
    file or information about model and Serial
    Number provided is incorrect and hence
    the pricing file is incorrect or missing pricing
    for a model that is in scope.
    endnote
    if (Mismatch or the model for
Serial Number is not on
pricing file?) then (yes)
      :Trigger [[#change-order-process Change Order Process]]>
    else (no)
    endif
:Update change FIS file with Serial Numbers;
}
else (no)
partition "Hardware Deployment" {
	'_____INCORRECT ORDER________

:Provide go ahead for
pre-staging using
updated ChangeFIS;
	'_____DEAD ON ARRIVAL________
if (Is Device found to be \nDOA during pre-staging?) then (Yes)
:Trigger [[#doa-process DOA Process]]>
Note
To trigger DOA process PM should
provide VAS team with following
information:
* Serial Number
* Order Number
* Device SKU
* Device Model
* Installation Partner Contact Info

As part of DOA process first B/F engineer
will assess and if that does Not work it
will be referred to ATS team.
endNote
else (No)
endif
:Confirmation from Installation Partner that
site contact has been established
and visit to site is confirmed;
:Plan a "Go/No-Go" per site with customer
and Installation partner;

while (Is the decision No-Go) is (Yes)
:Work with all parties
to remove bottlenecks;
endwhile (No)
'_____CERTIFICATE OF ACCEPTANCE________
:Receive confirmation from
Installation Partner that
rollout went as planned;
:Receive Certificate of acceptance
from Installation Partner.;
Note
Track Installation Partner PO
to completion on Teams link
endNote
}
while (Deployment is ongoing?) is (Yes)
:Update [[https://app.smartsheet.com/sheets/C65p37qHGmPx48xw9m4xWQVVMJMQ4f9Q2vhPXGm1?view=grid&filterId=1465527521568644 Project Tracking sheet]] weekly;
endwhile (No)
endif
:Lease Activation>
@enduml
```

### Software Deployment

```plantuml!
@startuml
!theme cerulean
:Deployment Preparation<
'_____SOFTWARE DEPLOYMENT________
partition "Software Deployment" {
If (Is Software in scope?) then (Yes)
:Confirm Server etc are in place;
:Confirm remote access for dTC is in place;
:Request dTC to initiate
software installation and configuration;
:Test software works as expected;
while (Issues with Software exist?) is (Yes)
:Work with all parties to remove bottlenecks;
endwhile (No)
else (No)
endif
}
:Lease Activation>
@enduml
```

## Lease Activation

!!! note What is Billing Block?
    Billing Block is a flag on ordering system which stops an invoice from being sent out to customer as soon as devices have been shipped.

    All hardware must be shipped with a _**billing block**_ that should not be removed until all devices on that order have been deployed.

    !!! tip If there are multiple hardware orders for any one customer, it is advisable to use the devices from one complete order before moving onto the next order where possible, in order to be able to release the hardware order for billing.

```plantuml!
@startuml
!theme cerulean
:Deployment<
'_____LEASE ACTIVATION________
partition "Lease Activation" {
:Submit Change FIS to FOT Team for DCC updates;

while (Is [[https://dcc.ext.hp.com/#/ DCC]] updated?) is (No)
:chase FOT Agent;
endwhile (Yes)

while (DCC has NRD devices?) is (Yes)
:Work with dTC and customer to resolve NRD;
endwhile (No)

:Email GACOM team for Billing Block Removal;

if (Any One-off COs raised?) then (yes)
:Trigger the one-off invoice by
raising a ticket with PPS MPS Operations
Management Workflow MPS Requests
- [[https://hp.sharepoint.com/teams/pps_mps_Ops_WF/Lists/MPS_Req/All%20Items%20%20New.aspx Link]];
note
MPS Service Required will be "Invoice Action"
endnote
else (no)
endif

if (Is there a Missing Info Ticket on Lease Activation?) then (Yes)
:Work with GACOM and other teams to resolve missing info;

floating Note
* Check with the iAOM if the SCID is raised with a Billing
Block – if Not, this needs correcting for future Change
Orders

* If the SCID (and hence the order) was booked initially
with a Billing Block, who released it, before we have
completed the deployment? – check with COS

* Correct invoices where there are No shipping costs – suggest
credit ALL invoices, then raise DEBIT NoTE (with Billing Block, including
ALL shipping costs) for the entire order (to be released in one go,
once ALL devices are deployed) – COS

* We must NOT raise an invoice/Debit for just shipping
costs (as we can not lease these in isolation).
endNote
else (No)
endif
}
:BAU Handover>
@enduml
```

## BAU Handover

```plantuml!
@startuml
!theme cerulean
:Lease Activation<
'_____BAU HANDOVER________
partition "BAU Handover" {
:Organise a BAU HO call with SDM and CSM;
:Complete HO;
note #green
* The SDM cannot reject the HO due
  to a missing first IBR/Invoice.

* It is not mandatory for either the
  PM or SDM to check the IBR, yet due
  to the current high volume of wrong
  IBR’s, it is desirable IBR to be checked.

* If the first IBR/Invoice is not handed
  over to SDM when HO is done, then the
  SDM will review it post HO when it is
  ready. In case an error is found during
  that review which relates to the deployment
  phase the SDM may refer back to the PM
  for assistance.

endnote
:Close the project;
}
stop
'_____________________
@enduml
```
# DOA Process

!!! note What is a DOA device?
    A DOA (dead on arrival) device is one that fails within 30 days of installation and cannot be repaired (devices are expected to have been installed within 90 days of ordering).

```plantuml!
@startuml
!theme cerulean
autonumber
participant "SDM / TM" as TM
participant VAS
participant "Breakfix Partner" as B
participant ATS
participant CSR


TM --> VAS: Log a case for a fault device installed within the last 30 days
VAS --> B: Log a case for repair
group Attempt Fix
	B --> VAS: If resolved, confirm device is fixed
	VAS --> TM: Close case and inform TM
	group Not Fixed
		B --> ATS: Elevates case to ATS for additional help
		ATS --> B: Provide support to try and resolve the issue
		group Fixed
			B --> VAS: If resolved, confirm device is fixed
			VAS --> TM: Close case and inform TM
		end
		B --> ATS: Provide logs and information
		hnote over ATS
		Make a decision if
		DOA authorisation must
		be requested.
		endnote
		group DOA Authorisation
			ATS --> B: Inform break fix partner case is Not solvable.
			B --> VAS: Inform VAS case can not be resolved – Close case.
			VAS --> TM: Inform case can not be resolved – Expect DOA Authorisation Form.
			hnote over ATS
			Raise to ATS management
			for DOA authorisation
			endnote
			== After the decision on DOA Authorisation is available ==

			group DOA Not Authorised or not requested
				ATS --> TM: Inform that DOA is not Authorised or not requested along with reason

				hnote over TM
				If cases can not be treated as DOA -
				for example device is working within Spec,
				but not how customer wants, SDM/TM will
				need to make a business decision on whether
				device is replaced at cost to account/country
				or if device stays on site.
				endnote

			end

			group DOA Authorised
				ATS --> TM: Send DOA Authorisation Form
				TM --> CSR: Email CSR the DOA authorisation form and request a replacement device
				CSR <--> TM: Validates information provided and processes DOA or requests additional clarification from SDM/TM
			end

		end
	end
end
@enduml
```
<!--
## DOA Process Swim Lane

```plantuml!
@startuml
!theme cerulean
|A| ADM / TM
start
:Log a case for a fault
device installed within
the last 30 days with VAS;
|V| VAS
:Logs case with Break fix partner for repair;
|BF| B/F Partner
:Attempts to fix device;
if (Fixed?) then (Yes)
	|BF|
	#Green:Inform VAS case is fixed/
	|V|
	#Green:Inform ADM/TM that
	case is fixed./
	|A|
  #Green:Close the case/
  stop
else (No)
  |BF|
	:Elevates case to ATS
	for additional help;
	|ATS|
	:Provide support to try
	and resolve the issue;
	:Raise to ATS management for
	DOA authorisation;
	:Inform break fix partner
	case is Not solvable.;
	|BF|
	:Inform VAS case can not
	be resolved – Close case.;
	|V|
	:Inform ADM/TM that case
	can not be fixed.;
	|ATS|
	If (DOA authorised?) then (No)
		|A|
  	 :If cases can not be treated as DOA -
		 for example device is working within
		 Spec, but not how customer wants,
		 ADM/TM will need to make a business
		 decision on whether device is replaced
		 at cost to account/country or if device
		 stays on site.;
		 stop
	else (Yes)
	  :Send DOA authorisation
	  form to ADM/TM;
	  |A|
	  :Email CSR the DOA authorisation
	  form and request a replacement
	  device;
	  |CSR|
	  :Validates information provided
	  and processes DOA or requests
	  additional clarification from
	  ADM/TM;
		stop
	endif
endif
@enduml
```
-->

# Change Order process

```plantuml!
@startuml
!theme cerulean
|Customer|
start
:Confirm the \nchange order \nis required;
:Email HP the \nchange order \nrequirements;

|HP PM|
if (CO is for third party) then (Yes)
	:Obtain quote
from third party;
	:Obtain deal
margin from
pursuit;
	:Apply deal margin on
the quote and
create a one off CO;  
else (No)
	:Submit CORF to
CO Service Desk;
	|CO Service Desk|
	:Provide the CO template;
	|HP PM|
	repeat :Verify the CO template \nis correct and has all \nrequired information \nfilled;
	|CO Service Desk|
	backward :Provide amended CO template;
	|HP PM|
	repeat while (CO template provided is incorrect) is (Yes) Not (No)
endif

|HP PM|
if (Order is for UK&I) then (Yes)
	if (is CSM / iCSM assigned?) then (Yes)
		if (Order is <50K) then (Yes)
			:Send CO for
  CSM/iCSM verification;
		else (No)
			:Send CO for CSM Lead
  verification and approval;
		endif
	else (No)
		:Send CO for CSM Lead
  verification and approval;
	endif
else (No)
	:Send CO for
country manager
sign-off;
endif
:Send CO for
Customer signature;

|Customer|
:Sign and return
the CO to HP;

|HP PM|
:File the CO on
dealsource;
stop
@enduml
```

# New Vendor Setup in Procure 360

While not regularly required, there are times when a deal includes service / component that is to be procured from a third party. If the third party is set-up on HP system it usually is fairly straight forward process to raise the order through Sharepoint Workflow.

However, if the vendor is not on HP system specifically for the country where the services are required, this will require setting up the vendor on HP system. At this point, PM will need to facilitate the following information on the vendor. Most of it should be on the quote from vendor but where missing it should be possible to request directly from vendor:


!!! note Please note it is mandatory to fill the below template to create the New vendor in Procure 360.
    ||Response|
    |--|--|
    |Supplier legal name:||
    |Address(Street):||
    |City:||
    |Postal Code:|
    |Country:||
    |State:||
    |Region:||
    |Email address:||
    |Phone:||
    |Supplier Contact First Name:||
    |Supplier Contact Last Name:||
    |Currency:||
    |Region and Country where services would be delivered:||
    |What will be the services/deliverables that the Supplier will provide?:||
    |Is this a non-US based supplier providing services within the US? :| Yes or No|
    |Is there a conflict of interest between you and/or the party you are requesting on behalf of, and the supplier?:| Yes or No|
    |Will this supplier provide products and/or services to the public sector?:|Yes or No|
    |Will the supplier have access to HP employee and/or HP customer personal data?: <br><code>Personal data is anything that can identify, locate, or be used to contact a person (customers and employees alike) or a person's device, by itself or combined with other information (but only if that combination is a reasonably non-complex effort).</code><br> [Training Link](https://hp.sharepoint.com/sites/PrivacyOfficeCommunications/SitePages/Training-Library.aspx)| Yes or No|
    |Will this supplier host, process, store or have access, in any manner, to HP data?:| Yes or No|
    |Will this supplier have HP Network access?:| Yes or No|
    |Will this supplier create HP software, applications, or websites or other HP products?:|Yes or No|
    |Will this supplier host HP applications, websites or systems?:| Yes or No|
    |Payment Terms :<br><code> For additional information about Payment Terms please use the this [link](https://hpi12.sharepoint.hp.com/teams/gbshub/pt1/finance_and_admin/nspta.html) and select correct options</code>  | <ol><li>	EOAP+45 or better </li><li>	Country Exception Payment Terms </li><li>	Lower than EOAP+ 45 or than the Payment Term Country Exception </li></ol>|
    |What will be the services/deliverables that the Supplier will provide? *||
    |Is it related to HP Indigo Business Unit? *|Yes or No|
    |Will the supplier have access to any physical US HP Site?: <br><code> HP's updated policy requires proof of COVID-19 vaccination as a condition of accessing any physical HP site in the US starting on November 1, 2021. This policy will apply to employees, contractors, contingent workers, visitors, partners, and customers. Anyone doing business on behalf of HP at partner and customer sites or attending an HP-approved external event in the US must also be fully vaccinated. A full copy of the policy is available at: Supplier Sustainability Requirements (hp.com)</code>  :|Yes or No|
