# B2B Lead Generation & Outreach Automation

This n8n workflow automates the entire B2B lead generation and outreach process, from prospect targeting to personalized email creation.

## Workflow Overview
![Workflow Demo]([https://imgur.com/a/s1Et5ZY](https://i.imgur.com/iRN5TAR.png))

<!-- Insert your video here -->
<!-- For GitHub README, use: ![Video Description](path/to/video.mp4) -->
<!-- Or for YouTube: [![Video Title](https://img.youtube.com/vi/VIDEO_ID/0.jpg)](https://www.youtube.com/watch?v=VIDEO_ID) -->

## Step-by-Step Process

### Step 1: Prospect Input Form
- **Node**: Form Trigger
- **Purpose**: Collects target prospect criteria
- **Input Fields**: Industry, Location, Job Title, Company Size
- **Output**: Structured prospect description

### Step 2: Apollo URL Generation
- **Node**: LangChain Agent with DeepSeek AI
- **Purpose**: Converts prospect criteria into targeted Apollo.io search URLs
- **Logic**: 
  - Maps industries to specific Apollo filter IDs
  - Handles hospitality, restaurants, and food & beverage industries specially
  - Generates search URLs with proper parameters

### Step 3: Lead Scraping
- **Node**: HTTP Request to Apify API
- **Purpose**: Executes the Apollo search and extracts lead data
- **Features**:
  - Fetches up to 20 leads per search
  - Excludes contacts without email addresses
  - Gets verified email contacts

### Step 4: Data Storage
- **Node**: Google Sheets
- **Purpose**: Saves extracted leads to spreadsheet
- **Fields Saved**:
  - Full name, email, LinkedIn URL
  - Job title, company, industry
  - Location, phone, website
  - Seniority level and timestamp

### Step 5: Email Deduplication
- **Node**: Code Processor
- **Purpose**: Prevents duplicate outreach
- **Logic**:
  - Compares new leads against existing email tracker
  - Filters out already-contacted emails
  - Validates email format and completeness

### Step 6: Email Content Generation
- **Node**: LangChain with DeepSeek AI
- **Purpose**: Creates personalized outreach emails
- **Customization**:
  - Industry-specific messaging
  - Role-targeted value propositions
  - Professional HTML formatting
  - HostBooks branding and logo

### Step 7: Gmail Draft Creation
- **Node**: Gmail Integration
- **Purpose**: Creates email drafts in Gmail
- **Features**:
  - Professional subject lines
  - HTML-formatted content
  - Ready for manual review before sending

### Step 8: Campaign Tracking
- **Node**: Google Sheets Email Tracker
- **Purpose**: Records all outreach activities
- **Fields Tracked**:
  - Contact information
  - Campaign details
  - Sent status and timestamps
  - Follow-up requirements

### Step 9: Notifications & Reporting
- **Nodes**: Telegram Integration
- **Purpose**: Real-time campaign updates
- **Notifications Sent**:
  - Lead fetch confirmation
  - Email generation status
  - Campaign completion summary
  - Performance metrics

## Key Features

### 🤖 AI-Powered Intelligence
- Dynamic Apollo URL generation based on prospect criteria
- Industry-aware email content creation
- Personalized messaging for different roles

### 🔄 Smart Deduplication
- Prevents duplicate outreach across campaigns
- Maintains comprehensive email history
- Ensures professional communication standards

### 📊 Comprehensive Tracking
- Full campaign performance analytics
- Real-time progress monitoring
- Detailed lead quality assessment

### 🎯 Targeted Outreach
- Industry-specific value propositions
- Role-relevant pain point addressing
- Location-aware messaging

## Setup Requirements

### API Credentials Needed:
- Apollo.io Account
- Apify API Key
- Google Sheets OAuth
- Gmail OAuth
- Telegram Bot Token
- DeepSeek AI API Key

### Configuration:
1. Set up all API credentials in n8n
2. Configure Google Sheets templates
3. Set up Telegram chat IDs for notifications
4. Customize email templates for your industry

## Output Deliverables

1. **Targeted Lead Lists** in Google Sheets
2. **Personalized Email Drafts** in Gmail
3. **Comprehensive Campaign Analytics**
4. **Real-time Progress Notifications**

This workflow streamlines B2B outreach from hours to minutes while maintaining personalization and professional standards.

---

