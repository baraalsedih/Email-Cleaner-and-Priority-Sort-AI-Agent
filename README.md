# Email Cleaner & Priority Sort AI Agent

An intelligent n8n workflow that automatically classifies, organizes, and prioritizes your Gmail emails using AI. This workflow runs daily to help you maintain a clean and organized inbox by categorizing emails into Important, Can Wait, or Spam categories.

## 🚀 Features

- **AI-Powered Classification**: Uses Google Gemini to intelligently categorize emails
- **Automatic Gmail Labeling**: Applies appropriate labels based on priority
- **Discord Notifications**: Get notified about important emails instantly
- **Scheduled Processing**: Runs automatically every day at 8 AM
- **Smart Summarization**: Provides concise summaries of email content

## 📋 How It Works

1. **Schedule Trigger**: Runs daily at 8 AM
2. **Fetch Emails**: Retrieves recent Gmail messages
3. **AI Analysis**: Google Gemini analyzes each email and classifies it as:
   - **Important**: Actionable or high-priority (work, clients, deadlines, bills)
   - **Can Wait**: Low-priority (newsletters, notifications, social media)
   - **Spam**: Unwanted, promotional, or irrelevant content
4. **Auto-Labeling**: Applies Gmail labels based on classification
5. **Notifications**: Sends Discord notification for important emails

## 🛠️ Prerequisites

Before importing this workflow, you'll need:

- n8n instance (cloud or self-hosted)
- Gmail account with API access
- Google Gemini API key
- Discord webhook (optional, for notifications)

## 📥 Installation

### 1. Import the Workflow

1. Download the `Email Cleaner & Priority Sort AI Agent.json` file
2. In your n8n instance, go to **Workflows**
3. Click **Import from file** or **Import from clipboard**
4. Select the downloaded JSON file

### 2. Set Up Required Credentials

#### Gmail OAuth2 Setup
1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Create a new project or select existing one
3. Enable Gmail API
4. Create OAuth2 credentials
5. In n8n, create a new **Gmail OAuth2** credential
6. Follow the OAuth flow to authorize access

#### Google Gemini API Setup
1. Go to [Google AI Studio](https://makersuite.google.com/app/apikey)
2. Create a new API key
3. In n8n, create a new **Google Gemini (PaLM) API** credential
4. Enter your API key

#### Discord Webhook Setup (Optional)
1. In your Discord server, go to **Server Settings** → **Integrations**
2. Click **Create Webhook**
3. Copy the webhook URL
4. In n8n, create a new **Discord Webhook** credential
5. Paste the webhook URL

### 3. Configure Gmail Labels

Create these labels in your Gmail account:
- **Important** (or any custom name for high-priority emails)
- **Can Wait** (or any custom name for low-priority emails)
- The workflow will automatically use the **Spam** label

After creating labels, you'll need to update the label IDs in the workflow:
1. Go to Gmail
2. Get label IDs from the URL when viewing each label
3. Update the `labelIds` in the respective Gmail nodes

### 4. Customize Settings

#### Schedule Configuration
- Default: Daily at 8 AM
- To change: Edit the **Schedule Trigger** node
- Options: Hourly, daily, weekly, or custom cron expression

#### AI Prompt Customization
- Edit the **Basic LLM Chain** node to modify classification criteria
- Adjust categories or add new classification rules
- Customize the summary format

## 🔧 Configuration Options

### Email Filtering
You can modify the Gmail node to filter emails by:
- Date range (only process recent emails)
- Sender domains
- Subject keywords
- Unread status

### Classification Categories
The default categories are:
- **Important**: Work, clients, deadlines, bills
- **Can Wait**: Newsletters, notifications, social media
- **Spam**: Unwanted, promotional content

Modify the AI prompt to add custom categories or change classification logic.

### Notification Settings
- **Discord**: Sends summary of important emails
- **Email**: Could be extended to send email notifications
- **Slack**: Could be adapted for Slack notifications

## 📊 Workflow Structure

<img width="1280" height="654" alt="image" src="https://github.com/user-attachments/assets/5f06e349-1fc0-4250-b3b6-1699eb7d907a" />


## 🔒 Security & Privacy

- **No credentials are stored in the workflow file** - only references
- **Emails are processed locally** through your n8n instance
- **AI processing** uses Google Gemini API (check their privacy policy)
- **OAuth tokens** are securely managed by n8n

## 🐛 Troubleshooting

### Common Issues

1. **"Failed to parse cleaned Gemini response"**
   - The AI response format might be inconsistent
   - Check the Code node for JSON parsing errors
   - Consider adding more robust error handling

2. **Gmail API Rate Limits**
   - Reduce the frequency of the schedule trigger
   - Add delays between API calls
   - Implement exponential backoff

3. **Label IDs Not Working**
   - Ensure Gmail labels exist
   - Update label IDs in the workflow
   - Check Gmail API permissions

4. **Discord Notifications Not Sending**
   - Verify webhook URL is correct
   - Check Discord channel permissions
   - Test webhook independently

### Debug Mode
1. Enable debug mode in n8n
2. Run the workflow manually
3. Check execution logs for detailed error messages
4. Test individual nodes to isolate issues

## 📈 Customization Ideas

### Extensions
- **Sentiment Analysis**: Add emotion detection to emails
- **Auto-Reply**: Generate AI responses for certain email types
- **Calendar Integration**: Create calendar events from meeting emails
- **CRM Integration**: Log important emails to your CRM system
- **Multi-Language Support**: Handle emails in different languages

### Advanced Features
- **Learning Mode**: Train the AI on your email patterns
- **Batch Processing**: Handle large volumes of emails efficiently
- **Custom Webhooks**: Trigger actions based on email content
- **Integration Hub**: Connect with other automation tools

## 🤝 Contributing

Feel free to:
- Report bugs or issues
- Suggest improvements
- Submit pull requests
- Share your customizations

## 📄 License

This workflow is open source and available under the MIT License.

## 🙏 Acknowledgments

- Built with [n8n](https://n8n.io/) - Fair-code workflow automation
- Powered by [Google Gemini](https://ai.google.dev/) for AI classification
- Inspired by the need for better email management

---

## 📞 Support

If you need help:
1. Check the [n8n community forum](https://community.n8n.io/)
2. Read the [n8n documentation](https://docs.n8n.io/)
3. Open an issue in this repository

**Happy email organizing! 📧✨**
