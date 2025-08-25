# Inventory Stock Assistant with n8n

Automate your inventory management through conversational AI. This project lets users query and update stock levels using natural language, while the workflow reads from and writes to Google Sheets in real time.

![Inventory Stock Assistant Cover](./images/Inventory%20Stock%20Assistant%20Cover.png)

---

## Table of Contents

- [Overview](#overview)
- [How It Works](#how-it-works)
  - [Workflow Steps](#workflow-steps)
- [Benefits](#benefits)
- [Requirements](#requirements)
- [Setup Instructions](#setup-instructions)
  - [1. Clone or Import Workflow](#1-clone-or-import-workflow)
  - [2. Connect Google Gemini](#2-connect-google-gemini)
  - [3. Connect Google Sheets](#3-connect-google-sheets)
  - [4. Configure the Chat Trigger](#4-configure-the-chat-trigger)
  - [5. Test the Workflow](#5-test-the-workflow)
- [Customization](#customization)
  - [Inventory Sheet Structure](#inventory-sheet-structure)
  - [Agent Capabilities and Guardrails](#agent-capabilities-and-guardrails)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

---

## Overview

**Inventory Stock Assistant** is an n8n workflow that brings a chat-first experience to inventory management. It:

- Enables natural language queries like “What’s the stock for Product A?”
- Updates stock levels or low-stock thresholds on command
- Uses Google Sheets as the single source of truth for inventory
- Leverages an AI Agent (Google Gemini) with short-term memory for smooth conversations

---

## How It Works

![Inventory Stock Assistant Workflow](./images/Inventory%20Stock%20Assistant%20Workflow.png)

### Workflow Steps

1. **Trigger: When chat message received**
   - Public chat endpoint accepts user messages and starts the workflow.

2. **AI Agent with memory + Google Gemini chat model**
   - The agent interprets user intent and decides whether to fetch or update inventory.
   - A memory buffer preserves recent context for a smoother conversation.

3. **Google Sheets operations (read/update)**
   - Reads current stock data on queries.
   - Updates rows when the user requests stock changes or threshold edits.

---

## Benefits

- **Natural language inventory queries and updates**
- **Automates inventory data handling** with reliable read/write actions
- **Improves efficiency and accuracy** in stock management
- **Seamless AI + spreadsheet integration** for instant results

---

## Requirements

- [n8n](https://n8n.io/) installation or cloud account
- Google account with:
  - Access to Google Sheets (inventory spreadsheet)
  - Access to the Gemini API (for the chat model)
- An inventory sheet similar to the sample in this repo

---

## Setup Instructions

### 1. Clone or Import Workflow

- Download or import the attached `Inventory Stock Assistant.json` into your n8n instance (Visual or Desktop).

### 2. Connect Google Gemini

- Add your Gemini API credentials in n8n and link them to the AI language model node.
- Choose your preferred Gemini chat model and defaults.

### 3. Connect Google Sheets

- Add Google Sheets OAuth credentials in n8n.
- In the Google Sheets tool nodes, set the `documentId` and `sheetName` to your inventory sheet.
- Ensure your account has read/write permissions.

### 4. Configure the Chat Trigger

- The Chat Trigger node is set to public in the workflow. Use the provided webhook URL or the built-in n8n Chat UI to interact.
- Optionally protect access by restricting who can reach the public endpoint.

### 5. Test the Workflow

- Send a message like: “What is the stock for Product ID 1001?”
- Try an update: “Set Current Stock of Product ID 1001 to 45.”
- Confirm that the Google Sheet reads/updates correctly and the agent replies with a concise confirmation.

---

## Customization

### Inventory Sheet Structure

Your sheet should look similar to `data/Inventory Data.csv` and the example below.

![Inventory Spreadsheet Example](./images/Inventory%20Spreadsheet.png)

Recommended columns:

- **Product ID**: Unique identifier
- **Product Name**: Descriptive name
- **Variant**: Size/color or other variant
- **Current Stock**: Current quantity on hand
- **Low Stock Threshold**: Minimum acceptable quantity
- (Optional) **row_number**: Used for precise row matching during updates

### Agent Capabilities and Guardrails

The agent is scoped to two actions only:

- Provide inventory details (ID, name, variant, current stock, low-stock threshold)
- Update inventory records (stock levels or thresholds)

If a request falls outside of these, it politely declines and reminds users of supported actions.

---

## Troubleshooting

- **Google Sheets read/write errors**: Verify OAuth credentials, `documentId`, `sheetName`, and sharing permissions.
- **Gemini model errors**: Check API keys/quotas and selected model configuration.
- **No response to chat**: Confirm the chat trigger’s public URL and that the workflow is active (or run manually for tests).
- **Unexpected updates**: Ensure the correct matching column (e.g., `row_number` or `Product ID`) is configured in the update node.

---

## Contributing

Contributions and suggestions are welcome. Fork the repo, submit issues, or open pull requests for improvements.

---

## License

This project is licensed under the MIT License.

---

## Contact

- **Email:** nebeyoumusie@gmail.com
- **LinkedIn:** [LinkedIn](https://www.linkedin.com/in/nebeyou-musie)
- **X(Twitter):** [X](https://x.com/NebeyouMusie)
- **Upwork:** [Upwork](https://www.upwork.com/freelancers/~017ff01729e3cd26e0?mp_source=share)
- **My Agency:** [Fuzion Tech Website](https://fuzion-tech.com/) or [Fuzion Tech on Upwork](https://www.upwork.com/agencies/1948388369189366041/)

---

**Skills & Technologies:**  
`n8n`, `Inventory Management`, `AI Agent Development`, `Google Sheets Automation`, `Chatbot`

---

**Enjoy conversational inventory management with AI-powered assistance!**

---

> _For any issues, please contact the project maintainer or open an issue on your workflow repository._


