# Default Web Specifications

This repository contains early drafts, proposals, and evolving specifications for the Default Web — an alternative, document-centric branch of the Web built around stable static data types and visible connections between documents.

---

## Vision

This project is inspired by Ted Nelson’s vision of hypertext, ideas that the modern Web never implemented. Early design choices in the 1990s mixed content, presentation, and behavior (HTML + CSS + JavaScript), turning pages into isolated containers and making something as basic as visible connections between documents practically impossible.

The Default Web aims to finally introduce true hypertext into the Web ecosystem.

It defines a set of static document types (HDOC, Embedded HDOC, CDOC, CONDOC, etc.) that:

- don’t support scripts,
- render the same everywhere,
- enable visible connections,
- are self-contained and have no dependencies beyond images and iframes.

These documents form a parallel ecosystem — living alongside today’s HTML pages, and in the case of Embedded HDOCs, even inside them. Most web pages (blog posts, docs, articles) don’t need custom design or complex interactivity; a stable default format works better. Over time, standalone HDOCs can replace a large portion of the Web.

HTML with CSS and JavaScript remains the right tool for special cases:
- landing pages with heavy design or animation,
- complex applications like social networks, marketplaces, or stores.

But for simple content pages, there should be a default data format. That’s where the name “Default Web” comes from. Over time I used other names too:
- Static Web — because the formats are static,
- Web 1.1 — a continuation of the old static Web,
- Standard Web — because documents look the same across sites,
- Readers’ Web — because readers, not authors, control appearance through themes and clients.

All these names describe different angles of the same idea.

We start with visible connections. As the ecosystem matures, we’ll explore more of Ted Nelson’s concepts: transclusions, richer link types, links with multiple ends, bidirectional links, versioning, micropayments, and more complex relationship graphs (beyond simple one-to-many connections between documents).

Some of these ideas require centralized services. This project’s job is to demonstrate technical feasibility, define the data formats, and build the frontend layer so that when those services appear, they can plug directly into an existing ecosystem.

---

## Default Web Document Types

The following formats are under development:

### **HDOC** — Hypertext Document  
A static, portable, minimally styled text document format.  
Can contain HTML or plain text conent and visible connections to other web pages.

### **Embedded HDOC**  
A version of HDOC embedded inside existing HTML pages.  
Allows websites to participate in the Default Web without having to serve a standalone HDOC from an endpoint different from the URL of the original original HTML page.

### **CDOC** — Collage Document  
A document format for 2D collages. It is based on SVG format and can contain visible connections to any number of other documents.

### **CONDOC** — Connections Document  
A container type that can reference the main document (HDOC, CDOC, or a regular web page with parsing rules), and use visible connections to connect it to any number of other documents.

### ***Static comments*** - A JSON array used in the Comments section of an HDOC 
HDOCs can include comments stored as a JSON array (inspired by the WordPress comments format, but with small modifications like visible connections to the host page and multiple ID types).

For a full description, see: specs/static-comments.md.

---

### *(Future formats may be added here.)*

Full draft specifications for each format will be placed in the `specs/` directory.

---

## Parsing Rules

Clients can create HDOCs from ordinary HTML pages using deterministic parsing rules. These rules ensure all clients display the same content and avoid broken links.

For full details, syntax, and examples, see: `specs/parsing-rules.md`.

---


## Repository Structure

/
README.md
GOVERNANCE.md
/specs
hdoc.md
embedded-hdoc.md
cdoc.md
condoc.md
static-comments.md
parsing-rules.md
...
/drafts
design-notes.md
examples/

- **specs/** — finalized or semi-finalized specs (once they exist).  
- **drafts/** — rough notes, sketches, early proposals.

You may start with drafts and promote them to `/specs` when they stabilize.

---

## Contributing

Contributions are welcome in the form of:

- Proposals for syntax or semantics
- Drafts improving document type definitions
- Examples and interoperability tests
- Discussions in issues and pull requests

See **GOVERNANCE.md** for details on roles and decision-making.

---

## Licensing

This repository contains two categories of content with separate licenses:

1. **Source code (tools, examples, scripts)**  
   Licensed under a permissive open-source license (MIT).  
   See `LICENSE-CODE.md`.

2. **Specification documents (HDOC, Embedded HDOC, CDOC, CONDOC, Parsing Rules, Connections, Static Comments, etc.)**  
   Licensed under **Creative Commons Attribution-NoDerivatives 4.0 (CC BY-ND 4.0)**.  
   These specifications define document formats and related standards for the Default Web project and are **not to be modified**. 
   See `LICENSE-SPECS.md`.

Unless otherwise noted, each file clearly indicates which license applies.

---

## Status

The Default Web specifications are **early drafts**.  
Expect rapid changes as the formats evolve and the ecosystem grows.


## Reference Implementations

The following software projects demonstrate early support for Default Web formats.
They are not required for implementing or using the specifications.

- [Visible Connections](https://chromewebstore.google.com/detail/visible-connections/hlckcdbgknflkkciojgdbhomdnegimbm) (Chrome extension) — adds support for new data formats and visible-connection rendering inside the browser.

- [Static Web Publisher](https://wordpress.org/plugins/static-web-publisher/) (WordPress plugin) — automatically embeds an Embedded HDOC version of each page.

- [LZ Desktop](https://reinventingtheweb.com/lzdesktop/) (desktop viewer/editor) — standalone app for browsing Default Web content and creating new documents with visible connections.

More tools will be added as the ecosystem evolves.

---

## Official Website

More information about the Default Web project, ecosystem updates, and guides can be found at:

**https://reinventingtheweb.com/**