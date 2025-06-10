# 🕵️ Phishing Detection & Simulation with Gophish + Custom HTML Templates

> ⚠️ **Disclaimer**: This project is for **educational and ethical** purposes **only**. Do not attempt to send phishing emails or run campaigns on real users or organizations without **informed consent and written permission**.

---

## 🎯 Project Objective

This project simulates a phishing email campaign using [Gophish](https://getgophish.com/) to demonstrate:
- The structure and flow of a phishing attack
- How HTML email templates are crafted
- How credentials are harvested in a simulation
- Reporting & detection of click-throughs and data entry

It also includes **tips for identifying phishing attempts** and steps to build awareness in a workplace setting.

---

## 🛠️ Tools Used

| Tool         | Purpose                                    |
|--------------|--------------------------------------------|
| Gophish      | Phishing simulation framework              |
| HTML/CSS     | Email and landing page templates           |
| Python       | For log parsing and detection simulation   |
| Nginx/Apache | To host the landing page locally           |
| Docker       | Optional Gophish deployment                |

---

## 📦 Folder Structure
├── email_templates/
│ └── fake_microsoft_update.html
├── landing_pages/
│ └── login_clone.html
├── detection/
│ └── analyze_logs.py
├── screenshots/
├── gophish_config/
│ └── campaign_example.json
├── README.md


---

## 🚀 Quick Start

### 🔧 Install Gophish
```bash
wget https://github.com/gophish/gophish/releases/download/v0.12.1/gophish-v0.12.1-linux-64bit.zip
unzip gophish*.zip
cd gophish
./gophish

Access the dashboard:
📍 https://localhost:3333
(Default username: admin@gophish.io, password: gophish)

📨 Create a Campaign
          -Upload email_templates/fake_microsoft_update.html in the Email Template section.
          -Set up a Landing Page using landing_pages/login_clone.html
          -Configure Sending Profile (can use SMTP testing tool like MailHog or Mailtrap)
          -Launch campaign to your test users (your own lab emails)

🕸️ Example: Fake Microsoft Login
          -Mimics Microsoft login page
          -Harvests email & password inputs
          -Sends data to Gophish for reporting

🧠 Phishing Detection Tips
🔍 Things to look for:
          -Mismatched URLs (hover to preview)
          -Urgent call-to-action messages ("Click now to avoid account lock")
          -Poor grammar or misspelled brand names
          -Unexpected attachments or requests for credentials

🧪 Detection Script (Example)
python
Copy
Edit
# analyze_logs.py
with open('gophish_logs.csv') as f:
    for line in f:
        if "Submitted Data" in line:
            print("⚠️ Possible credential entry detected:", line)

✅ Legal Usage
          -Use only in closed lab environments or internal training
          -Do not send phishing emails to external or public addresses
