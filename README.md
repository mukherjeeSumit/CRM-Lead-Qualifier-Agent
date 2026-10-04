# CRM Lead Qualifier Agent

## Goal

To develop an AI agent that automatically enriches a new sales lead (identified by an email address) by gathering publicly available company information, checking for prior engagement in the internal CRM, and assigning a preliminary qualification score.

## Context

Sales representatives often spend valuable time manually researching leads and cross-referencing internal systems before a discovery call. This process is slow, inconsistent, and often leads to a poorly prepared first interaction.

## Agent Functionality

The agent must be able to:

1. Extract Domain: Take the email address and extract the company domain name (e.g., jane@acmecorp.com → acmecorp.com).

2. Enrich Company Data: Use the domain to look up (simulated) company details like industry, size, and annual revenue.

3. Check CRM History: Search the internal (simulated) CRM for any past contact or notes associated with the lead's email.

4. Calculate Lead Score: Synthesize all gathered data to assign a qualitative priority score (e.g., High, Medium, Low).

5. Final Summary: Present a concise, actionable summary of all findings to the sales representative.
