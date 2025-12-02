# License Notice

This specification is part of the Default Web project and is licensed under 
**Creative Commons Attribution-NoDerivatives 4.0 International (CC BY-ND 4.0)**.

You are free to share, copy, and redistribute this specification in any medium or format, 
provided you give appropriate credit, provide a link to the license, and do **not** 
modify the content. 

For details, see: https://creativecommons.org/licenses/by-nd/4.0/

---

# CONDOC Specification (Draft)

**Status:** Early draft — subject to change
**Document Type:** CONDOC (Connectioins Document)


A **CONDOC** is a document that contains **no primary content of its own**.
Its purpose is to *augment an external document* by providing:

* a reference to the document being enhanced, and
* a set of outbound connections to additional documents, optionally with floating links.

CONDOCs allow users to add connections **without modifying the original source document**.

---

## 1. Structure Overview

A CONDOC has the following structure:

```xml
<condoc>
  <title>…</title>            <!-- optional -->
  <description>…</description> <!-- optional -->
  <main>…</main>              <!-- required -->
  <connections>…</connections> <!-- optional -->
</condoc>
```

Only `<main>` is required.

---

# 2. Elements

## 2.1 `<title>` (optional)

A human-readable title describing the CONDOC in plain text. HTML is not allowed.
This title is for display only and does not affect functionality. 

Example:

```xml
<title>Famous Men of the Middle Ages</title>
```

---

## 2.2 `<description>` (optional)

A brief explanation of what the CONDOC does, why it exists, or what enhancements it contains. Can contain plain text only. HTML is not allowed.

Example:

```xml
<description>
The Project Gutenberg eBook with table of contents added as a separate document.
</description>
```

---

## 2.3 `<main>` (required)

The URL of the **primary document** that this CONDOC enhances.

The referenced document may be:

* an **HDOC**
* a **CDOC**
* a **standard HTML page**

### Special Case: HTML Documents

When the `<main>` element points to an HTML document, the URL **must** include parsing rules so that clients know:

* how to extract the document’s title
* how to extract the document’s text content
* how to locate individual characters for floating links

Example (with parsing rules embedded in the URL):

```xml
<main>
https://example.com/page.html#pr=c/body/r/.page
</main>
```

---

## 2.4 `<connections>` (optional)

The `<connections>` section contains:

* a list of referenced documents
* optional floating links connecting the main document to those documents

### Format

The structure of `<connections>` is **identical to the shared Connections Specification** used by:

* HDOC
* CDOC
* CONDOC

Each `<doc>` element may contain zero or more floating links.

Example:

```xml
<connections>
  <doc
      url="https://example.com/extra.hdoc"
      title="Additional Material"
      hash="1a2b3c">
      i:25422;l:19;h:60e455;e:QUg=_i:5;l:19;h:3c1f60;e:QWg=
  </doc>
</connections>
```

---

# 3. Example CONDOC

```xml
<condoc>

  <title>Famous Men of the Middle Ages</title>

  <description>
    The Project Gutenberg eBook with table of contents added as a separate document
  </description>

  <main>
    https://www.gutenberg.org/cache/epub/3725/pg3725-images.html#pr=c/body/r/.page
  </main>

  <connections>
    <doc
        url="https://reinventingtheweb.com/examples/famous-men/table-of-contents.hdoc"
        title="Table of contents of the Project Gutenberg eBook &quot;Famous Men of the Middle Ages&quot;"
        hash="1f25bd">

        i:25422;l:19;h:60e455;e:QUg=_i:5;l:19;h:3c1f60;e:QWg=
        i:33104;l:14;h:df0913;e:QU4=_i:43;l:14;h:457c77;e:QW4=
        …
    </doc>
  </connections>

</condoc>
```