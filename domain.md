# Purchase order - domain description

## Use Cases

![Usecases](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.githubusercontent.com/karbonfw/purchaseorderdoc/master/diagrams/usecases.puml)

### Import Purchase Order Use case

**Use case name:** *Purchase Order Import*  
**Use case description:** *Purchase Order which is sent by Customer system is imported by application.*

**Actors:** *Customer System*  

**Precondition:** *Customer must be configured in the application (other microservice)*

**Postcondition:** *After successful import all order lines are existing in the application as well as other services are informed about that.*


**Main scenario:**

	1. Message with PO (including OrderLines) is received
	2. Data is validated:
		2.1 Customer exists (another microservice has this configuration)
		2.2 Collaboration parties can be processed (Supplier only or Supplier and Factory)
		2.3 Create parties (Supplier/Factory) in other system
		2.4 All required attributes exist
		
	3. Check if PO exists already in the system
		(If doesn't exist)
		3.1a Create PO with Lines in the system
		3.2a Create addresses
		3.3a Create users (another microservice)
		3.4a Raise Order placed event (this information must be sent to other systems)
		
		(if exists)
		3.1b Update existing PO and Lines, create new lines (old are not removed, but can be cancelled)
		3.2b Calucalte differences in attributes
		3.3 Raise Order updated event (this information must be sent to other systems)
			
	4. Import of the PO must be logged (including possible errors) for further analysis
	

**Additional requirement:**
*Import of Purchase Order has to be logged in the system to allow tracking of all import and possible errors.*


**Alternative scenario:**

	1. Customer doesn't exists -> Import fails

![Import PO UseCase](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.githubusercontent.com/karbonfw/purchaseorderdoc/master/diagrams/importPO_UseCase.puml)

### Allocate Purchase OrderLine to Booking
**Use case name:** *Allocate Purchase OrderLine to Booking*  
**Use case description:** *If line is allocated to the Booking the message with such information comes. It includes deallocation as well*

**Actors:** *Supplier*
**Precondition:** *Order Line must exists*

**Postcondition:** *none*


**Main scenario:**  

	1. User chooses Purchase Order Lines to newly created booking and allocates quantity.
	2. System calculates outstanding quantity.


**Alternative scenario:**

	1. Purchase order is already cancelled -> Message with uncompleted information should be published.