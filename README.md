# 📧 CI/CD Failure Notification System using GitHub Actions and Python

Automate email notifications for failed CI/CD workflows using **GitHub Actions**, **Python**, and **SMTP**. This project demonstrates how to integrate Python scripts into GitHub Actions workflows to notify developers whenever a workflow execution requires attention.

---

## 🚀 Overview

In modern DevOps practices, timely notifications are essential for quick incident response and reducing downtime. This project sends automated email alerts containing workflow details whenever a GitHub Actions workflow is triggered.

Using GitHub Secrets, sensitive credentials remain secure while workflow metadata is passed to a Python script that handles email delivery through Gmail's SMTP server.

---

## ✨ Features

* 📧 Automated email notifications using Python
* ⚙️ GitHub Actions integration
* 🔐 Secure secret management with GitHub Secrets
* 📋 Includes workflow execution details
* ☁️ Cloud-friendly and lightweight implementation
* 🐍 Built entirely with Python standard libraries
* 🚀 Easy to extend for Slack or Microsoft Teams alerts

---

## 🏗️ Project Structure

```text
CD-Github-Actions-Python_Mailer/
│
├── script.py
└── .github/
    └── workflows/
        └── email_sender.yml
```

---

## 🛠️ Technologies Used

* Python 3
* GitHub Actions
* SMTP
* Gmail App Passwords
* MIME Email Libraries

---

## 📂 Workflow Explanation

### GitHub Actions Workflow

The workflow performs the following steps:

1. Checks out the repository code.
2. Sets up a Python environment.
3. Installs required dependencies.
4. Passes workflow metadata as environment variables.
5. Executes the Python mailer script.
6. Sends an email notification.

---

## 📧 Python Email Script

The Python script performs the following tasks:

* Reads sender and receiver information from environment variables.
* Constructs an email message dynamically.
* Connects to Gmail SMTP servers.
* Authenticates using secure credentials.
* Sends the email notification.
* Reports success or failure.

---

## 🔐 GitHub Secrets Configuration

Configure the following secrets in your GitHub repository:

| Secret Name       | Description                              |
| ----------------- | ---------------------------------------- |
| `SENDER_EMAIL`    | Gmail address used to send notifications |
| `SENDER_PASSWORD` | Gmail App Password                       |
| `RECEIVER_EMAIL`  | Email address receiving alerts           |

Navigate to:

```text
Repository
→ Settings
→ Secrets and variables
→ Actions
→ New repository secret
```

Add all required secrets before running the workflow.

---

## ⚙️ Environment Variables

The workflow passes the following variables to the Python script:

| Variable          | Purpose                             |
| ----------------- | ----------------------------------- |
| `WORKFLOW_NAME`   | Name of the GitHub Actions workflow |
| `REPO_NAME`       | Repository name                     |
| `WORKFLOW_RUN_ID` | Unique workflow execution ID        |
| `SENDER_EMAIL`    | Sender email address                |
| `SENDER_PASSWORD` | Gmail App Password                  |
| `RECEIVER_EMAIL`  | Recipient email address             |

---

## ▶️ Running the Workflow

### Manual Execution

This project currently uses:

```yaml
on:
  workflow_dispatch:
```

To run it:

1. Push the repository to GitHub.
2. Open the **Actions** tab.
3. Select the workflow.
4. Click **Run workflow**.
5. Verify that the notification email is received.

---

## 📨 Example Email Notification

### Subject

```text
Workflow Build Pipeline failed for repo username/project-name
```

### Email Body

```text
Hi,

The workflow Build Pipeline failed for the repository username/project-name.

Please check the logs for more details.

Run ID: 123456789
```

---

## 🔄 Future Enhancements

Potential improvements include:

* Trigger alerts only when workflows fail
* HTML email templates
* Slack notifications
* Microsoft Teams integration
* Multiple recipients support
* Direct links to GitHub Actions logs
* Retry mechanisms for failed email delivery
* Docker containerization

---

## 💡 Suggested Production Enhancement

A more practical implementation would use:

```yaml
on:
  workflow_run:
    workflows: ["Build and Deploy"]
    types:
      - completed
```

Combined with:

```yaml
if: github.event.workflow_run.conclusion == 'failure'
```

This ensures notifications are sent only when important workflows fail.

---

## 📚 Learning Outcomes

This project demonstrates practical knowledge of:

* CI/CD concepts
* GitHub Actions workflows
* Workflow automation
* Secret management
* Python scripting
* SMTP integration
* DevOps notification mechanisms
* Event-driven automation

---


## 👨‍💻 Author

**Bikramjit Roy – DevOps & Cloud Engineering Enthusiast passionate about automation, CI/CD, cloud-native practices, and building reliable software delivery pipelines.**

GitHub Profile: https://github.com/Bikramjit2212

### ⭐ If you found this project useful, consider giving it a star.
