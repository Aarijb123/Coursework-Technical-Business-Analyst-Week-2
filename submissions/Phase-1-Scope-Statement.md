### Phase 1: In-Scope Justifications

### 1. Identity Verification & Customer Portal
- Entry is managed via a "Magic Link" sent to the customer’s verified contact method, granting temporary session access to a mobile-friendly dashboard. This dashboard displays the current balance, existing payment plan details, and the three most recent payments in a read-only format.

Justification:
- Eliminates development costs for password management and security reset workflows.
- Protects data integrity by preventing users from manually altering financial records.
- Captures a mandatory audit trail of all logins for compliance and risk monitoring.

### 2. Tiered Payment Plan Selection
- The system applies logic-based filters to route customers into specific categories based on their debt balance, ranging from £150 to £10,000. Customers are guided toward either "Pay in Full" links or structured installment plans that are automatically capped at a five-year duration.

Justification:
- Prevents "Interest Loops" by keeping low-balance cases with agents for final negotiation.
- Automates high-volume, low-complexity debt recovery to increase operational efficiency.
- Standardizes the recovery window to a maximum of 5 years for better financial forecasting.

### 3. Financial Difficulty & Vulnerability Exit
- A prominent "Financial Hardship" option allows customers to self-declare difficulties, which triggers an immediate halt to all automated collection prompts. The system captures basic hardship details through a simple form before automatically routing the case to a specialized human agent.

Justification:
- Ensures strict adherence to consumer credit regulations regarding vulnerable customers.
- Mitigates brand risk by ensuring empathetic human handling of sensitive personal crises.
- Facilitates "Duty of Care" by providing immediate access to third-party support links.

### 4. Digital Promise-to-Pay (PTP) Capture
- The system generates a structured repayment schedule that the customer accepts via a "Click-to-Accept" digital disclaimer. Once accepted, the CRM is updated to "PTP Active" and a confirmation PDF is automatically emailed to the customer for their records.

Justification:
- Converts manual agent notes into structured, monitorable data.
- Reduces "Average Handle Time" (AHT) by automating the generation and delivery of legal schedules.
- Secures a defendable legal commitment via timestamped and IP-logged records.

### 5. Case Validation
- Before proceeding to a plan, the system prompts the user to verify their mobile number and email address to ensure our records are current. A backend validation check simultaneously confirms the case has a verified balance and valid status before allowing the journey to continue.

Justification:
- Prevents system errors by ensuring only "Complete" cases enter the automation flow.
- Improves long-term debt recovery rates by constantly refreshing customer contact information.
- Reduces agent administrative burden by filtering out cases with missing or invalid data.

### 6. Rules-Based Routing
- An automated logic that assigns cases to specific agent queues or automated workflows based on balance size and case completeness. This ensures that high-value or highly complex cases are prioritized for human review while standard cases remain in the digital flow.

Justification:
- Protects specialist agent capacity by filtering out simple administrative tasks.
- Eliminates "Case Stagnation" by ensuring every file has a clear automated or manual destination.
Provides Daniel with a transparent "Reason Code" for every case handoff for auditing.

### 7. Journey Monitoring & Reminders
- The system monitors user progress in real-time and triggers automated email or SMS reminders if a journey is started but not completed. If a customer remains inactive after a set number of nudges, the case is automatically closed in the portal and returned to a manual agent queue.

Justification:
- Ensures no case is "lost" in the portal if a customer fails to complete the journey.
- Creates a "Closed Loop" system where the human takes back control the moment the automation stalls.

### 8. Agent Case Visibility (Read-Only)
- Agents are provided with a dedicated view within the CRM that displays a chronological timeline of the customer’s interactions with the portal. This view includes login timestamps, plans viewed, and any validation errors encountered, without allowing the agent to edit the portal data.

Justification:
- Eliminates "Blind Calling" by giving agents full context before they contact a customer.
- Increases agent productivity by consolidating disparate data points into a single timeline.

### Phase 1: Out-of-Scope Justifications

### 1. Identity & Portal Management
- We are excluding the creation of permanent user profiles and the integration of government ID verification tools. There will be no functionality for customers to search for their own accounts via a public-facing website.

Justification:
- Excluded to avoid the significant security infrastructure and maintenance costs required for user profiles.

### 2. Custom Plan Negotiation
- The system will not allow customers to propose their own payment amounts or dates outside of the pre-set tiers, nor will it support interest rate waivers. All "off-menu" negotiations must be handled through a direct conversation with a collections agent.

Justification:
- Excluded to keep the system logic rigid and reduce the risk of non-compliant payment plans being generated.

### 3. Automated Hardship Resolution
- While the portal detects hardship, it will not attempt to calculate or offer a specific "Hardship Payment Plan" or debt-relief agreement automatically. The system will not host direct 1-on-1 financial counseling sessions or live web-chat support for these cases.

Justification:
- Excluded because these high-risk decisions require human judgment and deep financial assessment.

### 4. Transactional Banking
- Direct payment processing via credit/debit card, the automated setup of Direct Debit mandates, and the use of third-party signature tools like DocuSign are entirely excluded. The portal serves to capture the promise to pay, not the physical transaction of funds.

Justification:
- Excluded to avoid the heavy technical complexity and security compliance of banking integrations in Phase 1.

### 5. Legal Identity Changes
- Customers will not be able to use the portal to update their legal names, home addresses, or to authorize third-party representation (such as a debt management company). These changes require physical proof of identity which is outside the current digital verification scope

Justification:
- Excluded to bypass the complex "Proof of Identity" (KYC) requirements associated with legal record changes.

### 6. Infrastructure & Manual Overrides
- We are not attempting to consolidate legacy databases into a "Single Source of Truth" or allowing agents to manually "override" the automated routing logic from within the portal. The system will function as a separate layer that reads from existing data sources "as-is."

Justification:
- Excluded to prioritize speed-to-market and protect the integrity of the automated routing logic.

### 7. Agent Editing Tools
- Agents will not have the ability to modify the customer’s view, trigger custom portal messages, or access high-level analytics and heatmaps within the dashboard. The agent interface is strictly for monitoring and information gathering to aid manual conversations.

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