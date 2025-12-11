🚀 CampaignOS: AI Automation Command Center
A full-stack, low-code automation suite for B2B outreach. This project provides a modern dashboard interface to manage CSV leads, trigger AI-written cold emails (via Google Gemini), and deploy AI Voice Agents (via VAPI) for outbound calling—all powered by n8n workflows.
✨ Features
●📊 Data Ingestion: Upload CSV files, automatically creating a Google Sheet database.
●🧹 Data Validation: Auto-detects missing emails or phone numbers and flags them for manual review.
●📧 AI Email Agent: Uses Google Gemini to draft personalized, context-aware emails based on lead data and sends them via Gmail.
●📞 AI Voice Agent: Deploys VAPI (GPT-4o) voice assistants to conduct outbound discovery calls.
●⚡ Real-Time Dashboard: Live status updates using a Single Page Application (SPA) architecture with no external database required.

🏗️ Architecture
●Frontend: HTML5, CSS3 (Inter font), Vanilla JavaScript (Fetch API).
●Backend / Orchestration: n8n (3 Synchronous Workflows).
●Database: Google Sheets.
●AI Services:
○Text Generation: Google Gemini (PaLM).
○Voice/Telephony: VAPI.ai + Twilio.
●Email Service: Gmail (via OAuth2).
├── workflows/
│   ├── 1_Upload_Leads_Workflow.json      # Handles CSV parsing & Sheet creation
│   ├── 2_Send_Email_Workflow.json        # AI writing & Gmail sending
│   └── 3_Make_Call_Workflow.json         # Phone formatting & VAPI triggering
├── website/
│   └── index.html                        # The main dashboard interface
└── README.md

⚙️ Prerequisites
Before installing, ensure you have:
1.n8n Instance: Self-hosted or n8n Cloud (Active account).
2.VAPI Account: You need your Private API Key, an Assistant ID, and a Phone Number ID.
3.Google Cloud Project: Enabled APIs for Google Sheets and Gmail.
4.Google AI Studio: An API Key for Gemini.

🚀 Installation & Setup
Phase 1: n8n Configuration
1.Import Workflows:
○Download the JSON files from the workflows/ folder.
○In n8n, go to Menu > Import from File and import all three.
2.Configure Credentials:
○Google Sheets & Gmail: Set up OAuth2 credentials in n8n nodes.
○Google Gemini: Add your API Key to the Gemini Chat Model node.
○VAPI: In Workflow 3 ("Make Call"), open the HTTP Request node and add a Header Auth credential (Authorization: Bearer YOUR_SECRET_KEY).
3.Update Hardcoded IDs (Crucial):
○Workflow 3 (Call): Open the HTTP Request node. inside the JSON Body, replace YOUR_ASSISTANT_ID_HERE and YOUR_PHONE_NUMBER_ID_HERE with your actual IDs from the VAPI Dashboard.
4.Activate Workflows:
○Toggle the Active switch to Green (On) for ALL three workflows. This generates your Production Webhook URLs.
Phase 2: Website Configuration
1.Open the website/index.html file in any code editor (VS Code, Notepad).
2.Locate the WEBHOOKS constant near the bottom of the script (approx line 220).
3.Replace the placeholder URLs with your Production Webhook URLs from n8n:
const WEBHOOKS = {
    upload: "https://your-n8n-instance/webhook/Upload",
    email: "https://your-n8n-instance/webhook/SendEmail",
    call: "https://your-n8n-instance/webhook/Call"
};

4.Save the file.

📖 Usage Guide
1.Launch: Open index.html in your browser (Chrome/Edge recommended).
2.Upload:
○Enter a Campaign Name (e.g., "Tech Leads Q4").
○Select a CSV file containing columns like first_name, company_name, email, phone.
○Click Upload. Wait for the "Needs Review" table to populate.
3.Email Campaign:
○Navigate to the Email Campaign tab.
○Click Start Campaign. The system will send an email to the next pending lead and update the stats instantly.
4.Voice Agent:
○Navigate to the Voice Agent tab.
○Click Initiate Dialing. The system will trigger VAPI to call the next valid number.

🔧 Troubleshooting
🛑 1. "Connection Error" on the Website
●Cause: The website cannot reach n8n.
●Fix: Ensure your n8n workflows are set to Active. Check that you pasted the Production URL (not the Test URL) into the HTML code.
🛑 2. "Workflow Error" (400 Bad Request)
●Cause: VAPI rejected the call request.
●Fix:
○Check if your VAPI daily spending limit is reached.
○Ensure the lead has a valid phone number (10+ digits).
○Verify the assistantId and phoneNumberId in Workflow 3 are correct.
🛑 3. "CORS Error" in Browser Console
●Cause: The browser blocked the response.
●Fix: In Workflow 3, check the final Respond to Webhook node. Ensure it has the header: Access-Control-Allow-Origin: *.
🛑 4. Dashboard Stats Not Updating
●Cause: Google Sheet status mismatch.
●Fix: The code expects specific statuses. Ensure your Google Sheet headers are strictly Email status and Call status. The internal JS handles capitalization (Sent vs sent), but the column header must exist.

📄 License
This project is open-source. Feel free to modify and distribute.

Built with ❤️ using n8n and AI.
