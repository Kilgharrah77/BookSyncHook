# Privacy Policy - BookSyncHook

**Last updated: March 9, 2026**

## Overview

BookSyncHook is a browser extension that sends bookmark change events (create, update, delete, move) to a user-configured webhook URL. The extension is designed with privacy in mind and processes data only as explicitly configured by the user.

## Data Collection

### What data is collected
- **Bookmark metadata**: Title, URL, folder name, and bookmark ID when a bookmark event occurs
- **No personal data**: The extension does not collect names, email addresses, browsing history, or any other personal information
- **No analytics**: The extension does not include any tracking, analytics, or telemetry

### What data is stored locally
- **Webhook URL**: The URL you configure in the extension settings
- **Event preferences**: Which bookmark events are enabled
- **Delay setting**: The configured delay time for new bookmarks

All settings are stored locally in your browser using `chrome.storage.sync` and are never transmitted to any third party.

## Data Transmission

### Where data is sent
Bookmark event data is sent **exclusively** to the webhook URL that **you** configure in the extension settings. No data is sent anywhere else.

### What is transmitted
When a bookmark event occurs and matches your configured events, the following JSON payload is sent to your webhook URL:

```json
{
  "source": "BookSyncHook",
  "event": "onCreated",
  "timestamp": "2026-01-01T00:00:00.000Z",
  "data": {
    "id": "bookmark_id",
    "bookmark": {
      "title": "Bookmark Title",
      "url": "https://example.com"
    },
    "folderName": "Folder Name"
  }
}
```

### No default destination
If no webhook URL is configured, **no data is transmitted at all**. The extension is completely inactive until you provide a webhook URL.

## Permissions

### Why we need these permissions

- **`bookmarks`**: Required to listen for bookmark create, update, delete, and move events. This is the core functionality of the extension.
- **`storage`**: Required to save your settings (webhook URL, event preferences, delay) locally in the browser.
- **`host_permissions: <all_urls>`**: Required to send HTTP POST requests to any webhook URL you configure. This is necessary because webhook URLs can be hosted on any domain (e.g., your self-hosted n8n instance, Zapier, Make, etc.).

## Third Parties

- The extension does **not** share data with any third party
- The extension does **not** include any third-party libraries, SDKs, or analytics
- The only network request made is to the webhook URL you configure

## Data Retention

- No data is stored on external servers by the extension
- Local settings can be cleared by removing the extension
- Bookmark data is sent in real-time and not cached or stored by the extension

## User Control

You have full control over:
- **Which events** trigger a webhook (configurable in settings)
- **Where data is sent** (your webhook URL)
- **When data is sent** (configurable delay for new bookmarks)
- **Stopping all data transmission** by removing the webhook URL or disabling the extension

## Children's Privacy

This extension is not directed at children under 13 and does not knowingly collect any data from children.

## Changes to This Policy

If this privacy policy is updated, the changes will be reflected in the "Last updated" date above. Significant changes will be communicated through the extension's Chrome Web Store listing.

## Contact

For questions about this privacy policy or the extension:
- **GitHub**: https://github.com/czlonkowski/BookSyncHook
- **Email**: privacy@nexo7.cloud

## Open Source

BookSyncHook is open source. You can review the complete source code to verify our privacy practices.
