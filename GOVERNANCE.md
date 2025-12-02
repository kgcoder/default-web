# Default Web Governance Model

This document defines how the Default Web project is guided, how decisions are made, and how stewardship of the specifications works — both now and in the future.

---

## 1. Purpose

The purpose of governance is to ensure that the Default Web specifications:
- maintain long-term stability,
- evolve according to community needs,
- remain open, transparent, and forkable,
- avoid centralization in any single company or private interest.

---

## 2. Roles

### **Project Steward (Temporary Role)**
The initial originator of the project (Karen Grigorian) acts as the temporary steward:
- Maintains the roadmap.
- Reviews and merges contributions.
- Has final say on decisions while the ecosystem is still forming.
- Can delegate tasks to collaborators.

### **Contributors**
Anyone who opens issues, writes proposals, or submits pull requests.

### **Trusted Collaborators**
Contributors who have demonstrated consistent, high-quality involvement.  
They may:
- Merge non-controversial PRs.
- Maintain specific specification files.
- Lead sub-projects.

These individuals may be named in future revisions of this governance document.

---

## 3. Decision Making

### **Consensus First**
The project aims for consensus through discussion.

### **Steward Override**
If consensus cannot be reached, the Project Steward may make the final decision.

### **Evolving Authority**
Over time, authority may shift:

- The Steward may designate Trusted Collaborators who can act as co-maintainers.
- Future versions of this document may transfer final authority from the Steward to a governing group or broader community model.

---

## 4. Long-Term Ownership and Continuity

The Default Web specifications should outlive any individual contributor.

### **Current Policy**
Until formal governance is established:
- The Project Steward maintains ownership of the repository.
- The community is encouraged to fork if development stalls.

### **Future Transfer Options**
The Steward may update this governance document at any time to clarify long-term ownership, including:

- Transfer to a small group of trusted collaborators.
- Transfer to a non-profit organization.
- Transfer to the community at large through an open voting or committee system.

Any such transfer will be documented in a future revision of this file.

---

## 5. Specification Maturity Levels

Each document type progresses through:

1. **Draft** — initial notes and unstable proposals.
2. **Working Draft** — has structure, ready for experimentation.
3. **Candidate Spec** — stable format; client developers must test interoperability.
4. **Standard** — stable and versioned; backward compatibility commitments apply.

Files should indicate their maturity level at the top.

---

## 6. How to Propose Changes

1. Open an issue describing the change.
2. Provide rationale, examples, and possible alternatives.
3. For syntax/format changes, include:
   - Before/after examples
   - Expected parsing rules
   - Compatibility concerns
4. Trusted Collaborators and the Steward will review the proposal.

---

## 7. License and Use Rights

- **Code:** MIT (see `LICENSE-CODE.md`)  
- **Specification documents:** CC BY-ND 4.0 (see `LICENSE-SPECS.md`)  

Specification documents include all document format specifications (HDOC, Embedded HDOC, CDOC, CONDOC) as well as related specifications such as Parsing Rules, Connections, and Static Comments.  
These documents define the structure, rules, and standards of the Default Web project and are licensed under CC BY-ND 4.0 to prevent derivative modifications.

---

## 8. Amendments to This Document

This governance document may be updated over time.  
Changes should follow the same proposal process described above.