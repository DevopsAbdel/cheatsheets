# The Ultimate AI GTM Pipeline Guide: Architecture, Templates & Examples

As an AI Engineer, building a deterministic, agentic workflow requires strict boundaries, clear API clients, and well-defined prompts. Below is the complete, comprehensive production manual containing the full folder architecture layout, template purposes, and concrete examples for **every single file** in the AI Cold Outreach Pipeline structure.

---

## 1. Project Directory Tree Layout

Below is the visual map of the entire repository structure required to make this pipeline operational:

```text
ai-cold-outreach-pipeline/
├── CLAUDE.md
├── .env.example
├── .mcp.json
├── .gitignore
├── requirements.txt
├── 1-scoring-criteria.md
├── 2-apollo-api-docs.md
├── 3-copy-frameworks.md
├── 4-smartlead-api-docs.md
├── lib/
│   ├── apollo_client.py
│   └── smartlead_client.py
├── outputs/
│   ├── companies-scored.csv
│   ├── contacts.csv
│   └── email-sequences.md
└── .claude/
    ├── skills/
    │   ├── score-icp/
    │   ├── find-contacts/
    │   ├── write-sequence/
    │   └── deploy-campaign/
    ├── agents/
    │   ├── icp-scorer.md
    │   ├── deliverability-auditor.md
    │   ├── personalization-writer.md
    │   └── reply-classifier.md
    ├── commands/
    │   └── run-campaign.md
    ├── hooks/
    │   └── PostToolUse.sh
    └── settings.json

```
## 2. Root Directory: Brain & System Configuration
### CLAUDE.md
**Template Purpose:** The core campaign brain and global context system prompt for your AI agent. It acts as the agent's absolute rules of engagement.
**Example:**
```markdown
# Role
You are an elite, production-grade AI Go-To-Market (GTM) Orchestrator. Your objective is to run autonomous cold outbound campaigns by coordinating dedicated sub-agents and programmatic API tools.

# Rules of Engagement
1. **Validation First:** Always analyze and score target companies using `1-scoring-criteria.md` before looking for contacts.
2. **Deterministic Calls:** Rely strictly on the Python modules inside `lib/` for all external network requests.
3. **Copywriting Standards:** Ensure every generated message perfectly complies with the multi-tiered guidelines in `3-copy-frameworks.md`.
4. **Safety Check:** You must execute the deliverability auditor agent on all sequence drafts before invoking production deployment tools.

```
### .env.example
**Template Purpose:** A secure environment configuration blueprint declaring required API credentials without revealing live credentials to source control.
**Example:**
```env
# Credentials Configuration Template
APOLLO_API_KEY=your_apollo_production_key_here
SMARTLEAD_API_KEY=your_smartlead_api_key_here
PIPELINE_ENV=development

```
### .mcp.json
**Template Purpose:** Configures Model Context Protocol (MCP) servers, granting the LLM native capability to run local integrations for data platforms.
**Example:**
```json
{
  "mcpServers": {
    "apollo-mcp": {
      "command": "python",
      "args": ["-m", "lib.apollo_mcp_server"]
    },
    "smartlead-mcp": {
      "command": "node",
      "args": [".claude/mcp/smartlead/index.js"]
    }
  }
}

```
### .gitignore
**Template Purpose:** Instructs git version control to completely ignore sensitive private files, environment variables, local logs, and large raw data exports.
**Example:**
```text
# Sensitive Configurations
.env
*.env.*
!.env.example

# Local Agent Caches & Python Artifacts
__pycache__/
*.py[cod]
.claude/cache/

# Pipeline Outputs & Execution Logs
outputs/*.csv
outputs/*.md
outputs/pipeline-log.txt

```
### requirements.txt
**Template Purpose:** Declares python library package dependencies with exact pinned versions to maintain deterministic workspace setups across engineering environments.
**Example:**
```text
requests==2.31.0
python-dotenv==1.0.0
pandas==2.2.0
openpyxl==3.1.2

```
## 3. Root Directory: Playbooks & Documentation Reference
### 1-scoring-criteria.md
**Template Purpose:** Sets a clear mathematical qualification rubric for the AI agent to accurately bucket leads into priority tiers.
**Example:**
```markdown
# Ideal Customer Profile (ICP) - 6-Factor Matrix Rubric

Evaluate target company profiles programmatically against the following exact indicators:
1. **Vertical Alignment (1 pt):** Enterprise B2B SaaS, Cloud Infrastructure, or FinTech.
2. **Employee Scaling (1 pt):** Active headcount between 50 and 500 personnel.
3. **Funding Velocity (1 pt):** Documented Series A or Series B institutional raise within the past 18 months.
4. **Technology Stack Compatibility (1 pt):** Currently deploys AWS, HubSpot, or Snowflake infrastructure.
5. **Growth Velocity Demand (1 pt):** Active career job openings for Sales Development or Engineering leadership.
6. **Market Signal Activation (1 pt):** Recent public product launch, merger announcement, or strategic executive hire.

### Priority Tier Evaluation Matrix
- **Tier 1 (High Priority Fit):** Score evaluation yields >= 5 out of 6 points.
- **Tier 2 (Medium Value Fit):** Score evaluation yields 3 to 4 points.
- **Tier 3 (Low Value Fit):** Score evaluation yields < 3 points. Discard immediately.

```
### 2-apollo-api-docs.md
**Template Purpose:** Serves as a reference sheet teaching the AI model how to make payload requests to the Apollo API client wrapper.
**Example:**
```markdown
# Apollo API Lead-Gen Reference Manual

### Target Lookup Endpoint
- **Method:** `POST`
- **Path:** `/v1/mixed_people/search`
- **Required Params:** `api_key`, `q_organization_domains`, `person_titles`

### Data Cleaning Validation Endpoint
- **Method:** `POST`
- **Path:** `/v1/email/verify`
- **Required Params:** `email`

### Engine Directives
- Always batch array operations in packets of up to 50 domains to minimize rate-limiting penalties.
- Extract custom corporate fields to populate growth indicators before running the scoring engine.

```
### 3-copy-frameworks.md
**Template Purpose:** Strict structural blueprint controlling copywriting patterns and ensuring context-driven email variations.
**Example:**
```markdown
# Tiered Messaging & Copywriting Rules

### Tier 1 Strategy (Hyper-Personalized Execution)
- **Opener Line:** Craft a completely unique, 1-line sentence mentioning a specific recent PR news event or executive quote.
- **Value Core:** Connect the observed event directly to quantified financial ROI benchmarks.
- **Call-To-Action:** Soft, zero-friction inquiry asking for a concept review (e.g., "Worth an exploratory look?").

### Tier 2 Strategy (Problem-Centric Template Execution)
- **Opener Line:** Focus directly on an immediate sector operational bottleneck.
- **Value Core:** Embed a highly relevant 1-sentence case study showcasing a direct competitor.
- **Call-To-Action:** Request a brief introduction to the internal project manager.

### Tier 3 Strategy (Generic Broad Outreach)
- **Opener Line:** Straight value-proposition introduction.
- **Call-To-Action:** Direct booking link request.

```
### 4-smartlead-api-docs.md
**Template Purpose:** Operational playbook guiding the AI agent through the precise formatting, validation, and multi-step delivery pipeline within Smartlead.
**Example:**
```markdown
# Smartlead Campaign Execution Playbook

### Required Lead Intake Structure
All prospect imports must strictly comply with the following header mapping sequence:
`email,first_name,last_name,company,tier,personalized_opener`

### System Deployment Steps
1. **Schema Check:** Confirm formatting correctness before data generation.
2. **Lead Injection API:** Issue a `POST` request to `/v1/campaigns/{campaign_id}/leads/import`.
3. **Sequence Start Execution:** Initialize active mail sending by executing a `POST` instruction to `/v1/campaigns/{id}/activate`.

```
## 4. lib/: Programmatic Python API Clients
### lib/apollo_client.py
**Template Purpose:** Underlying logic client enabling deterministic lookup requests against the Apollo data directory.
**Example:**
```python
import os
import requests
from dotenv import load_dotenv

load_dotenv()
APOLLO_KEY = os.getenv("APOLLO_API_KEY")

def lookup_company_decision_makers(domain, titles):
    """
    Queries the Apollo engine for validated business emails based on domain and job titles.
    """
    endpoint_url = "[https://api.apollo.io/v1/mixed_people/search](https://api.apollo.io/v1/mixed_people/search)"
    payload = {
        "api_key": APOLLO_KEY,
        "q_organization_domains": [domain],
        "person_titles": titles
    }
    headers = {
        "Content-Type": "application/json",
        "Cache-Control": "no-cache"
    }
    
    response = requests.post(endpoint_url, json=payload, headers=headers)
    if response.status_code == 200:
        return response.json().get("people", [])
    return []

```
### lib/smartlead_client.py
**Template Purpose:** Code backend orchestrating programmatic upload operations directly to sales campaign mailboxes.
**Example:**
```python
import os
import requests
from dotenv import load_dotenv

load_dotenv()
SMARTLEAD_KEY = os.getenv("SMARTLEAD_API_KEY")

def push_prospects_to_sequence(campaign_id, formatted_leads):
    """
    Deploys a list of verified prospects with custom variables directly to a Smartlead campaign.
    """
    endpoint_url = f"[https://api.smartlead.ai/api/v1/campaigns/](https://api.smartlead.ai/api/v1/campaigns/){campaign_id}/leads"
    query_params = {"api_key": SMARTLEAD_KEY}
    payload = {
        "lead_list": formatted_leads
    }
    
    response = requests.post(endpoint_url, params=query_params, json=payload)
    return response.status_code == 201 or response.status_code == 200

```
## 5. outputs/: Campaign Artifacts & Datasets
### outputs/companies-scored.csv
**Template Purpose:** Holds intermediate company metrics populated by the qualification agent for review and filtering.
**Example:**
```csv
company_domain,industry,employee_count,total_score,tier
enterprise-acme.com,SaaS,145,5,Tier 1
global-logistics.io,Logistics,220,3,Tier 2
micro-start.co,Fintech,12,2,Tier 3

```
### outputs/contacts.csv
**Template Purpose:** Persists individual validated executive data sets extracted via search functions.
**Example:**
```csv
email,first_name,last_name,title,company_domain,tier
sarah.jenkins@enterprise-acme.com,Sarah,Jenkins,VP Growth,enterprise-acme.com,Tier 1
marcus.vance@global-logistics.io,Marcus,Vance,Director Sales,global-logistics.io,Tier 2

```
### outputs/email-sequences.md
**Template Purpose:** Serves as a staging document storing custom written outreach messaging prior to automated push stages.
**Example:**
```markdown
# Campaign Sequence Review Drafts

### Target: sarah.jenkins@enterprise-acme.com
- **Campaign ID:** 88412
- **Subject Line:** Scale engineering efficiency at enterprise-acme.com
- **Email Content:**
  Hi Sarah, noticed you recently expanded enterprise-acme.com's infrastructure team by adding 15 remote developers last quarter. 

  As engineering presence scales, velocity tracking normally encounters alignment blindspots. Our tool automates real-time delivery audits directly from code activities.

  Worth a 5-minute exploratory sync next Tuesday?

```
## 6. .claude/: Agent OS Configuration & Core Systems
### .claude/skills/
**Template Purpose:** Folder containing single-purpose atomic script modules executed directly by the LLM runner environment.
**Example (.claude/skills/score-icp/run.py):**
```python
def main(factors_met):
    # Calculates quantitative prioritization tier category 
    score = sum(factors_met)
    if score >= 5:
        return "Tier 1"
    elif score >= 3:
        return "Tier 2"
    return "Tier 3"

```
### .claude/agents/
**Template Purpose:** Isolated markdown personas that enforce functional boundaries and keep sub-agents decoupled from unrelated workspace rules.
#### icp-scorer.md
```markdown
# Sub-Agent Prompt: ICP Qualification Specialist
Your sole task is parsing incoming raw domain data, fetching matching profiles via the Apollo MCP, applying the 6-factor assessment rubric, and updating `outputs/companies-scored.csv`. Do not draft emails or make sequencing adjustments.

```
#### deliverability-auditor.md
```markdown
# Sub-Agent Prompt: Email Safety & Deliverability Specialist
Analyze every email copy draft for high-risk spam-trigger words (e.g., "FREE", "BUY NOW", "GUARANTEED"). Validate that domain settings (SPF, DKIM) are correctly configured on any outbound mailbox profile prior to active queue processing.

```
#### personalization-writer.md
```markdown
# Sub-Agent Prompt: Contextual Copywriter
Review target executive background entries and generate unique, high-conversion 1-line email introductions in complete alignment with the framework strategies detailed in `3-copy-frameworks.md`.

```
#### reply-classifier.md
```markdown
# Sub-Agent Prompt: Incoming Reply Router
Analyze incoming campaign email responses and bucket them accurately into one of three classifications: `[Interested, Out of Office, Negative Subscriptions]`. Update CRM trackers accordingly.

```
### .claude/commands/run-campaign.md
**Template Purpose:** Custom workflows bound to macro terminal commands to chain multi-agent tasks together sequentially.
**Example:**
```markdown
# Executable Slash Macro: /run-campaign
Upon invocation, execute these orchestrations step-by-step:
1. Initialize target data processing via the `icp-scorer` agent.
2. For all Tier 1 & Tier 2 entities, run the `find-contacts` discovery module.
3. Pass results to `personalization-writer.md` to draft custom sequences.
4. Process all completed content blocks through the `deliverability-auditor.md` agent.
5. Programmatically trigger data loading into production endpoints using `deploy-campaign`.

```
### .claude/hooks/PostToolUse.sh
**Template Purpose:** Event hook scripts that trigger downstream processes automatically immediately after tools run.
**Example:**
```bash
#!/bin/bash
# Local pipeline audit logger hook
TIMESTAMP=$(date "+%Y-%m-%d %H:%M:%S")
echo "[${TIMESTAMP}] Tool Executed successfully by Claude Code Engine" >> outputs/pipeline-log.txt

```
### .claude/settings.json
**Template Purpose:** Global governance rules restricting prompt behavior, specifying model targets, and containing safety allowlists for tools.
**Example:**
```json
{
  "model": "claude-3-5-sonnet-20241022",
  "temperature": 0.1,
  "mcp_allowlist": [
    "apollo-mcp",
    "smartlead-mcp"
  ],
  "auto_approve_tool_use": true,
  "max_tokens_to_sample": 4096
}

```