# Solution Architecture

## Overview

The AI Lead Management & CRM Automation Platform connects website lead capture, data processing, AI-powered lead qualification, CRM integration, sales notifications, and marketing segmentation.

The workflow is orchestrated by **n8n** and integrates Wix, Google Sheets, OpenRouter, Zoho CRM, Telegram, and Klaviyo.

## System Components

| Component | Responsibility |
|---|---|
| Wix | Corporate website and lead capture form |
| n8n | Workflow orchestration and integration logic |
| Google Sheets | Lead data storage and process logging |
| OpenRouter | Access to an LLM for lead qualification |
| Zoho CRM | Lead record creation and centralized lead management |
| Telegram Bot API | Notifications to the sales team |
| Klaviyo | Customer profiles and marketing segmentation |

## Data Flow

1. A potential customer submits an inquiry through the Wix website form.
2. The n8n workflow receives the submitted lead data.
3. The workflow validates and preprocesses the available customer information.
4. Lead information is stored in Google Sheets.
5. The workflow creates a lead record in Zoho CRM through its API.
6. A Telegram notification is sent to the sales team.
7. Lead information is submitted to an LLM through OpenRouter for purchase-intent classification.
8. The qualification result is used to create or update a customer profile in Klaviyo and assign the contact to an appropriate marketing segment.

This sequence is a conceptual representation of the process. The exact execution order and dependencies should be verified against the actual n8n workflow.

## AI Lead Qualification

The AI analyzes the available lead information and assigns one of three purchase-intent categories:

- **Hot:** The customer is actively looking for a solution or is ready to purchase.
- **Warm:** The customer is interested but may require further communication.
- **Cold:** The customer shows low purchase intent or provides insufficient information for qualification.

A Structured Output Parser is used to return classification results in a standardized format.

The qualification result supports marketing segmentation in Klaviyo.

## Integration Architecture

### Wix to n8n

The website form acts as the lead acquisition entry point and initiates the automated processing workflow.

### n8n to Google Sheets

Lead information is stored for data logging and process tracking.

### n8n to Zoho CRM

The Zoho CRM API is used to create lead records automatically.

### n8n to Telegram

The Telegram Bot API delivers notifications about new inquiries to the sales team.

### n8n to OpenRouter

OpenRouter provides access to an LLM used to classify lead purchase intent.

### n8n to Klaviyo

Klaviyo API requests create or update customer profiles and support assignment to marketing segments based on AI qualification results.

## Design Considerations

- **Modularity:** Business applications are connected through an orchestration layer.
- **Structured AI output:** Standardized classification results support downstream processing.
- **Reduced manual work:** Lead data is transferred between connected systems automatically.
- **Sales visibility:** Telegram notifications help the team respond to new inquiries.
- **Marketing personalization:** AI qualification supports targeted customer segmentation.

## Scope and Limitations

This document describes the conceptual architecture of the portfolio case study. It is not an exact export of the n8n workflow or a complete deployment guide.

The actual workflow configuration, execution order, error handling, and retry behavior should be documented separately if they are verified in the implementation.

## Related Resources

- [Full portfolio case study](https://app.notion.com/p/portfolio-kovalov/AI-Lead-Management-CRM-Automation-Platform-for-Spec-Montazh-3b5b7f0c14358080b7b7f8ee6200b528?source=copy_link)
- [Repository README](../README.md)
