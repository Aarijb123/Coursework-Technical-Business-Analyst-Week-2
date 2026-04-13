## Phase 1 In-Scope

I have identified six main automation processes designed to eliminate current pain points for both our agents and our customers. By focusing on these specific boundaries, we ensure a "buildable" Phase 1 that delivers immediate value without over-complicating our backend infrastructure.

1. Identity Verification & Customer Portal
The entry point of the journey uses a "Magic Link" sent to the customer's preferred contact method, ensuring access is granted via a session-based token without the need for a permanent password. This portal provides a mobile-friendly Account Summary where customers can view their current debt balance, confirm their existing payment plan, and review their last three payments. To maintain data integrity, this remains a read-only environment where users can view their status but cannot manually edit financial figures. The system will log every login attempt, the device type used, and a timestamp of when the "Summary" was accessed.

2. Eligible Payment Plan Selection
This process uses automated logic to filter cases into three distinct tiers based on the balance floor and ceiling we have established. Balances under £150 will bypass the automated plan selection and move to an agent to prevent the "interest-only" loops Gareth identified. Tier 1 is between £150 and £1,000 are guided to a "Pay in Full" link, while Tier 2 is between £1,000 and £10,000 are presented with structured payment plans capped at a five-year period. Any debt over £10,000 is automatically flagged as "High Complexity" and routed to a specialist. 

3. Financial Difficulty & Vulnerability Exit
A critical component of the portal is the "Financial Difficulty" pathway, which acts as a safety valve for customers unable to meet the standard payment tiers. If a customer flags that they are facing financial or physical difficulties, the automated payment selection is immediately suspended to prevent inappropriate collections. The system will instead provide a self-declaration form to capture basic hardship details and then redirect the customer to an agent for human intervention. This ensures we meet compliance standards by logging the specific hardship flag and providing the customer with immediate links to external support services like StepChange or Citizens Advice.

4. Digital Promise-to-Pay (PTP) Capture
Once a viable plan is selected, the system secures the commitment through a structured digital handshake. This involves the generation of a fixed payment schedule based on the customer’s selection and a "Click-to-Accept" legal disclaimer where the customer acknowledges the debt. Upon acceptance, the system immediately sends an automated confirmation email with a PDF summary of the schedule and updates the CRM status to "PTP Active." To provide a defendable audit trail, we will capture timestamp of every "Accept" click.

5. Contact Detail Update Request & Case Validation
To maintain high data quality, the system includes a function that proactively prompts users to verify their mobile number, email, and contact preferences after a set period. Before any case is escalated or a plan is finalized, a Case Validation check ensures that the account has three mandatory fields, a valid email, a verified balance, and an account status are present and correct. We will log "Before and After" snapshots of contact data and track any validation failures to show how many cases were blocked due to missing information.

6. Rules-Based Routing
The final process ensures that the right work reaches the right person by automatically sorting cases based on the balance, complexity, and completeness verified in previous steps. This routing logic acts as the final handoff, moving straightforward cases through the automation while ensuring "High Complexity" or "Vulnerable" cases reach Gareth’s specialist teams. To ensure full visibility, the system will generate a decision log for every case, recording the specific reason code for its routing path, such as a balance exceeding the £10k threshold or a hardship declaration.

## Phase 1 Out-of-Scope

To maintain a disciplined delivery timeline and ensure the stability of our core automation, the following elements have been strictly excluded from the Phase 1 scope. These items may be considered for future iterations but are not part of Phase 1.

1. Identity Verification & Customer Portal
While the "Magic Link" provides secure session-based access, the creation of permanent customer accounts—including usernames, passwords, and profile management—is strictly out-of-scope. We will not be building "Forgotten Password" workflows, biometric login capabilities, or government-issued ID verification. 

2. Eligible Payment Plan Selection
The automation is limited to the predefined tiers (£150–£10k) and will not support custom negotiations, sliding scales for payment amounts, or interest rate waivers. Any debt falling outside of the "Golden Zone"—specifically "Nuisance" debts under £150 and "High Complexity" debts over £10,000 will be out-of-scope for automated selection and must be handled by an agent. 

3. Financial Difficulty & Vulnerability Exit
The scope for handling financial difficulty is limited to detection and redirection; the portal will not provide automated "Hardship Plan" generation or customized debt-relief negotiations. While we will provide links to external support services, the portal will not host direct financial counseling in Phase 1.

4. Digital Promise-to-Pay (PTP) Capture
The actual collection and processing of funds via credit cards, debit cards, or bank transfers are strictly out-of-scope for the digital capture process. We are excluding the automated setup of Direct Debit mandates and integration with 3rd-party electronic signature platforms like DocuSign, as a "Click-to-Accept" model is sufficient for this phase. The system will not allow for manual adjustments to the PTP dates or amounts once a structured plan has been selected; any deviations require agent intervention.

5. Contact Detail Update Request & Case Validation
The scope of data updates is limited to communication fields only; we are strictly excluding the ability for customers to change their Legal Name, Physical Home Address, or Third-Party authorizations. Case Validation is limited to internal field completeness and will not include the verification of external truths, such as checking if a mobile number is currently "active" with a telecom provider or if an email address is a "disposable" inbox.

6. Rules-Based Routing & Database Infrastructure
We will not be implementing the ability for the automation to re-route cases that are already assigned to a specific agent or team lead. Regarding infrastructure, the recreation or consolidation of backend data into a "Single Source of Truth" is entirely out-of-scope. We will accept the data "As-Is" and will rely on the Case Validation gate to filter out records that are too messy to process.

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