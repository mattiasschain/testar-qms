## Document identification

- SOP ID: SOP-04
- Title: Platform Versioning and System State Identification
- Document type: Standard Operating Procedure (SOP)

All information relating to document status, authorship, versioning, and effective date is maintained as document metadata within the version-controlled QMS repository hosted on GitHub.

---

## 1. Purpose

This SOP defines how platform versioning and system state identification are performed for the Hälsa Hemma platform, ensuring that each operational and released state of the platform is uniquely identifiable, traceable, and reconstructable over time.

The SOP supports controlled change, verification and validation, incident investigation, regulatory traceability, and post-market obligations by ensuring that the exact system state in use at any point in time can be determined.

---

## 2. Scope

This SOP applies to Hälsa Hemma’s in-house developed digital platform, as defined and scoped in the QMS system description (README.md, Section 2).

It covers:

- source code versioning,
- release identification,
- system state definition and preservation, and
- traceability between releases, changes, and operational use.

This SOP applies to all platform components, with additional traceability requirements where modules are qualified as medical devices under MDR.

---

## 3. Prerequisites and role competence

Execution of this SOP requires that involved personnel:

- understand **system state** as a controlled and regulatory-relevant concept within the QMS,
- are familiar with version control principles, including immutable commits, release tags, and protected branches,
- understand how source code, configuration, and deployment artefacts together define an authoritative system state,
- can maintain traceability between system states, Jira issues, pull requests, and release decisions, and
- understand the heightened traceability expectations applicable where MDR-qualified modules are involved.

---

## 4. Definitions

### 4.1 Platform version

A platform version is a formally released version of the Hälsa Hemma platform, identified by a unique version identifier and corresponding release tag in the version control system.

### 4.2 System state

A system state is the complete and authoritative combination of:

- source code version,
- configuration values affecting runtime behaviour,
- build artefacts, and
- deployment descriptors

that together define how the platform operates at a given point in time.

---

## 5. Version control and authoritative sources

### 5.1 Authoritative repositories

Platform source code and configuration items are maintained in version-controlled repositories hosted on GitHub.

In practice, GitHub is used as the authoritative source for:

- platform code,
- configuration artefacts affecting runtime behaviour, and
- historical version and change information.

This provides a single, consistent reference point for determining what code and configuration formed part of a given platform state.

### 5.2 Immutability of released versions

Once a platform release is created, the corresponding release tag and referenced commit are treated as immutable.

This working practice ensures that released system states remain stable reference points over time and can be relied upon for traceability, investigation, and reconstruction.

---

## 6. Release identification

### 6.1 Release tagging

Platform releases are identified through the creation of a release tag in GitHub.

The release tag points to the exact commit that represents the released system state and may be accompanied by a short release description where useful for orientation.

Release tagging is used as the primary mechanism for identifying which version of the platform was released and placed into operation.

### 6.2 Branching model

Platform development is organised using a structured branching model that separates:

- ongoing development work,
- review and approval activities, and
- release-ready system states.

This separation supports controlled introduction of changes and provides a clear distinction between working code and released platform states.

---

## 7. System state preservation

### 7.1 Preserving released states

For each platform release, the information needed to understand and reproduce the released system state is retained through version-controlled artefacts and associated references.

In practice, this typically includes:

- the release tag and commit reference,
- configuration files or references relevant to runtime behaviour, and
- build or deployment artefacts, or reproducible build and deployment definitions.

### 7.2 Reconstructability

Reconstruction of a released system state is achieved by retrieving the relevant version-controlled artefacts and applying the documented build and deployment procedures.

This approach allows historical system states to be reproduced when needed for investigation, validation, or regulatory review.

---

## 8. Freezing of version documentation and technical file creation

### 8.1 Purpose and relationship to SOP-02

In connection with each release, version documentation is frozen and used to create a technical file.

This practice operationalises the release decision and verification and validation conclusions defined under SOP-02 Platform Change Control and preserves the authoritative system state in accordance with this SOP.

Freezing the version documentation ensures that the technical basis, assessments, and conclusions applicable to a specific released system state are preserved as a coherent and reviewable snapshot.

### 8.2 Practical execution

In practice, freezing of version documentation is performed by:

- summarising the released changes, including scope and purpose,
- consolidating risk, regulatory, and clinical relevance assessments,
- summarising verification and validation activities and conclusions, and
- referencing the authoritative system state (release tag and commit).

This summary is created as a dedicated markdown (md) file and committed to the **GitHub (QMS)** repository under qms/Technical-File/.

The markdown file constitutes the frozen version documentation for the release and serves as the primary input to the technical file for that release.

### 8.3 Separation of MDR and non-MDR releases

Releases are handled in a manner that reflects the platform’s mixed regulatory scope.

In practice, this means that:

- **non-MDR releases** cover parts of the platform that constitute a **National Medical Information System (NMI)** only, and
- **MDR releases** cover modules that are qualified as medical devices.

Version documentation is frozen separately for these release types where applicable, so that technical documentation remains aligned with regulatory applicability.

### 8.4 Purpose of separation

The purpose of separating version documentation and releases is to enable creation and maintenance of:

- a technical file for non-MDR (NMI) parts of the platform, and
- a separate technical file for MDR-qualified modules.

This separation ensures that regulatory documentation remains proportionate, clear, and scoped to the applicable regulatory framework, while relying on a common underlying lifecycle and versioning practice.

---

## 9. Traceability

Traceability between platform releases and their originating work is maintained through consistent linking between tools.

In practice, a platform release can be followed back to:

- the Jira issues included in the release,
- the corresponding pull requests, code reviews, and the recorded release decision under **SOP-02 Platform Change Control**, as linked and traceable within **GitHub (code)**, and
- the frozen version documentation created in accordance with Section 8 of this SOP, stored in **GitHub (QMS)**, which preserves the consolidated release context for the identified system state.

This traceability supports investigation of incidents and deviations, assessment of regulatory relevance, and explanation of historical system behaviour. Also, system state identification and traceability under this SOP provide authoritative inputs for investigation, escalation, and governance of cybersecurity and resilience events under QMS-07 Cybersecurity and Resilience.

---

## 10. Evidence

Evidence of compliance with this SOP is produced as a **direct result of executing the procedures defined herein**, and is therefore inherent in normal platform development and release activities.

In practice, evidence consists of:

- **Change and release records in Jira**, documenting scope, purpose, risk, regulatory relevance, and inclusion of changes in a given release.
- **Version-controlled system states** in **GitHub (code)**, including immutable commits and release tags identifying each released platform version.
- **Traceability links in GitHub (code)** connecting release tags to pull requests, code reviews, and the recorded release decision, and
- **Frozen version documentation** created for each release in accordance with Section 8, stored in **GitHub (QMS)**, consolidating the release context for the identified system state.