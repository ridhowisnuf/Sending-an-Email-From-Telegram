# My n8n Project

This repository contains n8n workflow automations for document management and email communications.

## Workflows

### upload_and_send_email.json
An automated workflow that processes incoming Telegram messages and sends documents via email.

**Workflow Description:**
When a text message is received through a Telegram chatbot, the workflow performs the following actions:
1. Translates the incoming message content
2. Searches for PDF files in a specified Google Drive folder based on the translated message
3. Automatically generates an email body with relevant content
4. Attaches the PDF file(s) found in Google Drive
5. Sends the email through Brevo (formerly Sendinblue)

**Use Cases:**
- Automated document retrieval and distribution
- Multilingual customer support with document delivery
- Streamlined file sharing through conversational interfaces

## Prerequisites

Before using this workflow, ensure you have:
- An active n8n instance (cloud or self-hosted)
- A Telegram Bot Token
- A Brevo (Sendinblue) account with API access
- Google Cloud Platform account with the following APIs enabled:
  - Google Drive API
  - Google Sheets API (if applicable)
  - Other Google services as needed

## Setup Instructions

### 1. Import the Workflow
1. Log in to your n8n instance
2. Navigate to **Workflows** in the main menu
3. Click on **Import from File** or **Import from URL**
4. Select the `upload_and_send_email.json` file from this repository
5. The workflow will be imported into your n8n instance

### 2. Configure Credentials

You need to set up the following credentials in n8n:

#### Telegram
- Go to **Credentials** in n8n
- Create a new **Telegram API** credential
- Enter your Bot Token (obtain from [@BotFather](https://t.me/botfather) on Telegram)

#### Brevo (Email Service)
- Create a new **Brevo API** credential
- Enter your Brevo API key (found in your Brevo account settings)

#### Google Cloud API
- Create a new **Google Service Account** credential or **OAuth2** credential
- Configure the following scopes:
  - `https://www.googleapis.com/auth/drive` (for Google Drive access)
  - `https://www.googleapis.com/auth/spreadsheets` (for Google Sheets, if needed)
- Upload your service account JSON key or complete the OAuth2 authentication flow

### 3. Configure Workflow Parameters

After importing, review and update the following within the workflow:
- **Google Drive Folder ID**: Specify the folder where PDF files are stored
- **Email sender information**: Configure the "from" email address
- **Email recipient settings**: Set up default recipients or dynamic recipient logic
- **Translation settings**: Configure the translation service and target language

### 4. Test the Workflow

1. Use the **Execute Workflow** button in n8n to test manually
2. Send a test message to your Telegram bot
3. Verify that:
   - The message is received and translated correctly
   - The correct PDF is located in Google Drive
   - The email is composed with proper content
   - The email is successfully sent through Brevo

### 5. Activate the Workflow

Once testing is complete:
1. Click the **Inactive** toggle at the top of the workflow
2. The workflow will change to **Active** status
3. The automation will now run automatically when triggered by Telegram messages

## Troubleshooting

**Common Issues:**
- **Authentication errors**: Verify all API credentials are correctly configured and have not expired
- **File not found**: Ensure the Google Drive folder ID is correct and the service account has access permissions
- **Email delivery failures**: Check Brevo API limits and verify sender email is authorized
- **Translation errors**: Confirm translation API credentials and language codes are valid

## Security Considerations

- Never commit credential files or API keys to this repository
- Use n8n's built-in credential management system
- Ensure Google Drive folder permissions are properly restricted
- Regularly rotate API keys and tokens
- Review Brevo email logs for suspicious activity

## Contributing

Feel free to fork this repository and submit pull requests with improvements or additional workflows.

## License

This project is provided as-is for personal and commercial use.

## Support

For issues related to:
- **n8n platform**: Visit [n8n community forum](https://community.n8n.io/)
- **This workflow**: Open an issue in this repository
- **API services**: Contact respective service providers (Telegram, Brevo, Google Cloud)

---

**Last Updated:** February 2026
