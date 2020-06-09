# Purchase Order import

## Import of business document scenario

In this scenario we parse a formal business document describing purchase order. The `BusinessDocParser` therefore belongs to the domain.

In this scenario we want to handle purchase orders of infinite (unlimited) size. Imported data structures are big and complex. Here we present a technique of direct access to the store without core tier mediation. 

We use `Validator` to perform basic validation on imported data structures.
    
![Import PO UseCase Sequence](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.githubusercontent.com/karbonfw/purchaseorderdoc/master/diagrams/import_po/import_po_business_parser.puml)
