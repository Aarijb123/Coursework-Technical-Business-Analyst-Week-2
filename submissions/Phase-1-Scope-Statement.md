### Phase 1: In-Scope Justifications

### 1. Identity Verification & Customer Portal
- Session-based "Magic Link" access with a read-only view of balances and payments.

Justification:
- Eliminates development costs for password management and security reset workflows.
- Protects data integrity by preventing users from manually altering financial records.
- Captures a mandatory audit trail of all logins for compliance and risk monitoring.

### 2. Tiered Payment Plan Selection
- Logic-based filtering based on balance thresholds (£150–£10k).

Justification:
- Prevents "Interest Loops" by keeping low-balance cases with agents for final negotiation.
- Automates high-volume, low-complexity debt recovery to increase operational efficiency.
- Standardizes the recovery window to a maximum of 5 years for better financial forecasting.

### 3. Financial Difficulty & Vulnerability Exit
- Immediate "Hard Stop" and redirection to specialist agents upon hardship declaration.

Justification:
- Ensures strict adherence to consumer credit regulations regarding vulnerable customers.
- Mitigates brand risk by ensuring empathetic human handling of sensitive personal crises.
- Facilitates "Duty of Care" by providing immediate access to third-party support links.

### 4. Digital Promise-to-Pay (PTP) Capture
- Structured "Click-to-Accept" agreements with automated PDF confirmations and CRM updates.

Justification:
- Converts manual agent notes into structured, monitorable data.
- Reduces "Average Handle Time" (AHT) by automating the generation and delivery of legal schedules.
- Secures a defendable legal commitment via timestamped and IP-logged records.

### 5. Contact Hygiene & Case Validation
- Proactive verification of contact data and automated "Gatekeeper" checks for missing fields.

Justification:
- Prevents system errors by ensuring only "Complete" cases enter the automation flow.
- Improves long-term debt recovery rates by constantly refreshing customer contact information.
- Reduces agent administrative burden by filtering out cases with missing or invalid data.

### 6. Rules-Based Routing
- Automated sorting and queue assignment based on balance, complexity, and completeness.

Justification:
- Protects specialist agent capacity by filtering out simple administrative tasks.
- Eliminates "Case Stagnation" by ensuring every file has a clear automated or manual destination.
Provides Daniel with a transparent "Reason Code" for every case handoff for auditing.

### 7. Journey Monitoring & Reminders
- Time-based nudges for abandoned sessions and automated "Return to Agent" triggers.

Justification:
- Ensures no case is "lost" in the portal if a customer fails to complete the journey.
- Creates a "Closed Loop" system where the human takes back control the moment the automation stalls.

### 8. Agent Case Visibility (Read-Only)
- Consolidated agent view of portal activity, routing reasons, and validation history.

Justification:
- Eliminates "Blind Calling" by giving agents full context before they contact a customer.
- Increases agent productivity by consolidating disparate data points into a single timeline.

### Phase 1: Out-of-Scope Justifications

### 1. Identity & Portal Management
- Permanent user accounts, biometrics (FaceID), and government ID verification.

Justification:
- Excluded to avoid the significant security infrastructure and maintenance costs required for user profiles.

### 2. Custom Plan Negotiation
- Interest rate waivers, sliding scales, or custom payment amounts.

Justification:
- Excluded to keep the system logic rigid and reduce the risk of non-compliant payment plans being generated.

### 3. Automated Hardship Resolution
- Automated generation of hardship plans or debt-relief agreements.

Justification:
- Excluded because these high-risk decisions require human judgment and deep financial assessment.

### 4. Transactional Banking
- Payment processing, Direct Debit setup, and integration with 3rd-party signature tools (DocuSign).

Justification:
- Excluded to avoid the heavy technical complexity and security compliance of banking integrations in Phase 1.

### 5. Legal Identity Changes
- Updates to Legal Name, Physical Address, or 3rd-party authorizations.

Justification:
- Excluded to bypass the complex "Proof of Identity" (KYC) requirements associated with legal record changes.

### 6. Infrastructure & Manual Overrides
- Database consolidation (SSOT) and manual agent "overrides" within the automation.

Justification:
- Excluded to prioritize speed-to-market and protect the integrity of the automated routing logic.

### 7. Complex Outreach
- Multi-channel orchestration and "Resume Journey" features.

Justification:
- Excluded to keep the communication logic simple and ensure customers follow a linear, manageable path.

### 8. Agent Editing Tools
- Ability for agents to modify portal data or access advanced analytics dashboards.

Justification:
- Excluded to focus development purely on operational visibility and context-sharing.
## Assumptions

For the project to stay within this scope I have made the following assumptions:
- While the data is 'messy' the core debt balance figures are accurate enough to be presented to customers as a source of truth.
- A set of "Template" emails and disclaimers for the PTP capture can be fast-tracked through legal approval rather than reviewing every individual customer communication.
- We assume that operations will support a limited pilot meaning that we can roll out Phase 1 to a select few to start with then gradually allowing all customers to phase 1
- Gareth’s specialist teams will have the capacity to monitor the "High Complexity" queues created by the new routing rules.

## constraints
- A major constraint is that the automation can only be as accurate as the existing records. If an account has a "ghost" balance or duplicate entry in the old system, the portal will display it.
- Because we are using "Magic Links" instead of permanent accounts, users cannot "save their progress" and come back later. If the session expires, they have to start the verification flow from scratch.
- If a customer clicks the "Financial Hardship" button, there is a regulatory constraint on how quickly a human specialist must follow up. The automation can't just "drop" the case; it must hit a queue that is staffed within legal time limits to avoid breaching the consumer credit regulations.
- The "Rules-Based Routing" will push high-complexity cases to Gareth’s team. A major operating constraint is the headcount of that team. If the automation is too successful at filtering, Gareth’s specialists might get buried under a mountain of complex cases all at once.
- The £150 and £10k boundaries are hardcoded. A constraint is that agents cannot "force" a £12k case into the automation if they are busy; the system must remain rigid to protect the logic.
- Every automated email (PTP confirmation, OTP code) must pass a formal legal review. The constraint is that any change in the automated message can require a 1-week approval turnaround.

## Deliverables Table

https://docs.google.com/spreadsheets/d/1asMldVsXtsj0Zas_urC_ijlMtxAFTF1uL9I1Oms_NXw/edit?usp=sharing