# Open Source AI Project Governance and Security Baseline

Version: 2026-03-06

{: .warning}
Not for production use.


<button onclick="toTop()" id="topButton" title="Go to top"
style="display: none; position: fixed; bottom: 20px; right: 30px; border: none; background-color: CornflowerBlue; color: white; cursor: pointer; padding: 10px; border-radius: 10px; font-size: 18px;">to top</button>

<script>
let topButton = document.getElementById("topButton");
window.onscroll = function() {scrollFunction()};

function scrollFunction() {
  if (document.documentElement.scrollTop > 50 ) {
    topButton.style.display = "block";
  } else {
    topButton.style.display = "none";
  }
}

function toTop() {
  document.documentElement.scrollTop = 0;
}
</script>


* Contents
{:toc}

## Overview

The Open Source AI Project Governance and Security Baseline (AIGS Baseline) is designed to act as a minimum set of requirements for AI projects relative to its maturity level. It extends the principles of the [OpenSSF Security Baseline](https://baseline.openssf.org/) to address the unique challenges of developing, deploying, and managing Artificial Intelligence (AI) systems. It is designed to be a foundational guide for ensuring AI systems are secure, robust, transparent, and aligned with governance objectives.

For more information on the motive and purpose, see the [FAQ](FAQ.md).

For more information on the project and to make contributions, visit the [GitHub repo](https://github.com/ossf/security-baseline).

---

## Controls Overview

* [Maturity Level 1 - Foundational](#maturity-level-1---foundational): Foundational security controls for AI projects covering basic governance, supply chain, data integrity, model robustness, deployment, and transparency.
* [Maturity Level 2 - Intermediate](#maturity-level-2---intermediate): Intermediate security controls for AI projects adding formal policies, advanced scanning, continuous testing, and enhanced monitoring.
* [Maturity Level 3 - Advanced](#maturity-level-3---advanced): Advanced security controls for AI projects requiring regulatory compliance, cryptographic signing, third-party testing, runtime safeguards, and incident reporting.


### Level 1

**[AIGS-GA-01.01](#aigs-ga-0101)**: Roles and responsibilities for maintainers and contributors MUST be documented

**[AIGS-GA-01.02](#aigs-ga-0102)**: Documentation MUST cover the entire lifecycle from development to deployment and ongoing monitoring

**[AIGS-GA-02.01](#aigs-ga-0201)**: Model name MUST be disclosed

**[AIGS-GA-02.02](#aigs-ga-0202)**: Developer MUST be disclosed

**[AIGS-GA-02.03](#aigs-ga-0203)**: Release date MUST be disclosed

**[AIGS-GA-02.04](#aigs-ga-0204)**: License MUST be disclosed

**[AIGS-GA-02.05](#aigs-ga-0205)**: Model description MUST be disclosed

**[AIGS-GA-02.06](#aigs-ga-0206)**: Deployment status MUST be disclosed (as necessary)

**[AIGS-GA-02.07](#aigs-ga-0207)**: URL to open source model repository or model release announcement MUST be provided (if available)

**[AIGS-GA-03.01](#aigs-ga-0301)**: Dataset name MUST be disclosed

**[AIGS-GA-03.02](#aigs-ga-0302)**: Country of origin MUST be disclosed

**[AIGS-GA-03.03](#aigs-ga-0303)**: License MUST be disclosed

**[AIGS-GA-03.04](#aigs-ga-0304)**: Description MUST be disclosed

**[AIGS-GA-03.05](#aigs-ga-0305)**: Data processing information MUST be disclosed (if any)

**[AIGS-GA-03.06](#aigs-ga-0306)**: Public URL MUST be provided (if available)

**[AIGS-GA-04.01](#aigs-ga-0401)**: License for model weights MUST be specified

**[AIGS-GA-04.02](#aigs-ga-0402)**: License for model files MUST be specified

**[AIGS-GA-05.01](#aigs-ga-0501)**: Intended use MUST be defined and documented

**[AIGS-GA-05.02](#aigs-ga-0502)**: Ethical principles MUST be documented

**[AIGS-GA-06.01](#aigs-ga-0601)**: Inventory of components MUST be maintained

**[AIGS-GA-06.02](#aigs-ga-0602)**: Inventory of tooling MUST be maintained

**[AIGS-GA-06.03](#aigs-ga-0603)**: Inventory of systems MUST be maintained

**[AIGS-GA-06.04](#aigs-ga-0604)**: Inventory of applications MUST be maintained

**[AIGS-GA-06.05](#aigs-ga-0605)**: Inventory MUST be disclosed in the project README

**[AIGS-SCS-01.01](#aigs-scs-0101)**: Controls to detect poisoned data MUST be implemented

**[AIGS-SCS-01.02](#aigs-scs-0102)**: Controls to prevent poisoned data sourcing MUST be implemented

**[AIGS-SCS-01.03](#aigs-scs-0103)**: Controls MUST be documented

**[AIGS-SCS-01.04](#aigs-scs-0104)**: Controls MUST be disclosed

**[AIGS-SCS-02.01](#aigs-scs-0201)**: Web crawling activity MUST respect robots.txt requirements (if applicable)

**[AIGS-SCS-02.02](#aigs-scs-0202)**: Crawler MUST be clearly identified

**[AIGS-SCS-02.03](#aigs-scs-0203)**: Web crawling activity MUST be disclosed in project documentation

**[AIGS-SCS-03.01](#aigs-scs-0301)**: Version control system MUST be used

**[AIGS-SCS-03.02](#aigs-scs-0302)**: Process for reviewing changes MUST be documented

**[AIGS-SCS-03.03](#aigs-scs-0303)**: Process for approving changes MUST be documented

**[AIGS-DI-01.01](#aigs-di-0101)**: Origin of all training data MUST be tracked

**[AIGS-DI-01.02](#aigs-di-0102)**: Origin of all testing data MUST be tracked

**[AIGS-DI-01.03](#aigs-di-0103)**: Lineage of all training data MUST be tracked

**[AIGS-DI-01.04](#aigs-di-0104)**: Lineage of all testing data MUST be tracked

**[AIGS-DI-02.01](#aigs-di-0201)**: Authentication controls MUST be implemented

**[AIGS-DI-02.02](#aigs-di-0202)**: Authorization controls MUST be implemented

**[AIGS-DI-02.03](#aigs-di-0203)**: Confidentiality of data MUST be protected

**[AIGS-DI-02.04](#aigs-di-0204)**: Integrity of data MUST be protected

**[AIGS-DI-02.05](#aigs-di-0205)**: Availability of data MUST be protected

**[AIGS-DI-03.01](#aigs-di-0301)**: Data access controls MUST be documented

**[AIGS-DI-03.02](#aigs-di-0302)**: Least privilege principle MUST be applied to data access

**[AIGS-DI-04.01](#aigs-di-0401)**: Controls to prevent PII leakage MUST be implemented

**[AIGS-DI-04.02](#aigs-di-0402)**: Controls to prevent proprietary data leakage MUST be implemented

**[AIGS-DI-04.03](#aigs-di-0403)**: Testing for sensitive data leakage MUST be performed

**[AIGS-MR-01.01](#aigs-mr-0101)**: Red teaming MUST be conducted

**[AIGS-MR-01.02](#aigs-mr-0102)**: Red teaming MUST screen for adversarial attack vulnerabilities

**[AIGS-MR-01.03](#aigs-mr-0103)**: Red teaming MUST include prompt injection attack screening

**[AIGS-MR-02.01](#aigs-mr-0201)**: Testing MUST be performed before deployment

**[AIGS-MR-02.02](#aigs-mr-0202)**: Testing MUST use publicly available benchmarks or manually-created task-specific benchmarks

**[AIGS-MR-02.03](#aigs-mr-0203)**: Model resilience against common vulnerabilities MUST be evaluated

**[AIGS-MR-02.04](#aigs-mr-0204)**: Model resilience MUST be quantified

**[AIGS-MR-02.05](#aigs-mr-0205)**: Model resilience MUST be validated

**[AIGS-DP-01.01](#aigs-dp-0101)**: Guardrails MUST be implemented to mitigate identified risks

**[AIGS-DP-01.02](#aigs-dp-0102)**: Guardrails MUST mitigate against prompt injection attacks (at minimum)

**[AIGS-DP-02.01](#aigs-dp-0201)**: Communication channel for vulnerability disclosure MUST be defined

**[AIGS-DP-02.02](#aigs-dp-0202)**: Mechanism for security-related information disclosure MUST be defined

**[AIGS-DP-03.01](#aigs-dp-0301)**: Model output validation MUST be implemented

**[AIGS-DP-03.02](#aigs-dp-0302)**: Model output sanitization MUST be implemented

**[AIGS-TE-01.01](#aigs-te-0101)**: Explanations for design decisions affecting performance MUST be provided (where feasible)

**[AIGS-TE-01.02](#aigs-te-0102)**: Explanations for design decisions affecting security MUST be provided (where feasible)

**[AIGS-TE-02.01](#aigs-te-0201)**: Documentation for intended use MUST be maintained

**[AIGS-TE-02.02](#aigs-te-0202)**: Documentation for limitations MUST be maintained

**[AIGS-TE-02.03](#aigs-te-0203)**: Documentation for potential risks MUST be maintained


### Level 2

**[AIGS-GA-07.01](#aigs-ga-0701)**: AI policy MUST define principles guiding AI activities

**[AIGS-GA-07.02](#aigs-ga-0702)**: AI policy MUST define processes for handling deviations

**[AIGS-GA-07.03](#aigs-ga-0703)**: AI policy MUST define processes for handling exceptions

**[AIGS-GA-07.04](#aigs-ga-0704)**: Policy MUST cover AI resources and assets

**[AIGS-GA-07.05](#aigs-ga-0705)**: Policy MUST cover AI system impact assessment scope

**[AIGS-GA-07.06](#aigs-ga-0706)**: Policy MUST cover AI project secure development

**[AIGS-SCS-04.01](#aigs-scs-0401)**: AI components MUST be scanned in development workflows

**[AIGS-SCS-04.02](#aigs-scs-0402)**: AI components MUST be scanned in CI/CD pipelines

**[AIGS-SCS-04.03](#aigs-scs-0403)**: Scanning MUST detect malicious components

**[AIGS-SCS-04.04](#aigs-scs-0404)**: Scanning MUST detect compromised components

**[AIGS-SCS-05.01](#aigs-scs-0501)**: Training pipeline MUST be documented

**[AIGS-SCS-05.02](#aigs-scs-0502)**: Training pipeline MUST be secured

**[AIGS-SCS-05.03](#aigs-scs-0503)**: Dependencies MUST be documented and secured

**[AIGS-SCS-05.04](#aigs-scs-0504)**: Training code MUST be documented and secured

**[AIGS-SCS-05.05](#aigs-scs-0505)**: Environment configuration MUST be documented and secured

**[AIGS-SCS-06.01](#aigs-scs-0601)**: Provenance records MUST link model artifacts to training datasets

**[AIGS-SCS-06.02](#aigs-scs-0602)**: Provenance records MUST link model artifacts to training code

**[AIGS-SCS-06.03](#aigs-scs-0603)**: Provenance records MUST link model artifacts to training parameters

**[AIGS-SCS-07.01](#aigs-scs-0701)**: Reproducible model builds SHOULD be supported (where feasible)

**[AIGS-SCS-07.02](#aigs-scs-0702)**: Independent parties SHOULD be able to recreate model artifacts

**[AIGS-DI-05.01](#aigs-di-0501)**: Training datasets MUST be tracked and versioned

**[AIGS-DI-05.02](#aigs-di-0502)**: Evaluation datasets MUST be tracked and versioned

**[AIGS-DI-05.03](#aigs-di-0503)**: Traceability of datasets MUST be ensured

**[AIGS-DI-05.04](#aigs-di-0504)**: Reproducibility of datasets MUST be ensured

**[AIGS-DI-06.01](#aigs-di-0601)**: Legal risk assessment MUST be performed

**[AIGS-DI-06.02](#aigs-di-0602)**: Copyright risk assessment MUST be performed

**[AIGS-DI-06.03](#aigs-di-0603)**: Licensing compatibility assessment MUST be performed

**[AIGS-DI-06.04](#aigs-di-0604)**: Data poisoning risk assessment MUST be performed

**[AIGS-DI-06.05](#aigs-di-0605)**: PII/SPI risk assessment MUST be performed

**[AIGS-DI-07.01](#aigs-di-0701)**: Controls to limit unnecessary data MUST be implemented

**[AIGS-DI-07.02](#aigs-di-0702)**: Controls to limit high-risk data MUST be implemented

**[AIGS-MR-03.01](#aigs-mr-0301)**: Red teaming MUST be continuously implemented

**[AIGS-MR-03.02](#aigs-mr-0302)**: Evaluations MUST be continuously implemented

**[AIGS-MR-03.03](#aigs-mr-0303)**: Testing MUST occur before production pushes

**[AIGS-MR-03.04](#aigs-mr-0304)**: Testing MUST occur before model re-training

**[AIGS-MR-04.01](#aigs-mr-0401)**: Regression tests for safety behaviors MUST be maintained

**[AIGS-MR-04.02](#aigs-mr-0402)**: Regression tests for security behaviors MUST be maintained

**[AIGS-MR-05.01](#aigs-mr-0501)**: Scope of testing MUST be documented

**[AIGS-MR-05.02](#aigs-mr-0502)**: Limitations of testing MUST be documented

**[AIGS-DP-04.01](#aigs-dp-0401)**: Access to models MUST follow least-privilege principles

**[AIGS-DP-04.02](#aigs-dp-0402)**: Access to tools and tool calling MUST follow least-privilege principles

**[AIGS-DP-04.03](#aigs-dp-0403)**: Access to deployment infrastructure MUST follow least-privilege principles

**[AIGS-DP-05.01](#aigs-dp-0501)**: Logging for deployment environments MUST be implemented

**[AIGS-DP-05.02](#aigs-dp-0502)**: Monitoring for deployment environments MUST be implemented

**[AIGS-DP-05.03](#aigs-dp-0503)**: Tool use logging MUST be implemented

**[AIGS-DP-05.04](#aigs-dp-0504)**: Anomaly detection MUST be implemented

**[AIGS-DP-06.01](#aigs-dp-0601)**: Incident response procedures MUST be defined

**[AIGS-DP-06.02](#aigs-dp-0602)**: Procedures MUST ensure timely response to incidents

**[AIGS-DP-07.01](#aigs-dp-0701)**: Model update release processes MUST be documented

**[AIGS-DP-07.02](#aigs-dp-0702)**: Security patch release processes MUST be documented


### Level 3

**[AIGS-GA-08.01](#aigs-ga-0801)**: Regulatory compliance status MUST be assessed

**[AIGS-GA-08.02](#aigs-ga-0802)**: Compliance or non-compliance MUST be disclosed

**[AIGS-GA-09.01](#aigs-ga-0901)**: Model metadata MUST be disclosed in machine-readable format

**[AIGS-GA-09.02](#aigs-ga-0902)**: Data metadata MUST be disclosed in machine-readable format

**[AIGS-GA-09.03](#aigs-ga-0903)**: Disclosure MUST be available while project is active

**[AIGS-SCS-08.01](#aigs-scs-0801)**: AI models MUST be signed with cryptographic tools

**[AIGS-SCS-08.02](#aigs-scs-0802)**: Model files MUST be signed with cryptographic tools

**[AIGS-SCS-08.03](#aigs-scs-0803)**: Release artifacts MUST be signed with cryptographic tools

**[AIGS-SCS-08.04](#aigs-scs-0804)**: Signatures MUST be verified before deployment

**[AIGS-DI-08.01](#aigs-di-0801)**: All read access MUST be logged

**[AIGS-DI-08.02](#aigs-di-0802)**: All write access MUST be logged

**[AIGS-DI-08.03](#aigs-di-0803)**: Timestamp MUST be recorded for all access

**[AIGS-DI-08.04](#aigs-di-0804)**: User ID MUST be recorded for all access

**[AIGS-DI-08.05](#aigs-di-0805)**: Action performed MUST be recorded

**[AIGS-DI-08.06](#aigs-di-0806)**: Dataset ID MUST be recorded

**[AIGS-DI-08.07](#aigs-di-0807)**: Dataset version(s) accessed MUST be recorded

**[AIGS-MR-06.01](#aigs-mr-0601)**: Independent third-party testing MUST be conducted

**[AIGS-MR-06.02](#aigs-mr-0602)**: Third-parties MUST be trusted

**[AIGS-MR-06.03](#aigs-mr-0603)**: Adversarial robustness testing MUST be performed

**[AIGS-MR-07.01](#aigs-mr-0701)**: Runtime evaluation against standardized benchmarks MUST be performed

**[AIGS-MR-07.02](#aigs-mr-0702)**: Benchmark suite MUST be standardized

**[AIGS-MR-07.03](#aigs-mr-0703)**: Benchmark suite MUST evolve over time

**[AIGS-DP-08.01](#aigs-dp-0801)**: Malicious input detection MUST be implemented

**[AIGS-DP-08.02](#aigs-dp-0802)**: Malicious output detection MUST be implemented

**[AIGS-DP-08.03](#aigs-dp-0803)**: Malicious input mitigation MUST be implemented

**[AIGS-DP-08.04](#aigs-dp-0804)**: Malicious output mitigation MUST be implemented

**[AIGS-DP-08.05](#aigs-dp-0805)**: Unexpected behavior detection MUST be implemented

**[AIGS-DP-08.06](#aigs-dp-0806)**: Unauthorized system-level behavior detection MUST be implemented

**[AIGS-DP-09.01](#aigs-dp-0901)**: Security mechanism MUST be implemented to halt/disable the AI project

**[AIGS-DP-09.02](#aigs-dp-0902)**: Mechanism MUST be able to contain the AI project

**[AIGS-DP-09.03](#aigs-dp-0903)**: Mechanism MUST enable immediate action

**[AIGS-TE-03.01](#aigs-te-0301)**: Residual risks MUST be documented

**[AIGS-TE-03.02](#aigs-te-0302)**: Known safeguard limitations MUST be documented

**[AIGS-TE-04.01](#aigs-te-0401)**: Public record of incidents MUST be maintained

**[AIGS-TE-04.02](#aigs-te-0402)**: Safety incidents MUST be recorded

**[AIGS-TE-04.03](#aigs-te-0403)**: Security incidents MUST be recorded

**[AIGS-TE-04.04](#aigs-te-0404)**: Ex post mitigations MUST be recorded




## Governance and Accountability

Controls for governance and accountability.



### AIGS-GA-01 - Contributor Roles and Responsibilities

The project MUST document the roles and responsibilities for maintainers and contributors to the AI project&#39;s lifecycle from development to deployment and ongoing monitoring.



#### AIGS-GA-01.01

**Requirement:** Roles and responsibilities for maintainers and contributors MUST be documented



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-GA-01.02

**Requirement:** Documentation MUST cover the entire lifecycle from development to deployment and ongoing monitoring



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced




---

### AIGS-GA-02 - Model Governance

The project MUST provide written, documented disclosure of the AI models ingested in, called, or otherwise used in the development or deployment of the open source AI project.



#### AIGS-GA-02.01

**Requirement:** Model name MUST be disclosed



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-GA-02.02

**Requirement:** Developer MUST be disclosed



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-GA-02.03

**Requirement:** Release date MUST be disclosed



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-GA-02.04

**Requirement:** License MUST be disclosed



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-GA-02.05

**Requirement:** Model description MUST be disclosed



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-GA-02.06

**Requirement:** Deployment status MUST be disclosed (as necessary)



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-GA-02.07

**Requirement:** URL to open source model repository or model release announcement MUST be provided (if available)



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced




---

### AIGS-GA-03 - Data Governance

The project MUST disclose datasets ingested in or otherwise used in the development or deployment of the open source AI project. This includes datasets used for training, testing, and validation.



#### AIGS-GA-03.01

**Requirement:** Dataset name MUST be disclosed



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-GA-03.02

**Requirement:** Country of origin MUST be disclosed



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-GA-03.03

**Requirement:** License MUST be disclosed



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-GA-03.04

**Requirement:** Description MUST be disclosed



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-GA-03.05

**Requirement:** Data processing information MUST be disclosed (if any)



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-GA-03.06

**Requirement:** Public URL MUST be provided (if available)



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced




---

### AIGS-GA-04 - Licensing

While active, the project MUST specify a license for the model weights and model files.



#### AIGS-GA-04.01

**Requirement:** License for model weights MUST be specified



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-GA-04.02

**Requirement:** License for model files MUST be specified



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced




---

### AIGS-GA-05 - Ethics and Intended Use

The project MUST define and document the intended use of the open source AI project, including the ethical principles that guide open source AI project development and deployment.



#### AIGS-GA-05.01

**Requirement:** Intended use MUST be defined and documented



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-GA-05.02

**Requirement:** Ethical principles MUST be documented



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced




---

### AIGS-GA-06 - Project Inventory

The project MUST maintain an inventory of its components, tooling, systems and applications, disclosed within the README of the repository where the project is made available.



#### AIGS-GA-06.01

**Requirement:** Inventory of components MUST be maintained



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-GA-06.02

**Requirement:** Inventory of tooling MUST be maintained



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-GA-06.03

**Requirement:** Inventory of systems MUST be maintained



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-GA-06.04

**Requirement:** Inventory of applications MUST be maintained



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-GA-06.05

**Requirement:** Inventory MUST be disclosed in the project README



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced




---

### AIGS-GA-07 - AI Policy

The project MUST define an AI policy with i) principles that guide all activities of the organization related to AI and ii) processes for handling deviations and exceptions to policy.



#### AIGS-GA-07.01

**Requirement:** AI policy MUST define principles guiding AI activities



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-GA-07.02

**Requirement:** AI policy MUST define processes for handling deviations



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-GA-07.03

**Requirement:** AI policy MUST define processes for handling exceptions



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-GA-07.04

**Requirement:** Policy MUST cover AI resources and assets



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-GA-07.05

**Requirement:** Policy MUST cover AI system impact assessment scope



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-GA-07.06

**Requirement:** Policy MUST cover AI project secure development



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced




---

### AIGS-GA-08 - Regulatory Compliance

To the extent the open source AI project meets regulatory requirements and standards for the deployment of AI models and systems, the project MUST disclose (non-)compliance.



#### AIGS-GA-08.01

**Requirement:** Regulatory compliance status MUST be assessed



**Control applies to:**
- Maturity Level 3 - Advanced


#### AIGS-GA-08.02

**Requirement:** Compliance or non-compliance MUST be disclosed



**Control applies to:**
- Maturity Level 3 - Advanced




---

### AIGS-GA-09 - AI Bill of Materials

While active, structured disclosures of relevant model and data metadata relevant to AI project development and deployment MUST be made available in machine-readable format to inform downstream risk-based controls.



#### AIGS-GA-09.01

**Requirement:** Model metadata MUST be disclosed in machine-readable format



**Control applies to:**
- Maturity Level 3 - Advanced


#### AIGS-GA-09.02

**Requirement:** Data metadata MUST be disclosed in machine-readable format



**Control applies to:**
- Maturity Level 3 - Advanced


#### AIGS-GA-09.03

**Requirement:** Disclosure MUST be available while project is active



**Control applies to:**
- Maturity Level 3 - Advanced




---

## Supply Chain Security

Controls for supply chain security.



### AIGS-SCS-01 - Secure Data Sourcing

The project MUST implement controls to detect and prevent the unintentional sourcing of poisoned data. Controls MUST be documented and disclosed.



#### AIGS-SCS-01.01

**Requirement:** Controls to detect poisoned data MUST be implemented



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-SCS-01.02

**Requirement:** Controls to prevent poisoned data sourcing MUST be implemented



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-SCS-01.03

**Requirement:** Controls MUST be documented



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-SCS-01.04

**Requirement:** Controls MUST be disclosed



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced




---

### AIGS-SCS-02 - Ethical Web Crawling

To the extent web crawling is used to source data, web crawling activity MUST respect robots.txt requirements, the crawler MUST be clearly identified, and web crawling activity MUST be disclosed in project documentation.



#### AIGS-SCS-02.01

**Requirement:** Web crawling activity MUST respect robots.txt requirements (if applicable)



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-SCS-02.02

**Requirement:** Crawler MUST be clearly identified



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-SCS-02.03

**Requirement:** Web crawling activity MUST be disclosed in project documentation



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced




---

### AIGS-SCS-03 - Change Control

The project MUST use a version control system and have a documented process for reviewing and approving changes.



#### AIGS-SCS-03.01

**Requirement:** Version control system MUST be used



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-SCS-03.02

**Requirement:** Process for reviewing changes MUST be documented



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-SCS-03.03

**Requirement:** Process for approving changes MUST be documented



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced




---

### AIGS-SCS-04 - AI Components Scanning

Embedded AI components MUST be scanned as part of development workflows, including CI/CD pipelines, to prevent application security risks from malicious or otherwise compromised components.



#### AIGS-SCS-04.01

**Requirement:** AI components MUST be scanned in development workflows



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-SCS-04.02

**Requirement:** AI components MUST be scanned in CI/CD pipelines



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-SCS-04.03

**Requirement:** Scanning MUST detect malicious components



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-SCS-04.04

**Requirement:** Scanning MUST detect compromised components



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced




---

### AIGS-SCS-05 - Training Pipeline Integrity

The project MUST document and secure the training pipeline used to produce model artifacts, including dependencies, training code, and environment configuration.



#### AIGS-SCS-05.01

**Requirement:** Training pipeline MUST be documented



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-SCS-05.02

**Requirement:** Training pipeline MUST be secured



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-SCS-05.03

**Requirement:** Dependencies MUST be documented and secured



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-SCS-05.04

**Requirement:** Training code MUST be documented and secured



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-SCS-05.05

**Requirement:** Environment configuration MUST be documented and secured



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced




---

### AIGS-SCS-06 - Model Provenance

The project MUST maintain provenance records linking: model artifacts, training datasets, training code, and training parameters.



#### AIGS-SCS-06.01

**Requirement:** Provenance records MUST link model artifacts to training datasets



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-SCS-06.02

**Requirement:** Provenance records MUST link model artifacts to training code



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-SCS-06.03

**Requirement:** Provenance records MUST link model artifacts to training parameters



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced




---

### AIGS-SCS-07 - Reproducible Builds

Where feasible, the project SHOULD support reproducible model builds such that independent parties can recreate the model artifacts from disclosed inputs.



#### AIGS-SCS-07.01

**Requirement:** Reproducible model builds SHOULD be supported (where feasible)



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-SCS-07.02

**Requirement:** Independent parties SHOULD be able to recreate model artifacts



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced




---

### AIGS-SCS-08 - Model Integrity

The project MUST sign AI models, model files, and/or other release artifacts with cryptographic tools and verify them before deployment to prevent the introduction of untrusted components.



#### AIGS-SCS-08.01

**Requirement:** AI models MUST be signed with cryptographic tools



**Control applies to:**
- Maturity Level 3 - Advanced


#### AIGS-SCS-08.02

**Requirement:** Model files MUST be signed with cryptographic tools



**Control applies to:**
- Maturity Level 3 - Advanced


#### AIGS-SCS-08.03

**Requirement:** Release artifacts MUST be signed with cryptographic tools



**Control applies to:**
- Maturity Level 3 - Advanced


#### AIGS-SCS-08.04

**Requirement:** Signatures MUST be verified before deployment



**Control applies to:**
- Maturity Level 3 - Advanced




---

## Data Integrity

Controls for data integrity.



### AIGS-DI-01 - Enforceable Data Policy

Track the origin and lineage of all data used for training and testing AI models.



#### AIGS-DI-01.01

**Requirement:** Origin of all training data MUST be tracked



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-DI-01.02

**Requirement:** Origin of all testing data MUST be tracked



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-DI-01.03

**Requirement:** Lineage of all training data MUST be tracked



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-DI-01.04

**Requirement:** Lineage of all testing data MUST be tracked



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced




---

### AIGS-DI-02 - Data Security

The project MUST implement robust security controls to protect the confidentiality, integrity, and availability of data.



#### AIGS-DI-02.01

**Requirement:** Authentication controls MUST be implemented



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-DI-02.02

**Requirement:** Authorization controls MUST be implemented



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-DI-02.03

**Requirement:** Confidentiality of data MUST be protected



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-DI-02.04

**Requirement:** Integrity of data MUST be protected



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-DI-02.05

**Requirement:** Availability of data MUST be protected



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced




---

### AIGS-DI-03 - Data Least Privilege Access

Data access controls MUST be clearly documented and follow the principles of least privilege access.



#### AIGS-DI-03.01

**Requirement:** Data access controls MUST be documented



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-DI-03.02

**Requirement:** Least privilege principle MUST be applied to data access



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced




---

### AIGS-DI-04 - Sensitive and Copyright Data Leakage Prevention

The project MUST implement controls and testing to prevent the project from inadvertently revealing sensitive information (e.g., PII, proprietary data) from its training set.



#### AIGS-DI-04.01

**Requirement:** Controls to prevent PII leakage MUST be implemented



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-DI-04.02

**Requirement:** Controls to prevent proprietary data leakage MUST be implemented



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-DI-04.03

**Requirement:** Testing for sensitive data leakage MUST be performed



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced




---

### AIGS-DI-05 - Dataset Cataloguing

Datasets used for training and evaluation MUST be tracked and versioned to ensure traceability and reproducibility.



#### AIGS-DI-05.01

**Requirement:** Training datasets MUST be tracked and versioned



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-DI-05.02

**Requirement:** Evaluation datasets MUST be tracked and versioned



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-DI-05.03

**Requirement:** Traceability of datasets MUST be ensured



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-DI-05.04

**Requirement:** Reproducibility of datasets MUST be ensured



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced




---

### AIGS-DI-06 - Dataset Risk Assessment

The project MUST assess datasets for, at a minimum: legal and copyright risk, licensing compatibility with project intended use, and security risks (e.g., data poisoning, PII/SPI).



#### AIGS-DI-06.01

**Requirement:** Legal risk assessment MUST be performed



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-DI-06.02

**Requirement:** Copyright risk assessment MUST be performed



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-DI-06.03

**Requirement:** Licensing compatibility assessment MUST be performed



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-DI-06.04

**Requirement:** Data poisoning risk assessment MUST be performed



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-DI-06.05

**Requirement:** PII/SPI risk assessment MUST be performed



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced




---

### AIGS-DI-07 - Data Risk Minimization

The project MUST implement controls to limit the use of unnecessary or high-risk data.



#### AIGS-DI-07.01

**Requirement:** Controls to limit unnecessary data MUST be implemented



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-DI-07.02

**Requirement:** Controls to limit high-risk data MUST be implemented



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced




---

### AIGS-DI-08 - Full Audit Logging

Read or write access to data must be logged, with timestamp, user id, action performed (read/write), and dataset id and version(s) accessed.



#### AIGS-DI-08.01

**Requirement:** All read access MUST be logged



**Control applies to:**
- Maturity Level 3 - Advanced


#### AIGS-DI-08.02

**Requirement:** All write access MUST be logged



**Control applies to:**
- Maturity Level 3 - Advanced


#### AIGS-DI-08.03

**Requirement:** Timestamp MUST be recorded for all access



**Control applies to:**
- Maturity Level 3 - Advanced


#### AIGS-DI-08.04

**Requirement:** User ID MUST be recorded for all access



**Control applies to:**
- Maturity Level 3 - Advanced


#### AIGS-DI-08.05

**Requirement:** Action performed MUST be recorded



**Control applies to:**
- Maturity Level 3 - Advanced


#### AIGS-DI-08.06

**Requirement:** Dataset ID MUST be recorded



**Control applies to:**
- Maturity Level 3 - Advanced


#### AIGS-DI-08.07

**Requirement:** Dataset version(s) accessed MUST be recorded



**Control applies to:**
- Maturity Level 3 - Advanced




---

## Model Robustness

Controls for model robustness.



### AIGS-MR-01 - Model Robustness - Red Teaming

The project MUST undertake red teaming to screen for vulnerabilities to adversarial attacks, including prompt injection attacks.



#### AIGS-MR-01.01

**Requirement:** Red teaming MUST be conducted



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-MR-01.02

**Requirement:** Red teaming MUST screen for adversarial attack vulnerabilities



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-MR-01.03

**Requirement:** Red teaming MUST include prompt injection attack screening



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced




---

### AIGS-MR-02 - Model Evaluations

Prior to deployment, the project team MUST test against publicly available or manually-created, task-specific benchmarks in order to evaluate, quantify, and validate the resilience of the AI project against common vulnerabilities.



#### AIGS-MR-02.01

**Requirement:** Testing MUST be performed before deployment



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-MR-02.02

**Requirement:** Testing MUST use publicly available benchmarks or manually-created task-specific benchmarks



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-MR-02.03

**Requirement:** Model resilience against common vulnerabilities MUST be evaluated



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-MR-02.04

**Requirement:** Model resilience MUST be quantified



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-MR-02.05

**Requirement:** Model resilience MUST be validated



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced




---

### AIGS-MR-03 - Continuous Testing

The project MUST continuously implement red teaming and evaluations prior to pushing system updates or model re-training into production.



#### AIGS-MR-03.01

**Requirement:** Red teaming MUST be continuously implemented



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-MR-03.02

**Requirement:** Evaluations MUST be continuously implemented



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-MR-03.03

**Requirement:** Testing MUST occur before production pushes



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-MR-03.04

**Requirement:** Testing MUST occur before model re-training



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced




---

### AIGS-MR-04 - Regression Testing

The project MUST maintain regression tests for safety and security behaviors to prevent regression during updates.



#### AIGS-MR-04.01

**Requirement:** Regression tests for safety behaviors MUST be maintained



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-MR-04.02

**Requirement:** Regression tests for security behaviors MUST be maintained



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced




---

### AIGS-MR-05 - Evaluation Coverage

The project MUST document the scope and limitations of testing.



#### AIGS-MR-05.01

**Requirement:** Scope of testing MUST be documented



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-MR-05.02

**Requirement:** Limitations of testing MUST be documented



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced




---

### AIGS-MR-06 - Third-Party Red Teaming

The project MUST conduct or commission independent testing for adversarial robustness from trusted third-parties.



#### AIGS-MR-06.01

**Requirement:** Independent third-party testing MUST be conducted



**Control applies to:**
- Maturity Level 3 - Advanced


#### AIGS-MR-06.02

**Requirement:** Third-parties MUST be trusted



**Control applies to:**
- Maturity Level 3 - Advanced


#### AIGS-MR-06.03

**Requirement:** Adversarial robustness testing MUST be performed



**Control applies to:**
- Maturity Level 3 - Advanced




---

### AIGS-MR-07 - Robustness Benchmark Testing

The project MUST evaluate models used in the AI project at runtime against an evolving suite of standardized robustness benchmarks.



#### AIGS-MR-07.01

**Requirement:** Runtime evaluation against standardized benchmarks MUST be performed



**Control applies to:**
- Maturity Level 3 - Advanced


#### AIGS-MR-07.02

**Requirement:** Benchmark suite MUST be standardized



**Control applies to:**
- Maturity Level 3 - Advanced


#### AIGS-MR-07.03

**Requirement:** Benchmark suite MUST evolve over time



**Control applies to:**
- Maturity Level 3 - Advanced




---

## Deployment

Controls for deployment.



### AIGS-DP-01 - Guardrails Implementation

The project MUST implement guardrails to mitigate identified risks, and at a minimum, implement guardrails to mitigate against prompt injection attacks (input).



#### AIGS-DP-01.01

**Requirement:** Guardrails MUST be implemented to mitigate identified risks



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-DP-01.02

**Requirement:** Guardrails MUST mitigate against prompt injection attacks (at minimum)



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced




---

### AIGS-DP-02 - Vulnerability Disclosure Mechanism

The project MUST have a defined communication channel or mechanism through which vulnerabilities and other security-related information may be disclosed to the project contributors and maintainers.



#### AIGS-DP-02.01

**Requirement:** Communication channel for vulnerability disclosure MUST be defined



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-DP-02.02

**Requirement:** Mechanism for security-related information disclosure MUST be defined



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced




---

### AIGS-DP-03 - Insecure Output Handling

The project MUST validate and sanitize model outputs to prevent downstream vulnerabilities.



#### AIGS-DP-03.01

**Requirement:** Model output validation MUST be implemented



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-DP-03.02

**Requirement:** Model output sanitization MUST be implemented



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced




---

### AIGS-DP-04 - Deployment Infrastructure

Access to models, tools and tool calling functionality, and general deployment scaffolding or infrastructure MUST follow least-privilege principles.



#### AIGS-DP-04.01

**Requirement:** Access to models MUST follow least-privilege principles



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-DP-04.02

**Requirement:** Access to tools and tool calling MUST follow least-privilege principles



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-DP-04.03

**Requirement:** Access to deployment infrastructure MUST follow least-privilege principles



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced




---

### AIGS-DP-05 - Logging and Monitoring

The project MUST implement logging and monitoring for deployment environments, including tool use, to detect misuse or anomalies.



#### AIGS-DP-05.01

**Requirement:** Logging for deployment environments MUST be implemented



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-DP-05.02

**Requirement:** Monitoring for deployment environments MUST be implemented



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-DP-05.03

**Requirement:** Tool use logging MUST be implemented



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-DP-05.04

**Requirement:** Anomaly detection MUST be implemented



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced




---

### AIGS-DP-06 - Incident Response Procedures

The project MUST define procedures for responding to security incidents involving the AI project in a timely manner.



#### AIGS-DP-06.01

**Requirement:** Incident response procedures MUST be defined



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-DP-06.02

**Requirement:** Procedures MUST ensure timely response to incidents



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced




---

### AIGS-DP-07 - Project Maintenance

The project MUST document processes for releasing model updates and security patches.



#### AIGS-DP-07.01

**Requirement:** Model update release processes MUST be documented



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-DP-07.02

**Requirement:** Security patch release processes MUST be documented



**Control applies to:**
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced




---

### AIGS-DP-08 - Runtime Safeguards

Deployment environments MUST include runtime safeguards for detecting and mitigating malicious inputs and outputs and unexpected or unauthorized system-level behavior.



#### AIGS-DP-08.01

**Requirement:** Malicious input detection MUST be implemented



**Control applies to:**
- Maturity Level 3 - Advanced


#### AIGS-DP-08.02

**Requirement:** Malicious output detection MUST be implemented



**Control applies to:**
- Maturity Level 3 - Advanced


#### AIGS-DP-08.03

**Requirement:** Malicious input mitigation MUST be implemented



**Control applies to:**
- Maturity Level 3 - Advanced


#### AIGS-DP-08.04

**Requirement:** Malicious output mitigation MUST be implemented



**Control applies to:**
- Maturity Level 3 - Advanced


#### AIGS-DP-08.05

**Requirement:** Unexpected behavior detection MUST be implemented



**Control applies to:**
- Maturity Level 3 - Advanced


#### AIGS-DP-08.06

**Requirement:** Unauthorized system-level behavior detection MUST be implemented



**Control applies to:**
- Maturity Level 3 - Advanced




---

### AIGS-DP-09 - Kill Switch

The project MUST implement a security mechanism designed to immediately halt, disable, or contain an AI project if it is believed to behave in dangerous or unpredictable ways causing harm.



#### AIGS-DP-09.01

**Requirement:** Security mechanism MUST be implemented to halt/disable the AI project



**Control applies to:**
- Maturity Level 3 - Advanced


#### AIGS-DP-09.02

**Requirement:** Mechanism MUST be able to contain the AI project



**Control applies to:**
- Maturity Level 3 - Advanced


#### AIGS-DP-09.03

**Requirement:** Mechanism MUST enable immediate action



**Control applies to:**
- Maturity Level 3 - Advanced




---

## Transparency and Explainability

Controls for transparency and explainability.



### AIGS-TE-01 - Explainability

Where feasible, the project MUST provide explanations for design decisions that affect project performance and security.



#### AIGS-TE-01.01

**Requirement:** Explanations for design decisions affecting performance MUST be provided (where feasible)



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-TE-01.02

**Requirement:** Explanations for design decisions affecting security MUST be provided (where feasible)



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced




---

### AIGS-TE-02 - System Documentation

Project contributors MUST maintain clear and comprehensive documentation for the AI system, including its intended use, limitations, and potential risks.



#### AIGS-TE-02.01

**Requirement:** Documentation for intended use MUST be maintained



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-TE-02.02

**Requirement:** Documentation for limitations MUST be maintained



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced


#### AIGS-TE-02.03

**Requirement:** Documentation for potential risks MUST be maintained



**Control applies to:**
- Maturity Level 1 - Foundational
- Maturity Level 2 - Intermediate
- Maturity Level 3 - Advanced




---

### AIGS-TE-03 - Residual Risk Documentation

The project MUST document residual risks and known limitations of safeguards.



#### AIGS-TE-03.01

**Requirement:** Residual risks MUST be documented



**Control applies to:**
- Maturity Level 3 - Advanced


#### AIGS-TE-03.02

**Requirement:** Known safeguard limitations MUST be documented



**Control applies to:**
- Maturity Level 3 - Advanced




---

### AIGS-TE-04 - Security Incident Reporting

The project MUST maintain a public record of safety and security incidents and ex post mitigations.



#### AIGS-TE-04.01

**Requirement:** Public record of incidents MUST be maintained



**Control applies to:**
- Maturity Level 3 - Advanced


#### AIGS-TE-04.02

**Requirement:** Safety incidents MUST be recorded



**Control applies to:**
- Maturity Level 3 - Advanced


#### AIGS-TE-04.03

**Requirement:** Security incidents MUST be recorded



**Control applies to:**
- Maturity Level 3 - Advanced


#### AIGS-TE-04.04

**Requirement:** Ex post mitigations MUST be recorded



**Control applies to:**
- Maturity Level 3 - Advanced




---






## Acknowledgments

This document was developed, under the leadership of Derek Leist, thanks to contributions from technical experts across IBM Research, in addition to feedback and contributions from external collaborators including:
- [AIGS Baseline contributors](https://github.com/ibm/ai-security-baseline/graphs/contributors)

