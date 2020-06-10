# Purchase Order import

## Import of business document scenario

In this scenario we parse a formal business document describing purchase order. The `BusinessDocParser` therefore belongs to the domain.

In this scenario we want to handle purchase orders of infinite (unlimited) size. Imported data structures are big and complex. Here we present a technique of direct access to the store without core tier mediation. 

We use `Validator` to perform basic validation on imported data structures.
    
![Import PO UseCase Sequence](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.githubusercontent.com/karbonfw/purchaseorderdoc/master/diagrams/import_po/import_po_business_parser.puml)

### Benefits
* We don't have to leak technical details such as reactivity or stream based API in order to achieve scalability.
* Plain CRUD functionality (import) is kept separate from business logic (in app).

### Downsides
* Business parser requires additional intermediate data model for parsed structure. This is a waste.

## Import using local parser

We can save some by giving up with business parser. Instead, we parse business document locally in the `app` tier. With this approach we can use JPA datamodel directly when parsing.

![Import PO UseCase Sequence](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.githubusercontent.com/karbonfw/purchaseorderdoc/master/diagrams/import_po/import_po_local_parser.puml)
