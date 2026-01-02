        # Baron Bot Template

🤖 **Discord Bot for Demonic Scans Wave Monitoring**

## Overview

Baron Bot is a Discord bot that monitors the Demonic Scans website for Baron and Dragon King spawn events. It sends automatic alerts to your Discord server with customizable mentions and channels.

### Features

✅ **Real-time Wave Monitoring** - Continuously checks Demonic Scans for Baron/Dragon King status
✅ **Automatic Alerts** - Pings when bosses spawn
✅ **Status Command** - View current wave progress anytime with `/status`
✅ **Customizable** - Set alert channel and mention role with simple commands
✅ **Role-Based Access** - Restrict admin commands to authorized roles
✅ **24/7 Operation** - Runs continuously on Railway servers
✅ **Cloudflare Bypass** - Handles website protection automatically

---

## Table of Contents

1. [Prerequisites](#prerequisites)
2. [Discord Bot Setup](#discord-bot-setup)
3. [GitHub & Railway Setup](#github--railway-setup)
4. [Configuration](#configuration)
5. [Commands](#commands)
6. [Troubleshooting](#troubleshooting)

---

## Prerequisites

Before starting, you need:

- **Discord Server** - Where you want to deploy the bot
- **GitHub Account** - To fork and manage the code
- **Railway Account** - For 24/7 bot hosting (free tier available)
- **Node.js** - For local testing (optional)

---

## Discord Bot Setup

### Step 1: Create Discord Application

1. Go to [Discord Developer Portal](https://discord.com/developers/applications)
2. Click **"New Application"** button
3. Enter bot name (e.g., "Baron Bot")
4. Accept Terms of Service
5. Click **"Create"**

### Step 2: Add Bot to Application

1. Click **"Bot"** tab on the left
2. Click **"Add Bot"**
3. Under the TOKEN section, click **"Copy"** to copy your bot token
4. **SAVE THIS TOKEN SECURELY** - You'll need it later

⚠️ **Never share your bot token publicly!**

### Step 3: Configure Bot Permissions

1. Go to **"Bot"** section
2. Enable these **Intents:**
   - ✅ GUILDS
   - ✅ GUILD_MESSAGES
   - ✅ GUILD_MEMBERS
   - ✅ MESSAGE_CONTENT

3. Scroll to **"TOKEN PERMISSIONS"** section
4. Select these permissions:
   - ✅ Send Messages
   - ✅ Embed Links
   - ✅ Read Message History
   - ✅ Use Application Commands
   - ✅ Manage Messages (optional, for pinning)

### Step 4: Generate OAuth2 Invite Link

1. Go to **"OAuth2" → "URL Generator"**
2. Under SCOPES, select:
   - ✅ bot
   - ✅ applications.commands
3. Under PERMISSIONS, select:
   - ✅ Send Messages
   - ✅ Embed Links
   - ✅ Read Message History  
4. Copy the generated URL
5. Open it in your browser and select your server
6. Authorize the bot

---

## GitHub & Railway Setup

### Step 1: Fork/Clone This Repository

```bash
git clone https://github.com/PhotonX4/baron-bot-template.git
cd baron-bot-template
```

### Step 2: Prepare Environment File

1. Create a `.env` file in the root directory
2. Add your Discord bot token:

```
DISCORD_TOKEN=your_bot_token_here
```

⚠️ **IMPORTANT**: Add `.env` to `.gitignore` to prevent leaking tokens!

### Step 3: Install Dependencies

```bash
npm install discord.js dotenv
```

### Step 4: Deploy to Railway

1. Go to [Railway.app](https://railway.app)
2. Sign up with GitHub (easier)
3. Click **"Create Project"**
4. Select **"Deploy from GitHub repo"**
5. Authorize Railway and select this repository
6. Railway will auto-detect Node.js
7. Add environment variable:
   - Name: `DISCORD_TOKEN`
   - Value: Your bot token (copy from Discord Developer Portal)
8. Click **"Deploy"**

**Railway will now run your bot 24/7!**

---

## Configuration

### Bot Roles Setup

The bot restricts admin commands to these roles:
- Council Elders
- Commanders
- Dukes
- Overseer
- Emperor

**To allow users to use admin commands:**
1. Create or use existing roles in Discord
2. Make sure role names **exactly match** the list above
3. Assign roles to users you want to give access

### Code Configuration

Optional: Edit `bot.js` to customize:
- Monitored website URL (line ~20)
- Baron kill threshold (line ~190)
- Update intervals (30 min and 30 sec)
- Mention roles

---

## Commands

### `/status`
**Description:** View current wave status
**Access:** Everyone
**Usage:** `/status`
**Shows:**
- General kills (0/10,000)
- Baron kills (0/3)
- Dragon King spawn status
- Active monsters list

### `/set_channel`
**Description:** Set which channel receives alerts
**Access:** Admin roles only
**Usage:** `/set_channel #channel-name`
**Example:** `/set_channel #wave-announcements`

### `/set_role`
**Description:** Set which role gets mentioned in alerts
**Access:** Admin roles only
**Usage:** `/set_role @role-name`
**Example:** `/set_role @everyone`

---

## How It Works

### Monitoring
- ✅ Checks Demonic Scans every 30 seconds
- ✅ Detects when Barons spawn
- ✅ Tracks when all 3 barons are defeated
- ✅ Alerts when Dragon King spawns

### Alerts
- ✅ Sends formatted embed messages
- ✅ Mentions configured role (@everyone by default)
- ✅ Sends status update every 30 minutes
- ✅ Shows active monsters in real-time

---

## Troubleshooting

### Bot not responding to commands
- ✅ Check bot has permission to Send Messages in the channel
- ✅ Verify bot has GUILD_MEMBERS and MESSAGE_CONTENT intents enabled
- ✅ Ensure bot is online (check Railway deployment logs)

### Can't use admin commands
- ✅ Verify your role name matches exactly: Council Elders, Commanders, Dukes, Overseer, or Emperor
- ✅ Check role is assigned to your user
- ✅ Ensure bot has higher role in role hierarchy

### Bot keeps crashing
- ✅ Check Railway logs for error messages
- ✅ Verify DISCORD_TOKEN environment variable is set
- ✅ Make sure .env file is NOT committed to GitHub

### No alerts being sent
- ✅ Run `/set_channel` to set alert channel
- ✅ Verify bot has Send Messages permission in that channel
- ✅ Check if website is accessible (Demonic Scans)

---

## Security Notes

⚠️ **IMPORTANT:**
- Never commit `.env` file to GitHub
- Never share your Discord bot token
- Keep your Railway environment variables private
- Use strong passwords for all accounts

---

## File Structure

```
baron-bot-template/
├── bot.js              # Main bot code
├── .env.example        # Example environment file
├── .gitignore          # Git ignore patterns
├── package.json        # Dependencies
├── package-lock.json   # Locked versions
└── README.md           # This file
```

---

## Support & Issues

For issues, bugs, or feature requests:
1. Check this README first
2. Review Railway logs for errors
3. Verify Discord permissions
4. Check bot token is correct

---

## License

This project is provided as-is for educational and community use.

---

## Credits
**Made by PhantomX**

Built with:
- [Railway.app](https://railway.app)
- [Node.js](https://nodejs.org/)

---

## Keep Your Bot Running

✅ Bot updates automatically when you push to GitHub
✅ Railway re-deploys within seconds
✅ No manual server management needed
✅ Runs 24/7 without your computer

**Happy monitoring! 🎖️**
