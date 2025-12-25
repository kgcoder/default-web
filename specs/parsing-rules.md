# License Notice

This specification is part of the Default Web project and is licensed under 
**Creative Commons Attribution-NoDerivatives 4.0 International (CC BY-ND 4.0)**.

You are free to share, copy, and redistribute this specification in any medium or format, 
provided you give appropriate credit, provide a link to the license, and do **not** 
modify the content. 

For details, see: https://creativecommons.org/licenses/by-nd/4.0/

---

# Parsing Rules Specification (Draft)

**Status:** Early draft — subject to change

Parsing rules allow HDOC-aware clients to extract content and metadata from arbitrary web pages that **do not natively support HDOCs**. They ensure **deterministic parsing**, so that floating links and other connections behave consistently across different clients.

---

## 1. Overview

* **Purpose:** Convert a non-HDOC web page into a locally constructed HDOC.
* **Scope:** Used when connecting to pages on websites that do not provide HDOC versions. Parsing rules must be used when referencing regular HTML documents in **Connections** section of HDOC, CDOC or CONDOC, and in `<main>...</main>` tag of a CONDOC.
* **Key Principle:** Deterministic parsing—every client must extract the same text and metadata from a page using the same rules.

---

## 2. URL Format

Parsing rules are encoded in the page URL, after the `#pr=` fragment.

**Example:**

```
https://example.com/some-page#pr=c/body/t/.main-title/r/.page,.some-class/d/.date/a/.author
```

* The part after `#pr=` contains a **set of key–value pairs**, each specifying a selector.
* Only the **content selector (`c`)** is required. All other selectors are optional.

**Simplest form (only content required):**

```
https://example.com/some-page#pr=c/body
```

---

## 3. Supported Selectors

| Key | Purpose                   | Required | Notes                                                                                        |
| --- | ------------------------- | -------- | -------------------------------------------------------------------------------------------- |
| `c` | Content selector          | ✅        | CSS selector identifying the main content element.                                           |
| `t` | Title selector            | ❌        | Optional if `<h1>` exists and is unambiguous.                                                |
| `r` | Remove selectors          | ❌        | Comma-separated list of selectors for elements to remove. Each selector must be URL-encoded. |
| `d` | Publication date selector | ❌        | CSS selector for the date.                                                                   |
| `a` | Author name selector      | ❌        | CSS selector for the author.                                                                 |

* All selectors **must be URL-encoded**.
* Clients use `querySelector` for single-element selectors (`c`, `t`, `d`, `a`) and `querySelectorAll` for `r`.

---

## 4. Special Parsing Mode

```
#pr=text
```

* Treat the entire page as plain text.
* A line starting with `Title: ...` is used as the page title.

---

## 5. Creating Parsing Rules

### 5.1 Automatic Parsing (LZ Desktop)

* Uses a predefined list of selectors to extract content.
* Works ~50% of the time; fallback needed for manual rules if parsing fails.
* Ensures **deterministic extraction** for publishing visible connections.

### 5.2 Manual Parsing

1. Open the page in a browser (e.g., Chrome).
2. Inspect elements with Developer Tools.
3. Identify the main content container.
4. Select appropriate CSS selectors for content, title, date, author, and removal list.
5. Encode selectors and append to the URL as `#pr=...`.

* The **LZ Desktop Helper extension** can assist with encoding and testing.

---

## 6. Deterministic Parsing Principle

* All clients must parse a given URL **identically**.
* Differences in parsing may break floating links and prevent fixes.
* Parsing rules guarantee consistency, even for complex or heavily styled pages.
* Once configured, parsing rules can usually be reused across all pages of the same site.

---

## 7. Notes

* Parsing rules are primarily used **for publishing visible connections**.
* For personal reading, automatic text-density parsing may be sufficient.
* In the future, a **public database of parsing rules** may allow sharing rules for popular websites.
* HDOCs adoption will reduce the need for parsing rules over time.

