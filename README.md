# Purchase order doc
Purpose: document business domain of purchase order. The content of this repo is published as [https://karbonfw.github.io/purchaseorderdoc/](https://karbonfw.github.io/purchaseorderdoc/).

## Links
* [Domain description](domain.md)

## How to
### Markdown
Markdown is a simplified notation for creating documents in web format. Use [https://www.markdownguide.org/basic-syntax/](https://www.markdownguide.org/basic-syntax/) as guidance. Markdown documents should be placed in `md` files.

### Diagrams
Create diagrams in `puml` format using [https://plantuml.com](https://plantuml.com). Put files in `diagrams` folder. At any time you can embed diagram in your `md` documents using the following trick:

```markdown
![Dummy class diagram](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.githubusercontent.com/karbonfw/purchaseorderdoc/master/diagrams/dummy-class-diagram.puml)
```

Just replace the name of the `puml` file in the URL.
