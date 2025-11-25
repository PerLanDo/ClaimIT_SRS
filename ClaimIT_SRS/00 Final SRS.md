#

# **Software Requirements Specification**

# **for**

# **ClaimIT**

**Version 1.0**

**Prepared by**

|   Jubay Perlan    | perlan.jubay@g.msuiit.ed.ph       |   IT3N.1   |
| :---------------: | --------------------------------- | :--------: |
| **Espiña Joseph** | **joseph.espina@g.msuiit.edu.ph** | **IT3N.1** |
|                   |                                   |            |

|    Faculty: | Mary Ann Gliefen A. Bermudo               |
| ----------: | :---------------------------------------- |
| **Course:** | **ISY108 Requirements Engineering**       |
|   **Date:** | **\<place the date of submission here\>** |

## **Table of Contents**

**Table of Contents [ii](#table-of-contents)**

**Revision History [iii](#heading)**

**Executive Summary [1](#executive-summary)**

**1\.** **Introduction [1](#introduction)**  
1.1 Purpose [1](#purpose)  
1.2 Intended Audience and Reading Suggestions [1](#intended-audience-and-reading-suggestions)

**2\.** **Project Description [1](#project-description)**  
2.1 Overview of the Current System [1](#overview-of-the-current-system)  
2.2 Problem Statement [2](#problem-statement)  
2.3 Objectives [2](#objectives)  
2.4 Significance of the System [2](#significance-of-the-system)  
2.5 Scope and Limitation [2](#scope-and-limitation)  
2.6 Benchmark Systems [1](#heading=h.vwqafu79u5jk)  
1.3 Salient Features of the System [1](#heading=h.vwqafu79u5jk)  
2.6 Gantt Chart [2](#benchmark-systems)

**3\.** **Methodology [2](#methodology)**  
3.1 Requirements [2](#requirements)  
3.2 Design [3](#design)  
3.3 Build prototype [3](#heading=h.gjn26wscgrbs)  
3.4 User evaluation [3](#heading=h.yb4cptb85xs7)  
3.5 Refining prototype [3](#heading=h.yb4cptb85xs7)  
3.6 Implement and Maintenance [3](#implementation-and-maintenance)

**4\.** **Requirements Definition [3](#requirements-definition)**  
4.1 Requirements Traceability Matrix [3](#requirements-traceability-matrix)  
4.2 Proposed Activity Diagram [3](#activity-diagram)

**5\.** **Analysis and Design [4](#analysis-and-design)**  
5.1 Use Case Diagram [4](#use-case-diagram)  
5.2 Use Case Description [4](#use-case-description)  
5.3 Sequence Diagram [6](#sequence-diagram)  
5.4 Collaboration Diagram [6](#collaboration-diagram)

**6\.** **Data Models [7](#data-models)**  
6.1 Entity-Relationship Diagram [7](#entity-relationship-diagram)  
6.2 Class Diagram [7](#class-diagram)  
6.3 Context Diagram [7](#context-diagram)  
6.4 Component Diagram [7](#component-diagram)  
6.5 Package Diagram [8](#package-diagram)

**7\.** **The System [8](#the-system)**  
7.1 System Overview [8](#system-overview)

**8\.** **Other Nonfunctional Requirements [9](#other-nonfunctional-requirements)**  
8.1 Performance Requirements [9](#performance-requirements)  
8.2 Safety Requirements [9](#safety-requirements)  
8.3 Security Requirements [9](#security-requirements)  
8.4 Software Quality Attributes [9](#software-quality-attributes)

**9\.** **Results and Discussion [10](#results-and-discussion)**

**10\.** **Summary and Conclusion [10](#summary-and-conclusion)**

**11\.** **Recommendations [10](#recommendations)**

**Appendix A: Working Bibliography [10](#the-system)**

**Appendix B: Interview Results and Documentation [10](#appendix-b:-interview-results-and-documentation)**

**Appendix C: Work Breakdown Structure [10](#the-system)**

**Appendix D: Glossary**

**Revision History**

| Name | Date | Reason For Changes | Version |
| :--- | :--- | :----------------- | :------ |
|      |      |                    |         |
|      |      |                    |         |

# **Executive Summary**

This document outlines the Software Requirements Specification (SRS) for the **ClaimIT** project, a Progressive Web Application (PWA) designed to modernize the lost and found management system at Mindanao State University - Iligan Institute of Technology (MSU-IIT). The primary deliverables are this comprehensive SRS document and a fully functional prototype demonstrating the system's core capabilities.

The current manual system, managed exclusively by the Security Intelligence Division (SID), relies entirely on handwritten logbooks and physical storage. Based on stakeholder interviews, this legacy process has critical deficiencies: only **20-30% of found items are successfully claimed**, there is no visual documentation to verify ownership, service is limited to office hours (7 AM - 9 PM, weekdays), and SID personnel dedicate significant time managing inquiries that divert resources from core security functions. During peak periods such as campus events and symposiums, the workload becomes overwhelming, with SID staff reporting that **"most of our time is spent on this, and we are not able to do anything else,"** severely compromising primary security responsibilities.

ClaimIT addresses these challenges through a centralized digital platform accessible to the campus community of over 12,000 students, faculty, and staff. The system features photo-based item documentation, real-time search and filtering, secure in-app messaging, automated notifications, QR code generation for inventory management, and a comprehensive administrative dashboard. Critically, based on SID recommendations, the system supports both **centralized claims** (items surrendered to SID) and **peer-to-peer claims** (direct coordination between finders and owners), providing flexibility while reducing administrative burden.

Following ICTC's technical guidance, ClaimIT is architected as a **responsive web application** rather than a native mobile app, ensuring seamless integration with the university's existing **SAML-based Single Sign-On (SSO)** infrastructure backed by Active Directory. For the prototype phase, the system leverages **Google Firebase** for rapid development, with the understanding that production deployment will transition to the university's internal SQL database infrastructure and hosting environment to maintain data governance and policy enforcement consistency.

The primary project objectives are to: (1) document comprehensive system requirements validated by key stakeholders, (2) develop a functional prototype demonstrating core features, (3) design workflows capable of increasing the item return rate from 20-30% to over 60%, and (4) establish a foundation for future full-scale implementation. This SRS provides detailed specifications for requirements, architecture, data models, and user workflows that will guide prototype development and serve as a blueprint for production deployment.

1. # **Introduction**

   1. ## **Purpose**

The purpose of this Software Requirements Specification (SRS) document is to comprehensively define the functional and non-functional requirements for **ClaimIT**, a Progressive Web Application (PWA) for lost and found management, developed by third-year BSIT students as part of the **ISY108 Requirements Engineering course** at MSU-IIT.

This document serves multiple critical functions:

- **Development Blueprint** – Provides detailed specifications to guide the design, development, and testing of the ClaimIT prototype, ensuring all required functionalities are precisely defined and understood by the project team.

- **Stakeholder Alignment** – Acts as a communication bridge between developers and key stakeholders (Security Intelligence Division, Information and Communication Technology Center, students, and faculty), ensuring shared understanding of system capabilities and constraints.

- **Requirements Validation** – Documents requirements derived from structured interviews with SID and ICTC personnel, ensuring the system addresses real operational needs rather than assumed requirements.

- **Future Implementation Foundation** – Establishes a comprehensive technical foundation that can guide subsequent full-scale production deployment beyond the prototype phase.

Version 1.0 of ClaimIT focuses on implementing core functionalities necessary for a fully operational prototype:

- **SAML-based SSO Authentication** – Secure login integration with university Active Directory, automatically assigning role-based permissions (Student, Faculty, Staff, SID Admin).

- **Dual-Mode Item Reporting** – Flexible posting of lost or found items with photo documentation, supporting both centralized (SID-managed) and peer-to-peer (direct finder-to-owner) coordination models.

- **Advanced Search and Filtering** – Multi-criteria search enabling users to locate items by category, location, date range, and status.

- **Secure Claims Management** – Structured workflow for submitting, reviewing, and approving claims, with mandatory verification procedures to prevent fraudulent claims.

- **Privacy-Compliant Messaging** – In-app communication system that protects user contact information while facilitating coordination between parties.

- **Administrative Dashboard** – Comprehensive management interface for SID personnel to moderate posts, verify claims, track statistics, and manage item lifecycle from report to disposal.

- **QR Code Integration** – Automated generation of unique QR codes for physical item tracking and expedited verification at the SID office.

ClaimIT replaces the existing manual, paper-based process with a centralized, accessible digital platform that enhances efficiency, transparency, and accountability while reducing administrative burden on security personnel.

1. ## **Intended Audience and Reading Suggestions**

This document has been prepared for a diverse group of stakeholders, each with specific interests and informational needs:

- **Student Developers & Testers (Primary Team):** Perform a comprehensive reading of the entire document. Focus particularly on Sections 4-8, which contain technical specifications, data models, use cases, and non-functional requirements essential for prototype implementation. Review Appendix B to understand stakeholder requirements directly from interview transcripts.

- **Project Managers & Faculty Advisors:** Concentrate on Sections 1-3 and the Appendices to understand project scope, objectives, methodology, timeline (Gantt Chart), and resource requirements. Review the Work Breakdown Structure (Appendix C) for detailed task allocation and milestone tracking.

- **Security Intelligence Division (SID) Personnel:** Review Sections 2, 4, 7, and 8 to understand:

  - How the system addresses current operational pain points (Section 2.1-2.2)
  - Administrative workflows and claim verification procedures (Sections 4-5)
  - Dashboard capabilities and item management features (Section 7)
  - Security and data privacy implementations (Section 8.3)

- **Information and Communication Technology Center (ICTC):** Focus on Sections 3, 6, and 8 to evaluate:

  - System architecture and integration with existing university infrastructure (Section 3.2)
  - Database design and data models (Section 6)
  - Security requirements, authentication mechanisms, and compliance with university IT policies (Section 8)
  - Transition plan from Firebase prototype to production SQL database environment

- **University Administration & End Users (Students/Faculty):** Review Sections 1, 2, and 7.1 for a high-level understanding of:
  - System purpose and anticipated benefits (Section 1.1)
  - Problems being solved and expected improvements (Section 2.2-2.4)
  - User-facing features and workflows (Section 7.1)

**Reading Sequence Recommendation:**

- For technical understanding: Sections 1 → 3 → 4 → 5 → 6 → 7 → 8
- For operational overview: Sections 1 → 2 → 7 → 4
- For policy compliance review: Sections 2 → 8 → Appendix B

1. # **Project Description**

ClaimIT is a Progressive Web Application (PWA) meticulously designed to modernize and streamline lost and found management for the MSU-IIT campus community of over 12,000 students, faculty, and staff. The system establishes a centralized, accessible digital platform that facilitates seamless reporting, searching, and recovery of lost personal items while significantly reducing administrative burden on the Security Intelligence Division (SID).

Following technical recommendations from the Information and Communication Technology Center (ICTC), ClaimIT is architected as a responsive web application rather than a native mobile app. This architectural decision ensures optimal integration with university infrastructure, eliminates app store deployment complexities, and provides immediate accessibility through standard web browsers on any device without requiring installation. The system prioritizes user convenience, operational transparency, and data security while maintaining full compatibility with existing campus authentication systems.

1. ## **Overview of the Current System**

Based on structured interviews with SID personnel conducted in November 2025, the current lost and found system at MSU-IIT operates as an entirely manual, paper-based process managed exclusively by the Security Intelligence Division. The operational workflow is as follows:

**Item Intake Process:**
When a found item is delivered to the SID office, security personnel manually record entry details in a physical logbook, including: finder's name, item description (for wallets: itemized contents), location where found, date, and time. Items are then stored in a dedicated cabinet in a back-room storage area, with each item tagged using adhesive tape notation indicating discovery location and date. Commonly received items include umbrellas, tumblers, cellphones, and wallets.

**Claim Verification Process:**
Individuals seeking lost items must physically visit the SID office during operational hours (7 AM - 9 PM, Monday-Friday). Officers conduct verbal interviews asking claimants to describe item characteristics (color, brand, contents), location, and approximate time of loss. If descriptions match recorded entries, officers request identification, record contact information (phone number), obtain signature, and log claim date/time before releasing the item. According to SID staff, processing time for in-person claims averages approximately 2 minutes when items are readily located.

**Critical Deficiencies:**

- **Extremely Low Recovery Rate:** SID personnel report that only **20-30% of found items are successfully claimed**, representing a 70-80% failure rate in the system's core mission of reuniting owners with belongings.

- **Zero Visual Documentation:** The complete absence of photographic evidence necessitates reliance on subjective verbal descriptions, creating ambiguity in item matching and increasing vulnerability to fraudulent claims. SID staff confirmed encountering dishonest claimants whose descriptions did not match recorded items.

- **Restricted Accessibility:** Service availability limited to office hours creates barriers for students with conflicting class schedules, evening students, or off-campus community members who cannot make multiple trips during business hours.

- **No Proactive Communication:** The system provides no mechanism to notify potential owners when their items are found. Recovery burden falls entirely on the individual, requiring repeated speculative visits to check for their belongings.

- **Excessive Administrative Burden:** During normal operations, SID dedicates considerable time to lost and found management, with staff noting that "only a few people come" on typical days. During peak periods—symposiums, concerts, orientations, or large gym events—staff report that **"most of our time is spent on this, and we are not able to do anything else,"** severely compromising primary security responsibilities.

- **No Historical Data or Fraud Prevention:** The paper system cannot track claim patterns, identify repeat fraudulent claimants, or generate analytics for operational improvement.

- **Storage Capacity Crisis:** Unclaimed items accumulate for extended periods. Following university policy, items remain available for one year, then receive a two-week extension with display in the hallway. Still-unclaimed items (including documented cases with contents valued at ₱18,000) are eventually transferred to the Knowledge and Technology Transfer Office (KTTO) for disaster relief donations. Staff indicate the system has improved recently due to increased awareness, but historically faced severe overcapacity issues.

- **Awareness Gap:** SID personnel noted that many students remain unaware of the lost and found service location and procedures, contributing to low claim rates and unnecessary item disposal.

  1.  ## **Problem Statement**

The manual lost and found system at MSU-IIT represents a critical operational failure that negatively impacts all stakeholders. Interview data reveals systemic problems across multiple dimensions:

**Catastrophic Recovery Failure:** With only 20-30% of found items successfully reunited with owners, the system fails its fundamental mission in 70-80% of cases, resulting in significant financial and sentimental losses for the campus community.

**Unsustainable Administrative Burden:** SID personnel report dedicating substantial time to lost and found management during normal periods. During campus events (symposiums, concerts, orientations), workload becomes overwhelming, with staff stating that **"most of our time is spent on this, and we are not able to do anything else."** This misallocation of security resources compromises campus safety while failing to achieve acceptable recovery outcomes.

**Systemic Communication Breakdown:** The absence of proactive notification mechanisms forces students to make repeated speculative visits to the SID office. Combined with restricted office hours (7 AM - 9 PM weekdays), this creates insurmountable barriers for students with class conflicts, part-time employment, or off-campus residences.

**Verification Vulnerability:** Reliance on verbal descriptions without photographic evidence creates ambiguity in item matching and vulnerability to fraud. SID confirmed encountering dishonest claimants attempting to claim items that don't belong to them, with no systematic method to verify ownership beyond subjective interview assessment.

**Awareness and Accessibility Crisis:** Many students remain unaware of the lost and found service's existence or location, contributing directly to low recovery rates and unnecessary item disposal.

**Data Blindness:** The paper-based system provides no capacity for trend analysis, fraud pattern detection, or operational improvement metrics. Administrators cannot identify high-loss locations, peak loss periods, or optimize procedures based on historical data.

**Storage and Disposal Challenges:** Unclaimed items accumulate for over a year before disposal, creating storage capacity issues and administrative overhead for extension periods, public displays, and eventual transfer to KTTO for donation.

The cumulative effect is a system that simultaneously fails users seeking to recover belongings, overwhelms security personnel with non-core responsibilities, wastes university resources on ineffective processes, and requires eventual disposal of valuable items that could have been returned with proper infrastructure.

There exists an urgent and documented need for a digital solution that provides 24/7 accessibility, photo-based verification, automated notifications, fraud prevention capabilities, and analytics-driven operational improvement while drastically reducing administrative burden on security personnel.

1. ## **Objectives**

   1. ### **General Objective**

To design, document, and develop a high-fidelity, functional prototype of a centralized, mobile-first digital platform that effectively demonstrates a modernized lost and found process for MSU-IIT.

2. ### **Specific Objective**

- To produce a comprehensive SRS document (this document) that serves as a blueprint for a potential full-scale implementation.
- To develop a functional prototype that demonstrates the core functionalities of item reporting (with photos), searching, and a simulated claims management workflow.
- To design a system architecture that, if fully implemented, would be capable of increasing the item return success rate from 35% to over 60%.
- To model a user workflow within the prototype that illustrates a path to reducing the average claim processing time to under 24 hours.
- To demonstrate a secure, role-based system that integrates with the university's central LDAP authentication service for login.
- To create a proof-of-concept for an administrative dashboard with analytics to showcase how trends could be tracked and system effectiveness could be measured in a live environment.

1. To develop a functional prototype that demonstrates key features, including item reporting with photos, searching, and a simulated claim management workflow.
2. To design a scalable system architecture capable of improving the item return success rate from 35% to an expected target of over 60% when fully deployed.
3. To evaluate the prototype’s usability, functionality, and performance through user testing and stakeholder feedback, ensuring alignment with institutional needs and overall system effectiveness.

   1. ## **Significance of the System**

ClaimIT addresses documented, stakeholder-validated problems with measurable benefits across all user groups:

**For Students and Faculty:**

- **Eliminates Access Barriers:** 24/7 accessibility removes scheduling conflicts and repeated physical visits, addressing the primary complaint that many students cannot reach SID during office hours or are unaware of the service.
- **Accelerates Recovery:** Photo-based searching and automated match notifications reduce time from item loss to recovery from days/weeks to potentially hours.
- **Reduces Financial/Sentimental Loss:** Increasing recovery rates from 20-30% to 60%+ means students are three times more likely to recover valuable or irreplaceable items.
- **Provides Transparency:** Real-time status tracking and claim history eliminates uncertainty about whether items have been found or claims are being processed.
- **Enables Flexible Coordination:** Peer-to-peer claim option (explicitly approved by SID) allows finders and owners to coordinate directly when convenient, bypassing office visit requirements.

**For Security Intelligence Division:**

- **Drastically Reduces Workload:** Automation of search, matching, and notification processes reclaims substantial time for core security responsibilities rather than administrative tasks, particularly during peak periods when staff report most of their time is currently consumed by lost and found management.
- **Prevents Fraud:** Photo documentation, claim history tracking, and structured verification workflows address documented problems with dishonest claimants attempting to claim items that aren't theirs.
- **Improves Service Quality:** Despite reduced time investment, SID can deliver superior service through systematic processes, complete records, and data-driven insights.
- **Eliminates Storage Backlog:** Higher recovery rates reduce unclaimed item accumulation, storage capacity pressure, and administrative burden of annual disposal processes.
- **Enables Shift Coordination:** Digital records eliminate information loss between shifts and ensure all personnel have complete item histories without manual turnover procedures.
- **Provides Accountability:** Comprehensive audit logs document all actions, protecting personnel and institution from disputes or liability claims.

**For ICTC and University Administration:**

- **Validates Technical Architecture:** Prototype demonstrates feasibility of SAML SSO integration, responsive web design, and Firebase-to-SQL migration path specified by ICTC.
- **Provides Low-Risk Evaluation:** Functional prototype allows thorough testing and refinement before committing resources to production deployment and infrastructure.
- **Establishes Replication Template:** Successful design creates blueprint for digitizing other manual campus services (room reservations, equipment checkout, facility requests).
- **Demonstrates IT Governance:** Implementation of university data privacy policies, security requirements, and integration standards validates institutional technical standards.
- **Supports Institutional Reputation:** Modernized service reinforces MSU-IIT's position as a technologically progressive institution committed to student experience improvement.

**Broader Impact:**

- **Regional Model:** As one of the first comprehensive lost and found digitization projects in Philippine universities, ClaimIT can serve as a proven reference implementation for other institutions facing identical challenges.
- **Academic Contribution:** Comprehensive SRS documentation based on structured stakeholder interviews provides educational value for future Requirements Engineering courses.
- **Student Portfolio Value:** Team members gain demonstrable experience in full-cycle software development, stakeholder engagement, and production-grade system design.

  1. ## **Scope and Limitation**

**Scope:**

- **Primary Deliverables:** This comprehensive SRS document and a fully functional prototype demonstrating all core system capabilities.

- **Platform Architecture:** Progressive Web Application (PWA) accessible via standard web browsers on desktop and mobile devices, eliminating app store deployment requirements per ICTC recommendation.

- **Full Lifecycle Demonstration:** Complete item workflow from initial reporting through searching, matching, claiming (both centralized and peer-to-peer modes), verification, and final resolution or disposal.

- **User Roles and Permissions:** Four distinct roles with differentiated access levels:

  - **Students:** Report lost/found items, search database, submit claims, message other users, opt-in contact information sharing.
  - **Faculty/Staff:** All student capabilities plus ability to mark items as "turned in to security."
  - **SID Admin:** Full administrative dashboard access including item moderation, claim approval/denial, user messaging, analytics viewing, and system configuration.
  - **Guest/Visitor:** Limited read-only access for searching public item listings without authentication.

- **Core Functional Features:**

  - SAML-based SSO authentication integrated with Active Directory
  - Photo upload capability (up to 5 images per item) with file type and size restrictions
  - Advanced search with multi-criteria filtering (category, location, date range, status)
  - Dual-mode claims process (centralized SID management and peer-to-peer coordination)
  - Privacy-protected in-app messaging system
  - Automated notification system (push notifications and email alerts)
  - QR code generation for physical item tracking
  - Comprehensive administrative dashboard with analytics and reporting
  - Audit logging for all critical actions
  - Sensitive data encryption as per ICTC specifications

- **Technical Integration:** Authentication integration with university Active Directory via SAML SSO protocol, with role information automatically derived from institutional records.

- **Compliance Requirements:** Implementation of Philippine Data Privacy Act (RA 10173) requirements and university IT security policies including data encryption, access controls, and audit trails.

**Limitations:**

- **Prototype Status:** The deliverable is a **fully functional prototype** intended for evaluation, testing, and refinement. It is not a production-deployed system with formal university support commitments.

- **Backend Infrastructure - Prototype Phase:** The prototype utilizes **Google Firebase** (Authentication, Firestore, Storage, Cloud Messaging) operating within free tier limits for rapid development and evaluation.

- **Production Deployment Transition:** Per ICTC specifications, full production deployment will require migration from Firebase to **university-hosted SQL database infrastructure**. This migration is outside the current project scope but the system is architected to facilitate this transition.

- **Notification Implementation:** While the notification framework is fully implemented, actual push notification delivery and email sending may be simulated or limited during prototype phase due to Firebase free tier constraints and university email system integration requirements.

- **App Store Distribution:** The PWA is accessible via web browsers and does not require (or include) deployment to Google Play Store or Apple App Store. Users access via URL, with optional "Add to Home Screen" capability for mobile devices.

- **Initial Data Migration:** The system starts with an empty database. Migration of historical lost and found records from SID's paper logbooks is outside project scope but can be performed post-deployment if required.

- **Scope Exclusions:** The following are explicitly out of scope for this phase:

  - Long-term maintenance and user support beyond initial deployment
  - Hardware procurement (servers, storage, networking equipment)
  - Formal user training program development
  - Integration with additional university systems beyond Active Directory
  - Multi-campus or multi-institution deployment
  - Advanced AI-powered image recognition for automatic item matching
  - Mobile hardware (e.g., handheld scanners, dedicated kiosks)

- **ICTC Deployment Responsibility:** Final production deployment, server configuration, database setup, and integration with production Active Directory environment are ICTC responsibilities following successful prototype validation.

  1. ## **Benchmark Systems**

The following systems were analyzed to identify best practices, understand existing solutions in the lost and found domain, and determine areas where ClaimIT can provide distinct advantages tailored to the MSU-IIT campus environment:

1.  [**RepoApp:**](https://www.repoapp.com/lost-found-software-universities/) Enterprise software targeted at universities that focuses on managing lost and found inventories with comprehensive categorization and secure centralized databases. Its strengths include robust search functionality, detailed item histories, and reporting tools that improve storage management and accountability. It is relevant as a benchmark for its ability to digitize and streamline lost and found processes in educational environments. ClaimIT differs by adding dual coordination modes (centralized and peer-to-peer), advanced photo-based verification, real-time notifications, and integration with university SSO systems, providing greater usability and fraud prevention.

2.  [**List Perfectly:**](https://listperfectly.com/selling/list-perfectlys-inventory-management-system/) An all-in-one inventory management platform designed primarily for online sellers, offering extensive cross-listing to multiple marketplaces and flexible inventory editing. Its strengths lie in its inventory centralization, mobile-friendly interface, and powerful analytics that optimize listing management. It is a useful benchmark for managing and tracking numerous inventory items efficiently. ClaimIT improves upon this by focusing specifically on lost and found item management in a campus context, with features like QR code tagging, secure claims workflows, and role-based access integrated with institutional authentication.

3.  [**Chargerback:**](https://www.chargerback.com/) An AI-powered lost and found system widely used in hospitality, providing web-based inventory tracking and automating guest interactions to streamline item recovery. Its strengths include ease of use for both employees and customers, automation of communications, and standardized lost item handling processes. It is relevant as a benchmark due to its successful digital transformation of a traditionally manual industry. ClaimIT adapts this approach for higher education, emphasizing community engagement, peer-to-peer coordination, and integration with campus security workflows.

4.  [**Lost and Found Software:**](https://www.lostandfoundsoftware.com/) An AI-driven platform that automates lost item matching and management to reduce organizational workload and improve recovery rates. Its strengths stem from AI-powered matching algorithms and a user interface that allows editing and cancellation of lost item reports. This system is a good benchmark for its high level of automation and scalability. ClaimIT builds on this by adding photo documentation restrictions, proactive notifications, and a comprehensive admin dashboard tailored to university policies and security needs.

5.  [**Campus Trace:**](https://irojournals.com/tcsst/article/view/6/2/6) A lost and found application specifically designed for academic institutions, enhancing reporting and collaboration between finders and owners. Its strengths include user-friendly design, privacy protection measures, admin authentication for claims, and fostering community responsibility. It benchmarks educational use cases focused on social engagement and ease of item recovery. ClaimIT advances this by integrating with university SSO, employing advanced search filters, QR code physical tagging, and detailed claims verification processes to increase recovery rates and reduce administrative burden.

6.  [**USTP Panaon System:**](https://zenodo.org/records/15045175) A QR code-based lost and found solution implemented in a Philippine academic campus, focusing on efficient item retrieval via mobile/web applications. Its strengths include leveraging QR technology for quick identification and tracking, iterative user-centered development, and positive user evaluation. It serves as a benchmark for innovative integration of mobile tech in campus environments. ClaimIT improves by incorporating dual coordination (peer-to-peer and centralized claims), photo-based verification, and role-based access control linked to institutional directories.

7.  [**Lost and Found Networks:**](https://lostandfoundnetworks.com/) A global, public reporting platform allowing 24/7 item loss and found reporting published on a public domain and social media networks for wide exposure. Its strengths are global reach, public accessibility, and integration with major social networks for maximum visibility. It is relevant as a benchmark for public transparency and community involvement. ClaimIT differs by offering a closed, secure campus community system with privacy controls, detailed administrative tools, and seamless integration with university authentication and notification systems.

8.  [**AUFound (AU):**](https://www.studocu.com/ph/document/university-of-caloocan-city/bachelor-of-science-information-technology/383-jajajajajajaj/103846352) A university-specific lost and found retrieval system focusing on tracking missing items through web-based databases integrated within the campus environment. Its strengths are in localized tracking, targeted communication, and structured reporting forms tailored for academic settings. It benchmarks university-centric retrieval with focus on usability for students and staff. ClaimIT improves on this by providing a progressive web platform accessible on multiple devices, photo documentation, QR code tracking, proactive push notifications, and a dual-claims workflow including SID moderation.

9.  [**BOUNTE:**](https://www.bounte.net/home-2/) An AI image recognition platform designed for commercial venues like airports and hotels to identify and manage lost items efficiently. Its strengths lie in high accuracy image recognition technology, improving speed and accuracy of claims. It benchmarks commercial-scale AI-driven lost item processing. ClaimIT employs photo-based manual verification and focuses on privacy and controlled access rather than full AI image recognition, tailored for campus environments with administrative control and fraud prevention measures.

10. [**Pixit:**](https://www.pixithq.com/) A picture-based workflow management tool that simplifies lost and found tracking for businesses by enabling image-centric item management and communications. Its strengths include visual item documentation and streamlined workflows for customers and staff. It is a good benchmark for image-focused item handling in customer service environments. ClaimIT extends these ideas into an academic setting by combining photo documentation with QR codes, secure messaging, and role-based administration coupled with university Single Sign-On.

11. [**MSU-Sulu Lost and Found Management System:**](https://www.studocu.com/ph/document/mindanao-state-university-sulu/bs-information-technology/capstone-project-1-lost-and-found-monitoring-and-management-system-and-application/120113218) A campus-wide digital lost and found management tool developed for Mindanao State University-Sulu, providing reporting, tracking, and reclaiming functionalities. Its strengths include localized deployment for campus needs, digital item listing, and user interaction for claims. It benchmarks practical implementation in a university context within the Philippines. ClaimIT advances this concept with a fully integrated Progressive Web App, enhanced search and filtering, automated notifications, claims verification workflows, QR code inventory control, and centralized administrative dashboards aligning with modern university IT policies.

        1. ## **Salient Features of the System**

    Based on stakeholder interviews with SID and ICTC, ClaimIT incorporates the following key features validated against documented operational requirements:

- **Dual-Mode Item Reporting:** Users can post lost or found items with comprehensive details (title, description, category, location, date/time) and up to 5 photos. Critically, following SID approval, the system supports **both centralized and peer-to-peer coordination**: items can be marked as "turned in to security" for SID management, or finders can coordinate directly with owners to reduce administrative burden.

- **Privacy-Compliant Photo Documentation:** Automatic photo upload with security restrictions (file type validation, size limits) per ICTC specifications. Following SID policy, the system enforces restrictions on sensitive content: for wallets, users photograph only the exterior, never contents, preventing exposure of cash amounts or identification documents.

- **Advanced Multi-Criteria Search:** Powerful search engine with filters for category (electronics, clothing, IDs, wallets, books, tumblers, umbrellas), location (specific buildings/areas), date range, and status. Addresses the awareness gap by making all items instantly discoverable rather than requiring physical office visits and manual logbook searches.

- **Structured Anti-Fraud Claims Management:** Multi-step verification workflow addressing SID's documented problems with dishonest claimants:

  - Mandatory proof of ownership descriptions
  - Photo-based verification before claim approval
  - Complete claim history tracking per user
  - Administrative review before item release
  - Complete audit trail of all claim attempts

- **Automated Proactive Notifications:** Push notifications and email alerts for:

  - New items matching lost item descriptions
  - Claim status changes (submitted, approved, denied)
  - Messages from finders, owners, or SID
  - Reminders for pending item pickup

- **Privacy-Protected In-App Messaging:** Secure messaging system enabling coordination between finders and owners without exposing phone numbers or email addresses, directly addressing SID's explicit request that personal contact information "should not be included... it's not really necessary."

- **SAML SSO with Active Directory Integration:** Seamless authentication using university credentials per ICTC architectural requirements. Role-based permissions (Student, Faculty, Staff, SID Admin) automatically derived from institutional records. No separate account creation required.

- **QR Code Physical Tracking:** Automatic generation of unique QR codes for each registered item, enabling:

  - Rapid item lookup via mobile scanning
  - Physical tag printing for items stored at SID office
  - Verification of item authenticity during claim pickup

- **Comprehensive Administrative Dashboard:** SID-specific interface providing:

  - Real-time statistics (total items, claims pending, recovery rate)
  - Category and location analytics for trend identification
  - Item moderation tools (edit, archive, delete)
  - Claim approval workflow management
  - User communication interface
  - Audit log viewer
  - Bulk operations for item lifecycle management (archiving, disposal scheduling)

- **24/7 Accessibility:** Web-based access eliminates office hour constraints (current 7 AM - 9 PM, weekdays only), addressing barriers for students with class conflicts or off-campus residences.

- **Sensitive Data Encryption:** Per ICTC security requirements, encryption of student ID numbers, passwords, authentication tokens, and other sensitive personal information at rest and in transit, with appropriate access controls ensuring SID cannot view unnecessary personal details.

  1. ## **Gantt Chart**

The ClaimIT project follows a structured timeline aligned with the prototyping methodology, with major phases distributed across the academic term to ensure adequate time for stakeholder feedback and iterative refinement.

| **Phase** | **Major Activities**                                                                                                                                                                                                                             | **Duration** | **Start Date** | **Target Completion** | **Status**  |
| :-------: | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----------: | :------------: | :-------------------: | :---------: |
|   **1**   | **Requirements Gathering** <br/>• Stakeholder identification<br/>• Interview protocol development<br/>• SID interview<br/>• ICTC interview<br/>• Requirements documentation                                                                      |   3 weeks    |     Week 1     |        Week 3         |  Completed  |
|   **2**   | **SRS Documentation** <br/>• Document structure setup<br/>• Section drafting<br/>• Stakeholder review cycles<br/>• Final SRS v1.0                                                                                                                |   3 weeks    |     Week 3     |        Week 6         | In Progress |
|   **3**   | **System Design** <br/>• Database schema design (ERD, Class Diagrams)<br/>• Architecture diagrams (Component, Context, Package)<br/>• UI/UX wireframes and mockups<br/>• Use case modeling<br/>• Sequence/collaboration diagrams                 |   4 weeks    |     Week 5     |        Week 9         |   Pending   |
|   **4**   | **Prototype Development Phase 1** <br/>• Development environment setup<br/>• Firebase project configuration<br/>• SAML SSO integration (test environment)<br/>• User authentication and role management<br/>• Basic item reporting functionality |   3 weeks    |     Week 7     |        Week 10        |   Pending   |
|   **5**   | **Prototype Development Phase 2** <br/>• Search and filter implementation<br/>• Photo upload and storage<br/>• QR code generation<br/>• In-app messaging system<br/>• Notification framework                                                     |   3 weeks    |    Week 10     |        Week 13        | ⏳ Pending  |
|   **6**   | **Prototype Development Phase 3** <br/>• Claims management workflow<br/>• Administrative dashboard<br/>• Analytics and reporting<br/>• Audit logging<br/>• Security hardening                                                                    |   3 weeks    |    Week 13     |        Week 16        | ⏳ Pending  |
|   **7**   | **Testing and Refinement** <br/>• Internal testing and bug fixes<br/>• User Acceptance Testing with SID<br/>• Student user testing<br/>• Performance optimization<br/>• UI/UX refinements based on feedback                                      |   2 weeks    |    Week 16     |        Week 18        |   Pending   |
|   **8**   | **Documentation and Deployment** <br/>• User documentation<br/>• Technical documentation<br/>• Prototype deployment<br/>• Stakeholder demonstrations<br/>• Final report and handover                                                             |   2 weeks    |    Week 18     |        Week 20        |   Pending   |

**Key Milestones:**

- **M1 (Week 3):** Requirements Validation - All stakeholder interviews completed and documented
- **M2 (Week 6):** SRS Approval - Comprehensive SRS document approved by faculty advisor and stakeholders
- **M3 (Week 10):** Design Review - All UML diagrams and system architecture approved
- **M4 (Week 13):** Alpha Prototype - Core functionality operational for initial testing
- **M5 (Week 16):** Beta Prototype - Feature-complete system ready for UAT
- **M6 (Week 20):** Final Delivery - Validated prototype and complete documentation

**Critical Dependencies:**

- ICTC must provide test SAML SSO credentials by Week 7
- SID availability for UAT sessions in Week 17
- Faculty advisor approval gates at Weeks 6, 10, and 18

**Risk Mitigation:**

- Buffer time built into Phases 4-6 for unexpected technical challenges
- Parallel development of independent modules where possible
- Weekly progress check-ins with faculty advisor
- Bi-weekly stakeholder status updates

1. # **Methodology**

This project adopts the **Prototyping Methodology**, specifically the **Evolutionary Prototyping** approach. This methodology is optimally suited for ClaimIT due to several critical factors identified during requirements gathering:

**Rationale for Methodology Selection:**

1. **Stakeholder Clarity on End Goals:** SID and ICTC interviews revealed clear, specific requirements derived from documented pain points rather than abstract needs. The current manual system provides a concrete baseline for comparison, making evolutionary refinement more effective than exploratory prototyping.

2. **User-Centric Application Domain:** As a public-facing system serving 12,000+ diverse users (students, faculty, staff, visitors), usability is paramount. Iterative refinement based on actual user feedback ensures the final product aligns with real-world usage patterns rather than theoretical designs.

3. **Technical Risk Management:** Integration with university Active Directory and migration from Firebase to production SQL infrastructure represent significant technical challenges. Prototyping allows early validation of integration patterns and architecture feasibility before full-scale implementation.

4. **Stakeholder Engagement Requirements:** Both SID and ICTC expressed desire for hands-on evaluation before committing to full production deployment. The prototyping methodology inherently supports this through tangible, demonstrable increments at each phase.

### 3.1 Requirements Gathering

**Status: COMPLETED (November 2025)**

The requirements phase employed structured stakeholder interviews to elicit validated, documented needs:

**Stakeholder Engagement:**

- **Security Intelligence Division (SID):** In-depth interview focusing on current operational workflows, pain points, processing times, fraud experiences, storage procedures, and desired system capabilities. SID provided specific statistics (20-30% recovery rate), workload descriptions ("most of our time" during peak periods), and explicit policy requirements (photo restrictions for wallet contents, contact information privacy).

- **Information and Communication Technology Center (ICTC):** Technical architecture interview establishing integration requirements (SAML SSO with Active Directory), security specifications (data encryption, file upload restrictions), infrastructure preferences (web-based vs. mobile app, Firebase prototype with SQL production migration), and compliance requirements (Philippine Data Privacy Act).

**Documentation Outputs:**

- Complete interview transcripts (see Appendix B)
- Requirements conflict resolution document addressing contradictions between stakeholder inputs
- Validated requirements list forming the foundation of this SRS

**Key Requirement Themes Identified:**

- Accessibility (24/7 availability vs. current office hours limitation)
- Visual verification (photo documentation to address matching ambiguity)
- Proactive communication (automated notifications vs. current manual checking)
- Fraud prevention (structured verification vs. current interview-only approach)
- Administrative efficiency (automation to reduce time spent on lost and found management)
- Privacy protection (in-app messaging, controlled data access)
- Dual coordination modes (centralized and peer-to-peer options)

### 3.2 System Design

The design phase translates validated requirements into comprehensive architectural specifications and detailed interface models:

**Data Modeling:**

- **Entity-Relationship Diagram (ERD):** Defines database schema for Users, Items, Claims, Messages, Notifications, and Audit Logs entities with their relationships and cardinalities. Addresses ICTC's requirement for migration from Firebase (NoSQL) to production SQL database by designing normalized schema compatible with relational databases.

- **Class Diagram:** Object-oriented design representation showing system classes, attributes, methods, and inheritance relationships. Ensures clean separation of concerns and maintainable codebase structure.

**Architectural Design:**

- **Component Diagram:** Illustrates system modules (Authentication Module, Item Management Module, Claims Processing Module, Messaging Module, Notification Module, Admin Dashboard, QR Code Generator) and their inter-dependencies.

- **Context Diagram:** High-level view showing ClaimIT's boundaries and interactions with external systems (Active Directory/LDAP, University Email System, Firebase Services, Web Browsers).

- **Package Diagram:** Organizes code structure into logical packages (Frontend, Backend, Database Layer, External Integrations, Utilities) for modular development and maintenance.

**UI/UX Design:**

- **Wireframes:** Low-fidelity sketches of all major screens (login, dashboard, item posting form, search results, item details, claims interface, messaging, admin panel) establishing layout and navigation flow.

- **High-Fidelity Mockups:** Detailed visual designs incorporating MSU-IIT branding, color schemes, typography, and responsive layouts for desktop, tablet, and mobile viewports.

- **Interaction Flow Diagrams:** User journey maps showing step-by-step navigation through primary workflows (reporting lost item, searching for found items, submitting claims, admin approval process).

**Security Architecture:**

- Data encryption specifications for sensitive fields (ID numbers, passwords, tokens)
- Role-based access control (RBAC) matrix defining permissions for each user role
- API security design (authentication tokens, rate limiting, input validation)
- Audit logging specifications for compliance and accountability

### 3.3 Prototype Development

**Technology Stack:**

_Frontend:_

- **Framework:** React.js with responsive design principles for Progressive Web App
- **UI Library:** Material-UI (MUI) or similar component library for consistent interface
- **State Management:** Redux or Context API for application state
- **Routing:** React Router for single-page application navigation
- **QR Code:** qrcode.react library for QR code generation

_Backend (Prototype Phase):_

- **Platform:** Google Firebase (free tier)
  - **Authentication:** Firebase Authentication with custom SAML provider integration
  - **Database:** Cloud Firestore (NoSQL) for real-time data synchronization
  - **Storage:** Firebase Storage for photo uploads
  - **Hosting:** Firebase Hosting for PWA deployment
  - **Cloud Messaging:** Firebase Cloud Messaging (FCM) for push notifications

_Production Transition Architecture:_

- **Database:** PostgreSQL or MySQL (university-hosted)
- **Backend:** Node.js/Express API server
- **Authentication:** Direct SAML integration with university Active Directory
- **Storage:** University file storage infrastructure
- **Email:** University SMTP server integration

**Development Phases:**

_Phase 1 - Core Infrastructure:_

- Firebase project setup and configuration
- SAML SSO integration (test environment with ICTC support)
- User authentication flow implementation
- Role-based access control system
- Basic item CRUD operations (Create, Read, Update, Delete)

_Phase 2 - User Features:_

- Advanced search and filtering engine
- Multi-photo upload with validation (file type, size limits)
- Category and location management
- Date/time selection interfaces
- Responsive layout for all screen sizes

_Phase 3 - Communication & Verification:_

- In-app messaging system (Firestore real-time updates)
- Notification framework implementation
- QR code automatic generation and display
- Email notification templates

_Phase 4 - Administrative Functions:_

- Admin dashboard development
- Item moderation interface (edit, archive, delete)
- Claims approval workflow
- Analytics and reporting views (charts, statistics)
- Audit log viewer
- Bulk operations interface

_Phase 5 - Security & Polish:_

- Data encryption implementation
- Input validation and sanitization
- XSS and SQL injection prevention
- Rate limiting and abuse prevention
- Performance optimization
- Browser compatibility testing
- Accessibility (WCAG) compliance review

### 3.4 User Acceptance Testing (UAT)

**Testing Methodology:**

_Test Group Composition:_

- **SID Personnel (3-5 participants):** Administrators who will manage the system daily
- **Students (15-20 participants):** Representative sample across different colleges and year levels
- **Faculty/Staff (5-8 participants):** Regular users with varying technical proficiency

_Testing Scenarios:_

_For Regular Users:_

1. **Lost Item Reporting:** Post a lost item with photos and search for matches
2. **Found Item Reporting:** Report finding an item, decide between SID turnover vs. peer-to-peer
3. **Search and Discovery:** Use filters to locate specific item types and categories
4. **Claim Submission:** Submit a claim with proof of ownership description
5. **Messaging:** Communicate with item finder or SID via in-app chat
6. **Status Tracking:** Monitor claim status and receive notifications

_For SID Administrators:_

1. **Item Moderation:** Review newly posted items, edit details, approve/reject
2. **Claim Processing:** Evaluate claims, request additional information, approve/deny
3. **User Communication:** Send messages to claimants, respond to inquiries
4. **Analytics Review:** Access dashboard statistics, generate reports
5. **System Configuration:** Manage categories, locations, system settings
6. **Audit Trail Review:** Examine activity logs for specific items or users

_Data Collection Methods:_

- **Quantitative Metrics:**

  - Task completion rates and time-on-task measurements
  - Error rates and recovery patterns
  - Navigation path analysis
  - Feature usage frequency
  - System Usability Scale (SUS) scores

- **Qualitative Feedback:**
  - Post-task interviews
  - Think-aloud protocol observations
  - Written surveys with open-ended questions
  - Focus group discussions
  - Overall satisfaction surveys

_Success Criteria:_

- Minimum 80% task completion rate for all primary workflows
- Average task completion time under 3 minutes for simple operations
- SUS score above 70 (acceptable usability)
- No critical severity issues preventing core functionality
- Positive feedback from at least 75% of participants

### 3.5 Iterative Refinement

Following UAT, the prototype undergoes structured refinement cycles:

**Issue Triage Process:**

- **Critical (P0):** System-breaking bugs, security vulnerabilities - immediate fix required
- **High (P1):** Major functionality failures, significant usability problems - fix before next iteration
- **Medium (P2):** Minor bugs, UI inconsistencies - fix if time permits
- **Low (P3):** Enhancement requests, nice-to-have features - document for future versions

**Refinement Activities:**

1. **Bug Resolution:** Systematic addressing of all identified defects based on priority
2. **UI/UX Improvements:** Layout adjustments, color contrast fixes, button placements, error message clarity
3. **Performance Optimization:** Query optimization, image compression, caching strategies
4. **Workflow Streamlining:** Reducing steps in multi-stage processes based on user feedback
5. **Accessibility Enhancements:** Screen reader compatibility, keyboard navigation, color blind-friendly palettes

**Validation Cycles:**

- Fix implementation → Internal testing → Stakeholder review → Approval gate
- Repeat until all P0 and P1 issues resolved and stakeholder satisfaction achieved

### 3.6 Delivery and Handover

**Project Culmination Activities:**

_Deliverables:_

1. **Functional Prototype:** Fully operational ClaimIT PWA hosted on accessible URL
2. **Software Requirements Specification:** This comprehensive document (final version)
3. **Technical Documentation:**
   - System architecture documentation
   - Database schema with entity descriptions
   - API documentation (if applicable)
   - Deployment guides
   - Configuration guides
4. **User Documentation:**
   - End-user manual with screenshots
   - Administrator manual
   - Quick-start guides
   - FAQ document
5. **Source Code Repository:**
   - Complete codebase with version control history
   - README with setup instructions
   - Commented code for maintainability
6. **Testing Documentation:**
   - UAT results summary
   - Test case documentation
   - Known issues and limitations log

_Handover Process:_

1. **Stakeholder Demonstrations:**

   - Live demo for SID personnel (2-hour comprehensive session)
   - Technical walkthrough for ICTC (focus on architecture and deployment)
   - Overview for university administration (30-minute presentation)

2. **Knowledge Transfer:**

   - Training session for SID administrators
   - Documentation handover with Q&A
   - Q&A sessions for clarification

3. **Access Provisioning:**
   - Admin accounts for SID personnel
   - Source code repository access for ICTC
   - Documentation access for all stakeholders

**Out-of-Scope (Post-Handover):**

- Production deployment to university servers (ICTC responsibility)
- Firebase-to-SQL database migration (ICTC responsibility with developer consultation)
- Ongoing bug fixes and feature enhancements (separate maintenance contract)
- User training programs (university responsibility)
- Help desk support (university responsibility)

**Success Evaluation Criteria:**

- Complete delivery of all specified deliverables
- Stakeholder acceptance of prototype functionality
- Documented validation that system meets 80%+ of specified requirements
- ICTC confirmation of technical feasibility for production deployment
- Faculty advisor approval for academic project completion

1. # **Requirements Definition**

### Introduction

This section provides comprehensive documentation of all functional and non-functional requirements for the ClaimIT system, derived directly from stakeholder interviews with the Security Intelligence Division (SID) and Information and Communication Technology Center (ICTC). Requirements are organized systematically to ensure traceability from stakeholder needs through design, implementation, and testing phases.

The requirements reflect validated operational needs identified through structured interviews, addressing specific documented deficiencies in the current manual system. Each requirement is tagged with its source (SID, ICTC, or both) to maintain clear accountability and facilitate stakeholder validation.

**Requirement Categories:**

- **Functional Requirements:** Specific behaviors and capabilities the system must provide
- **Non-Functional Requirements:** Quality attributes (performance, security, usability)
- **Constraint Requirements:** Technical or operational limitations that must be respected
- **Interface Requirements:** Integration points with external systems

All requirements are prioritized using the MoSCoW method:

- **Must Have:** Critical for minimal viable product
- **Should Have:** Important but system can function without them initially
- **Could Have:** Desirable enhancements if time/resources permit
- **Won't Have (this version):** Explicitly out of scope for v1.0

### 4.1 Requirements Traceability Matrix {#requirements-traceability-matrix}

The Requirements Traceability Matrix (RTM) establishes bidirectional traceability between stakeholder needs, system requirements, design elements, implementation components, and test cases. This ensures no requirement is overlooked and all implemented features can be traced back to validated stakeholder requests.

| **RTM ID**  | **Requirement Description**                                                                                                      |             **Type**             | **Priority** |  **Source**   | **Status** |      **Design Reference**      | **Test Case** |
| :---------: | :------------------------------------------------------------------------------------------------------------------------------- | :------------------------------: | :----------: | :-----------: | :--------: | :----------------------------: | :-----------: |
| **FR-001**  | System shall authenticate users via SAML SSO integrated with university Active Directory                                         |            Functional            |  Must Have   |     ICTC      |  Approved  | Section 6.3 (Context Diagram)  |    TC-001     |
| **FR-002**  | System shall automatically assign user roles (Student, Faculty, Staff, Admin) based on Active Directory attributes               |            Functional            |  Must Have   |     ICTC      |  Approved  | Section 5.1 (Use Case Diagram) |    TC-002     |
| **FR-003**  | Users shall be able to post lost items with title, description, category, location, date, and time                               |            Functional            |  Must Have   | SID, Students |  Approved  |   UC-1.1 (Report Lost Item)    |    TC-010     |
| **FR-004**  | Users shall be able to upload up to 5 photos per item (max 5MB each, JPEG/PNG only)                                              |            Functional            |  Must Have   |      SID      |  Approved  |      UC-1.1, Section 8.3       |    TC-011     |
| **FR-005**  | System shall enforce photo content restriction: wallet interiors must not be photographed, only exteriors                        |            Functional            |  Must Have   |      SID      |  Approved  |     Validation Rule VR-012     |    TC-012     |
| **FR-006**  | Users shall be able to report found items with all metadata fields from FR-003                                                   |            Functional            |  Must Have   |      SID      |  Approved  |   UC-1.2 (Report Found Item)   |    TC-013     |
| **FR-007**  | Users reporting found items shall indicate if item is "turned in to SID" or available for "peer-to-peer" coordination            |            Functional            |  Must Have   |      SID      |  Approved  |             UC-1.2             |    TC-014     |
| **FR-008**  | System shall provide advanced search with filters: category, location, date range, status, keywords                              |            Functional            |  Must Have   | SID, Students |  Approved  |     UC-2.1 (Search Items)      |    TC-020     |
| **FR-009**  | Search results shall display as cards showing: thumbnail, title, category, location, date posted, poster name (non-contact info) |            Functional            |  Must Have   |      SID      |  Approved  |    Section 7.2 (UI Mockups)    |    TC-021     |
| **FR-010**  | System shall provide detailed item view with full description, all photos, QR code, claim button, message button                 |            Functional            |  Must Have   |      SID      |  Approved  |   UC-2.2 (View Item Details)   |    TC-022     |
| **FR-011**  | Authenticated users shall be able to submit claims for found items                                                               |            Functional            |  Must Have   |      SID      |  Approved  |     UC-3.1 (Submit Claim)      |    TC-030     |
| **FR-012**  | Claim submission shall require: explanation/proof of ownership, contact preference                                               |            Functional            |  Must Have   |      SID      |  Approved  |             UC-3.1             |    TC-031     |
| **FR-013**  | SID Admin shall review all claims and approve/deny with reason documentation                                                     |            Functional            |  Must Have   |      SID      |  Approved  |     UC-3.2 (Process Claim)     |    TC-032     |
| **FR-014**  | System shall send notifications to claimant when: claim submitted, claim approved, claim denied, additional info requested       |            Functional            |  Must Have   |      SID      |  Approved  |  Section 7.1 (Notifications)   |    TC-033     |
| **FR-015**  | Users shall have in-app messaging capability with item posters and SID without exposing phone numbers/emails                     |            Functional            |  Must Have   |   SID, ICTC   |  Approved  |     UC-4.1 (Send Message)      |    TC-040     |
| **FR-016**  | System shall generate unique QR code for each posted item containing item ID and access URL                                      |            Functional            | Should Have  |      SID      |  Approved  |     Section 7.1 (QR Codes)     |    TC-050     |
| **FR-017**  | SID Admin shall have dashboard displaying: total items, claims pending, recovery rate, category breakdown, location heatmap      |            Functional            |  Must Have   |      SID      |  Approved  | Section 7.2 (Admin Dashboard)  |    TC-060     |
| **FR-018**  | SID Admin shall be able to: edit item details, archive items, delete items, send messages to users                               |            Functional            |  Must Have   |      SID      |  Approved  |    UC-5.1 (Moderate Items)     |    TC-061     |
| **FR-019**  | System shall automatically send notifications for: new item matching lost description, claim status changes                      |            Functional            | Should Have  |      SID      |  Approved  |      Notification Module       |    TC-070     |
| **FR-020**  | System shall log all critical actions (claims, edits, deletions) with timestamp, user, action type for audit trail               |            Functional            |  Must Have   |     ICTC      |  Approved  |  Section 6.1 (ERD - AuditLog)  |    TC-080     |
| **FR-021**  | Users shall optionally provide contact phone number; if provided, visible to item owner/finder after claim approval              |            Functional            |  Could Have  | SID, Students |  Approved  |             UC-1.1             |    TC-015     |
| **FR-022**  | System shall support guest/visitor browsing of found items without authentication                                                |            Functional            | Should Have  |      SID      |  Approved  |             UC-2.1             |    TC-023     |
| **FR-023**  | System shall mark items as "claimed" and archive after successful recovery                                                       |            Functional            |  Must Have   |      SID      |  Approved  |    UC-3.3 (Complete Claim)     |    TC-034     |
| **FR-024**  | System shall allow SID to schedule disposal dates for unclaimed items per university policy (1 year + 2 week extension)          |            Functional            | Should Have  |      SID      |  Approved  |   UC-5.2 (Manage Lifecycle)    |    TC-062     |
| **NFR-001** | System shall support 12,000+ concurrent registered users                                                                         |   Non-Functional (Performance)   |  Must Have   |     ICTC      |  Approved  |      Architecture Design       |    TC-100     |
| **NFR-002** | Page load time shall not exceed 3 seconds on standard campus Wi-Fi (my.iit network)                                              |   Non-Functional (Performance)   | Should Have  |     ICTC      |  Approved  |      Performance Testing       |    TC-101     |
| **NFR-003** | System shall encrypt sensitive data fields (ID numbers, passwords, tokens) using AES-256                                         |    Non-Functional (Security)     |  Must Have   |     ICTC      |  Approved  |          Section 8.3           |    TC-110     |
| **NFR-004** | System shall comply with Philippine Data Privacy Act (RA 10173) regarding personal data handling                                 |    Non-Functional (Security)     |  Must Have   |     ICTC      |  Approved  |          Section 8.3           |    TC-111     |
| **NFR-005** | File uploads shall be restricted to JPEG/PNG formats, max 5MB each, with server-side validation                                  |    Non-Functional (Security)     |  Must Have   |     ICTC      |  Approved  |         Upload Module          |    TC-112     |
| **NFR-006** | System shall implement rate limiting to prevent abuse (max 10 item posts per user per day)                                       |    Non-Functional (Security)     | Should Have  |     ICTC      |  Approved  |           API Layer            |    TC-113     |
| **NFR-007** | User interface shall be responsive and functional on desktop (1920x1080), tablet (768x1024), mobile (375x667)                    |    Non-Functional (Usability)    |  Must Have   |     ICTC      |  Approved  |           UI Testing           |    TC-120     |
| **NFR-008** | System shall achieve minimum System Usability Scale (SUS) score of 70 during UAT                                                 |    Non-Functional (Usability)    | Should Have  |    Faculty    |  Approved  |          UAT Results           |    TC-121     |
| **NFR-009** | System shall maintain 99% uptime during office hours (7 AM - 9 PM, Mon-Fri)                                                      |   Non-Functional (Reliability)   | Should Have  |      SID      |  Approved  |           Monitoring           |    TC-130     |
| **NFR-010** | Database migration path from Firebase Firestore to PostgreSQL/MySQL shall be documented and feasible                             | Non-Functional (Maintainability) |  Must Have   |     ICTC      |  Approved  |          Section 3.6           |    TC-131     |
| **CR-001**  | Prototype shall use Firebase free tier; production shall migrate to university SQL infrastructure                                |            Constraint            |  Must Have   |     ICTC      |  Approved  |          Architecture          |       -       |
| **CR-002**  | System shall be deployable as Progressive Web App (PWA) accessible via standard web browsers                                     |            Constraint            |  Must Have   |     ICTC      |  Approved  |          Architecture          |    TC-140     |
| **CR-003**  | System shall NOT require deployment to Apple App Store or Google Play Store                                                      |            Constraint            |  Must Have   |     ICTC      |  Approved  |          Architecture          |       -       |
| **IR-001**  | System shall integrate with university Active Directory for user authentication via SAML protocol                                |            Interface             |  Must Have   |     ICTC      |  Approved  |          Section 6.3           |    TC-150     |
| **IR-002**  | System shall send email notifications via university SMTP server (production) or Firebase (prototype)                            |            Interface             | Should Have  |     ICTC      |  Approved  |      Notification Module       |    TC-151     |

**RTM Summary Statistics:**

- **Total Requirements:** 40
- **Functional Requirements:** 24 (60%)
- **Non-Functional Requirements:** 10 (25%)
- **Constraint Requirements:** 3 (7.5%)
- **Interface Requirements:** 2 (5%)
- **Must Have:** 27 (67.5%)
- **Should Have:** 10 (25%)
- **Could Have:** 1 (2.5%)

**Requirement Sources:**

- SID: 18 requirements
- ICTC: 15 requirements
- Both SID & ICTC: 5 requirements
- Students/Faculty: 2 requirements

**Requirements Status:**

- Approved: 40 (100%)

### 4.2 Activity Diagram

The Activity Diagram illustrates the complete workflow for the most critical use case: a user reporting a lost item, searching for matches, submitting a claim when a match is found, and the subsequent SID verification and approval process.

**Activity Diagram: End-to-End Lost Item Recovery Process**

_\<Placeholder for Activity Diagram - To be created using UML diagramming tool\>_

**Key Activities Represented:**

1. User Authentication (SAML SSO)
2. Report Lost Item (with photos and details)
3. System stores item in database
4. User performs periodic searches
5. System returns search results with potential matches
6. User views item details and compares photos
7. User submits claim with proof of ownership description
8. System notifies SID Admin of new claim
9. SID Admin reviews claim details and item photos
10. **Decision Point:** Admin approves or denies
    - **Branch A - Approval:**
      - System notifies user of approval
      - User schedules pickup time
      - User arrives at SID office with ID
      - SID verifies ID and releases item
      - System marks item as "claimed" and archives
    - **Branch B - Denial:**
      - Admin provides denial reason
      - System notifies user
      - User can submit additional proof (loop back to step 7)
11. Process ends

**Diagram Notes:**

- **Swimlanes:** User, System, SID Admin
- **Decision Points:**
  - User found match? (Yes → Submit Claim, No → Continue searching)
  - Admin approval? (Approve → Notify user, Deny → Request more info)
  - ID verification at pickup? (Verified → Release item, Failed → Escalate)
- **Exception Flows:**
  - User cancels claim → Item returns to "Available" status
  - Item lost/damaged before pickup → Admin notes in system, notifies user
  - Fraudulent claim detected → Admin flags user, logs incident

**Related Diagrams:**

- See Section 5.3 for Sequence Diagrams showing detailed system interactions
- See Section 5.4 for Collaboration Diagrams showing object relationships

2. Example of a figure label. (_figure label_)

3. # **Analysis and Design**

_\<Introduction here.\>_

1. ## **Use Case Diagram**

_\<Provide an introduction.\>_  
_\<Place here the use case diagram. Have a brief explanation below it.\>_

1. ## **Use Case Description**

_\<Write an introduction then place here the use case descriptions.\>_

|           Use Case ID: | Enter a unique numeric identifier for the Use Case. e.g. UC-1.2.1                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| ---------------------: | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|     **Use Case Name:** | Enter a short name for the Use Case using an active verb phrase. e.g. Withdraw Cash                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|            **Actors:** | \[An actor is a person or other entity external to the software system being specified who interacts with the system and performs use cases to accomplish tasks. Different actors often correspond to different user classes, or roles, identified from the customer community that will use the product. Name the actor that will be initiating this use case (primary) and any other actors who will participate in completing the use case (secondary).\]                                                                                                                                                                                                                                                                                                                                                 |
|       **Description:** | \[Provide a brief description of the reason for and outcome of this use case.\]                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|           **Trigger:** | \[Identify the event that initiates the use case. This could be an external business event or system event that causes the use case to begin, or it could be the first step in the normal flow.\]                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|     **Preconditions:** | \[List any activities that must take place, or any conditions that must be true, before the use case can be started. Number each pre-condition. e.g. Customer has active deposit account with ATM privileges Customer has an activated ATM card.\]                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|       **Normal Flow:** | \[Provide a detailed description of the user actions and system responses that will take place during execution of the use case under **normal, expected** conditions. This dialog sequence will ultimately lead to accomplishing the goal stated in the use case name and description. Example: Customer inserts ATM card Customer enters PIN System prompts customer to enter language performance English or Spanish System validates if customer is in the bank network System prompts user to select transaction type Customer selects Withdrawal From Checking System prompts user to enter withdrawal amount … System ejects ATM card\]                                                                                                                                                               |
| **Alternative Flows:** | \[Document **legitimate** branches from the main flow to handle special conditions (also known as extensions). For each alternative flow reference the branching step number of the normal flow and the condition which must be true in order for this extension to be executed. e.g. Alternative flows in the _Withdraw Cash_ transaction: 4a. In step 4 of the normal flow, if the customer is not in the bank network System will prompt customer to accept network fee Customer accepts Use Case resumes on step 5 4b. In step 4 of the normal flow, if the customer is not in the bank network System will prompt customer to accept network fee Customer declines Transaction is terminated Use Case resumes on step 9 of normal flow Note: Insert a new row for each distinctive alternative flow. \] |
|        **Exceptions:** | \[Describe any anticipated **error conditions** that could occur during execution of the use case, and define how the system is to respond to those conditions. e.g. Exceptions to the Withdraw Case transaction 2a. In step 2 of the normal flow, if the customer enters and invalid PIN Transaction is disapproved Message to customer to re-enter PIN Customer enters correct PIN Use Case resumes on step 3 of normal flow\]                                                                                                                                                                                                                                                                                                                                                                             |
|    **Postconditions:** | \[Describe the state of the system at the conclusion of the use case execution. Should include both _minimal guarantees_ (what must happen even if the actor’s goal is not achieved) and the _success guarantees_ (what happens when the actor’s goal is achieved. Number each post-condition. e.g. Customer receives cash Customer account balance is reduced by the amount of the withdrawal and transaction fees\]                                                                                                                                                                                                                                                                                                                                                                                        |

|           Use Case ID: | And so on… |
| ---------------------: | :--------- |
|     **Use Case Name:** |            |
|            **Actors:** |            |
|       **Description:** |            |
|           **Trigger:** |            |
|     **Preconditions:** |            |
|       **Normal Flow:** |            |
| **Alternative Flows:** |            |
|        **Exceptions:** |            |
|    **Postconditions:** |            |

3. ## **Sequence Diagram** {#sequence-diagram}

_\<Write an introduction here then place the sequence diagrams. Have a brief explanation of the diagram below it.\>_

3. Example of a figure label. (_figure label_)

_\<Narrative for the diagram placed above.\>_

4. Example of a figure label. (_figure label_)

_\<And so on….\>_

4. ## **Collaboration Diagram** {#collaboration-diagram}

_\<Write an introduction here then place the collaboration diagrams. Have a brief explanation of the diagram below it.\>_

5. Example of a figure label. (_figure label_)

_\<Narrative for the diagram above.\>_

6. Example of a figure label. (_figure label_)

7. # **Data Models** {#data-models}

_\<Intro here. In this section place the ERD and class diagram. Provide a short description of each section and write a short narrative explaining the diagram after each of them.\>_

1. ## **Entity-Relationship Diagram** {#entity-relationship-diagram}

_\<Write an introduction here then place the ER diagram. Write a short narrative explaining the diagram.\>_

7. Example of a figure label. (_figure label_)

   2. ## **Class Diagram** {#class-diagram}

_\<Write an introduction here then place the class diagram. Write a short narrative explaining the diagram.\>_

8. Example of a figure label. (_figure label_)

   3. ## **Context Diagram** {#context-diagram}

_\<Write an introduction here then place the context diagram. Write a short narrative explaining the diagram.\>_

9. Example of a figure label. (_figure label_)

   4. ## **Component Diagram** {#component-diagram}

_\<Write an introduction here then place the component diagram. Write a short narrative explaining the diagram.\>_

10. Example of a figure label. (_figure label_)

    5. ## **Package Diagram** {#package-diagram}

_\<Write an introduction here then place the package diagram. Write a short narrative below explaining the diagram.\>_

11. Example of a figure label. (_figure label_)

12. # **The System** {#the-system}

_\<Intro Here_  
_This section gives the overall specifications and functional requirements of the software to be developed_.\>

1. ## **System Overview** {#system-overview}

_\<Provide an overview of the section here. This section gives an overall view of the main features and capabilities of the software.\>_

### **System Features**

_\<Intro here\>_  
_\<Remember the difference between system feature and function. Place here the main features of the system then describe the functions in the next section. Example: Manage Users, Manage Registration, etc.\>_

1. #### **_System Feature 1_**

_\<Don’t really say “System Feature 1.” State the feature name in just a few words.\>_  
_\<Provide a description of the feature.\>_

2. #### **_System Feature 2_**

_\<Don’t really say “System Feature 2.” State the feature name in just a few words.\>_  
_\<Provide a description of the feature.\>_

3. #### **_System Feature 3 (and so on)_**

_\<Don’t really say “System Feature 3.” State the feature name in just a few words.\>_  
_\<Provide a description of the feature.\>_

2. ### **System Functions**

_\<Provide an overview here. This section provides a listing of all the functions that must be performed or delivered by the system, and a description of each. Include screen designs to help visualize the function being discussed. Usually, the functions are based on the menu and toolbar options. Be detailed in this section.\>_

1. #### **_System Function 1_**

   _\< Provide a description of the function.\>_

   _\<Screen Designs/Screen Shots of the function\>_

   2. #### **_System Function 2_**

   _\< Provide a description of the function.\>_

   _\<Screen Designs/Screen Shots of the function\>_

   3. #### **_System Function 3 (and so on)_**

   _\<Provide a description of the function.\>_

   _\<Screen Designs/Screen Shots of the function\>_

2. # **Other Nonfunctional Requirements** {#other-nonfunctional-requirements}

   1. ## **Performance Requirements** {#performance-requirements}

_\<If there are performance requirements for the product under various circumstances, state them here and explain their rationale, to help the developers understand the intent and make suitable design choices. Specify the timing relationships for real time systems. Make such requirements as specific as possible. You may need to state performance requirements for individual functional requirements or features.\>_

2. ## **Safety Requirements** {#safety-requirements}

_\<Specify those requirements that are concerned with possible loss, damage, or harm that could result from the use of the product. Define any safeguards or actions that must be taken, as well as actions that must be prevented. Refer to any external policies or regulations that state safety issues that affect the product’s design or use. Define any safety certifications that must be satisfied.\>_

3. ## **Security Requirements** {#security-requirements}

_\<Specify any requirements regarding security or privacy issues surrounding use of the product or protection of the data used or created by the product. Define any user identity authentication requirements. Refer to any external policies or regulations containing security issues that affect the product. Define any security or privacy certifications that must be satisfied.\>_

4. ## **Software Quality Attributes** {#software-quality-attributes}

_\<Specify any additional quality characteristics for the product that will be important to either the customers or the developers. Some to consider are: adaptability, availability, correctness, flexibility, interoperability, maintainability, portability, reliability, reusability, robustness, testability, and usability. Write these to be specific, quantitative, and verifiable when possible. At the least, clarify the relative preferences for various attributes, such as ease of use over ease of learning.\>_

9. # **Results and Discussion** {#results-and-discussion}

\<_This section provides the results and discussion. After you have done testing your software, present the results here and discuss its interpretation. Provide graphical representation of the results to support your discussion.\>_

10. # **Summary and Conclusion** {#summary-and-conclusion}

\<_This section gives an assessment of what happened in this project. It presents **explanations and justifications** on **how the objectives** of the project **were met**, to what extent and why some objectives were not met.\>_

11. # **Recommendations** {#recommendations}

**Appendix A: Working Bibliography**

_\<List any other documents or Web addresses to which this SRS refers. These may include user interface style guides, contracts, standards, system requirements specifications, use case documents, or a vision and scope document. Provide enough information so that the reader could access a copy of each reference, including title, author, version number, date, and source or location. Please use APA format. \>_

_\<Working Bibliography._ List all references – APA7 citation reference\>

\<DON’T FORGET TO UPDATE THE TABLE OF CONTENTS\>

**Appendix B: Interview Results and Documentation**

_\<Place interview questions and per respondent’s transcript. Include documentation – pictures during the interview\>_

**Appendix C: Work Breakdown Structure**

_\<Place complete WBS, align main phases using prototyping method\>_

**Appendix D: Glossary**

_\<Define all the terms necessary to properly interpret the SRS, including acronyms and abbreviations. You may wish to build a separate glossary that spans multiple projects or the entire organization, and just include terms specific to a single project in each SRS.\>_
