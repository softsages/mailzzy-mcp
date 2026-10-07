# Mailzzy MCP tools

47 tools. Generated from the production tool registry; do not edit by hand.

Access levels:

- **Read**: no changes to your account.
- **Write**: creates or edits records in your account.
- **Write (destructive)**: deletes, voids or cancels something. Clients should confirm with you first.
- **Sends email**: delivers email to real recipients. Clients should confirm with you first.

| Access | Tools |
| --- | --- |
| Read | 22 |
| Write | 20 |
| Write (destructive) | 2 |
| Sends email | 3 |

## Campaigns

| Tool | Access | What it does |
| --- | --- | --- |
| `mcp_crm_audience_select` | Read | Pick a campaign audience (groups, segments or tags), see the de-duplicated recipient count, and check it against the account's sending limits. |
| `mcp_crm_campaign_drafts_create` | Write | Create a campaign DRAFT. |
| `mcp_crm_campaign_drafts_update` | Write | Update an existing campaign DRAFT. |
| `mcp_crm_campaigns_cancel` | Write (destructive) | Permanently delete a campaign that is scheduled but not yet sent. |
| `mcp_crm_campaigns_get` | Read | Fetch a single campaign by its numeric id. |
| `mcp_crm_campaigns_list` | Read | List campaigns. |
| `mcp_crm_campaigns_send` | Sends email | Send or schedule a complete email campaign. |
| `mcp_crm_campaigns_send_test` | Sends email | Send a TEST email (send-to-self / preview) of campaign content to a few verification addresses. |
| `mcp_crm_reports_campaign_metrics` | Read | Fetch the metric counts (requested, sent, success, opened, clicked) for one campaign by its numeric id. |
| `mcp_crm_reports_campaign_performance` | Read | Date-bounded email-sent performance report: sent / success / requested / delivered / opened / clicked counts over a date range. |

## Contacts and groups

| Tool | Access | What it does |
| --- | --- | --- |
| `mcp_crm_contacts_add_tag` | Write | Apply a tag to a contact. |
| `mcp_crm_contacts_bulk_create` | Write | Create a small number of contacts from structured data in the conversation. |
| `mcp_crm_contacts_create` | Write | Create a single contact in a contact group. |
| `mcp_crm_contacts_delete` | Write (destructive) | Soft-delete (archive) a single contact. |
| `mcp_crm_contacts_get` | Read | Fetch a single contact by its numeric id. |
| `mcp_crm_contacts_list` | Read | List contacts. |
| `mcp_crm_contacts_remove_from_group` | Write | Remove a contact from a contact group. |
| `mcp_crm_contacts_remove_tag` | Write | Remove a tag from a contact. |
| `mcp_crm_contacts_update` | Write | Update a single existing contact. |
| `mcp_crm_contacts_upload_csv` | Write | Bulk-upload contacts from a CSV file into Mailzzy. |
| `mcp_crm_groups_create` | Write | Create a new, empty contact group (list). |
| `mcp_crm_groups_list` | Read | List the contact groups, each with its contact count. |

## Segments

| Tool | Access | What it does |
| --- | --- | --- |
| `mcp_crm_segments_bulk_create` | Write | Create multiple audience segments in a single bounded call. |
| `mcp_crm_segments_create` | Write | Create a new audience segment (a saved filter over contacts). |
| `mcp_crm_segments_filter_options` | Read | Get the vocabulary for building an audience segment filter. |
| `mcp_crm_segments_get` | Read | Fetch a single audience segment by its numeric id. |
| `mcp_crm_segments_list` | Read | List audience segments. |
| `mcp_crm_segments_preview` | Read | Preview a segment filter: return how many contacts a segmentDefinition would match, without saving anything. |
| `mcp_crm_segments_update` | Write | Update an existing audience segment. |

## Templates

| Tool | Access | What it does |
| --- | --- | --- |
| `mcp_crm_templates_create` | Write | Create a single email template (name, subject, and HTML/Velocity content). |
| `mcp_crm_templates_get` | Read | Fetch a single email template (including its HTML/JSON body) by its numeric id. |
| `mcp_crm_templates_list` | Read | List email templates (all scopes: system, public, and the caller's own). |
| `mcp_crm_templates_update` | Write | Update an existing email template (partial PATCH: send only the fields to change). |

## Automations

| Tool | Access | What it does |
| --- | --- | --- |
| `mcp_crm_automations_create` | Write | Create a new automation DEFINITION. |
| `mcp_crm_automations_get` | Read | Fetch a single automation by its numeric id, including its step graph. |
| `mcp_crm_automations_list` | Read | List marketing automations created by the authenticated user. |
| `mcp_crm_automations_set_steps` | Write | Wire (replace) the step graph of an existing automation so it actually runs a trigger then condition/action steps. |
| `mcp_crm_automations_update` | Write | Update an existing automation DEFINITION by its numeric id. |

## Transactional email

| Tool | Access | What it does |
| --- | --- | --- |
| `mcp_crm_smtp_events_list` | Read | List SMTP delivery events (sends, deliveries, opens, bounces, failures). |
| `mcp_crm_txn_email_list` | Read | List transactional (one-to-one) email send logs. |
| `mcp_crm_txn_email_send` | Sends email | Send a single transactional email to ONE recipient. |

## Senders and domains

| Tool | Access | What it does |
| --- | --- | --- |
| `mcp_crm_senders_get` | Read | Fetch a single sending identity (verified sender) by its numeric id. |
| `mcp_crm_senders_list` | Read | List the sending identities (verified senders) configured. |
| `mcp_crm_sending_domains_list` | Read | List the account's active, verified sending domains that a campaign can send from. |

## Reports

| Tool | Access | What it does |
| --- | --- | --- |
| `mcp_crm_reports_domain` | Read | Paginated domain-deliverability report: per recipient-domain delivery, open, click, bounce, drop, spam, and abuse counts. |

## Images

| Tool | Access | What it does |
| --- | --- | --- |
| `mcp_crm_assets_image_import` | Write | Re-host an image from a public https URL onto this tenant's own CDN and return the hosted URL. |
| `mcp_crm_assets_image_upload` | Write | Store a base64-encoded image on this tenant's own CDN and return the hosted URL. |
