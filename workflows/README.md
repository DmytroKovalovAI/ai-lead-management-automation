# Leads Save and Inform

A sanitized n8n workflow for automated lead capture, AI qualification, CRM synchronization, sales notifications, and marketing segmentation.

## Overview

This workflow processes website form submissions and distributes lead data across connected business tools. It uses an AI model to classify leads by buying intent and routes them to the corresponding marketing segment.

## Workflow Architecture

1. **Lead capture:** Receive a website form submission through an n8n Webhook.
2. **Data preprocessing:** Extract the lead's name, surname, email, phone number, and comment.
3. **Business system synchronization:** Send lead information to Zoho CRM and append the submission to Google Sheets.
4. **Sales notification:** Send a Telegram message containing the submitted lead details.
5. **AI qualification:** Analyze the lead's comment using an OpenRouter language model.
6. **Status validation:** Parse the model response and apply a default status when the returned value is not recognized.
7. **Marketing segmentation:** Map the lead's status to a Klaviyo list and create or associate the corresponding profile.

## Lead Qualification

The AI model assigns one of three statuses:

| Status | Meaning |
|---|---|
| `hot` | Strong buying intent, urgency, a specific project, budget, or timeline |
| `warm` | Interest in the service or a request for information without clear urgency |
| `cold` | General interest, browsing, testing, or no clear intent to buy |

Empty comments are classified as `warm` according to the workflow prompt.

## Integrations

- **n8n:** Workflow orchestration and data routing
- **Website form / Webhook:** Lead intake
- **OpenRouter:** AI-powered lead qualification
- **Zoho CRM:** Lead record creation
- **Google Sheets:** Lead data logging
- **Telegram:** Sales team notifications
- **Klaviyo:** Contact creation and list segmentation

## Setup

This repository contains a sanitized workflow export for demonstration purposes.

Before running it:

1. Import `leads-save-and-inform.json` into your n8n instance.
2. Configure your own credentials for each required integration.
3. Replace placeholder values with your own Google Sheets document ID, Telegram chat ID, Klaviyo list IDs, and webhook configuration.
4. Verify the incoming form payload and field mappings.
5. Test each integration with synthetic lead data.
6. Confirm the qualification branches, error handling, and end-to-end execution before enabling the workflow.

## Security Notes

- Credentials and execution sample data have been removed from this public export.
- Never commit API keys, access tokens, personal lead data, or private webhook URLs.
- Use test accounts and synthetic data when validating the workflow.

## Scope and Limitations

This file documents the exported workflow configuration. It does not establish that every integration has been tested successfully in a fresh environment.

Actual behavior depends on the configured credentials, external services, incoming payload structure, and account-specific settings.

