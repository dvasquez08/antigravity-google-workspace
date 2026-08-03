# Workflow: Prepare for Today's Meetings

## Objective
Automatically gather today's scheduled meetings from Google Calendar, cross-reference relevant client brief documents and product/service pricing, generate a comprehensive meeting prep summary, and create a structured entry inside Notion.

---

## STRICT RULES & CONSTRAINTS
1. **SAME-DAY ONLY (STRICT):** You must ONLY query and retrieve meetings scheduled for the CURRENT calendar day. Do NOT fetch, process, or include events from yesterday, tomorrow, or any other date.
2. **NO ACCIDENTAL MAILS/INVITES:** Do not send emails or alter calendar invites during this workflow run.

---

## Execution Steps

### Step 1: Fetch Today's Meetings
- Query Google Calendar via the Google Workspace MCP tool.
- Filter explicitly for events occurring today (00:00:00 to 23:59:59 local time).
- Extract key details for each event:
  - Event Title
  - Start & End Times
  - Attendees / Contacts
  - Event Description or Video Link

### Step 2: Retrieve Relevant Meeting Briefs
- Search the local or Google Drive folder titled **`Meeting Docs`**.
- Look for any document or brief corresponding to today's meeting attendee(s) or company name (e.g., matching the contact or company name found in the event title/attendees list).
- Read and extract:
  - Company overview & industry
  - Core pain points & requested scope
  - Key contacts

### Step 3: Check Products & Services Reference (Conditional)
- If the meeting brief or event context involves a sales discussion, proposal request, or project pricing:
  - Open and read the reference document inside the **`Products and Services`** folder (e.g., *Nexus AI Solutions – Products & Services Reference Guide*).
  - Cross-reference the requested items in the meeting brief against the service codes (e.g., `DEV-AGT-01`, `DEV-RAG-02`) and pricing tiers.
- *If the meeting is purely internal or unrelated to sales/pricing, skip this step.*

### Step 4: Synthesize Meeting Prep Summary
For each meeting identified today, format a clean summary containing:
- **Meeting Header:** Event Title, Time, and Attendees
- **Client Overview:** Industry, company background, and primary contact
- **Pain Points & Goals:** Key issues they want to solve
- **Recommended Solutions & Pricing Breakdown:** Matched service codes, rates, and estimated project total (if applicable)
- **Talking Points & Agenda Items:** 3–4 strategic questions or next steps to cover during the call

### Step 5: Export to Notion
- Connect to Notion via the Notion MCP tool.
- Locate the database named **`YouTube Test Database`**.
- Create a new page inside **`YouTube Test Database`** titled: `[Prep] <Meeting Title> - <Current Date>`.
- Set database properties if available (e.g., `Date`: Today, `Status`: `Prepared`, `Contact`: Attendee Name).
- Populate the page body with the full synthesized Meeting Prep Summary generated in Step 4.

---

## Final Output Response
Upon completion, output a concise status report back to the user/dashboard:
- Number of meetings processed for today
- Title of the Notion page(s) created in `YouTube Test Database`
- A brief bulleted summary of the meeting prep content