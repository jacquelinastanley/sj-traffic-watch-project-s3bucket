# 🚦 SJ Traffic Watch — Static AWS S3 Website

A community-sourced static website displaying peak traffic hours for major roads in **Subang Jaya, Selangor**. Hosted entirely on **Amazon S3** as a static website — no servers, no backend, no cost beyond a few cents of S3 storage.

> Fork this repo, upload to your own S3 bucket, and have a live public traffic info page in under 15 minutes.

---

## 📁 Files Included

| File | Purpose |
|------|---------|
| `index.html` | Main traffic dashboard — road conditions, peak hours, commuter tips |
| `error.html` | Custom 404 error page shown when a route doesn't exist |

---

## 🚀 Quick Start — Deploy to AWS S3

### 1. Fork this repo
Click **Fork** on GitHub to copy this to your own account.

### 2. Create an S3 Bucket
- Go to AWS Console → S3 → **Create bucket**
- Name it something like `sj-traffic-watch` (must be globally unique)
- **Uncheck** "Block all public access"
- Leave everything else as default → **Create bucket**

### 3. Enable Static Website Hosting
- Open your bucket → **Properties** tab
- Scroll to **Static website hosting** → **Edit**
- Enable it, set:
  - Index document: `index.html`
  - Error document: `error.html`
- Save changes

### 4. Add a Bucket Policy (Make it Public)
- Go to **Permissions** tab → **Bucket policy** → Edit
- Paste this JSON (replace `YOUR-BUCKET-NAME`):

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::YOUR-BUCKET-NAME/*"
    }
  ]
}
```

### 5. Upload the Files
- Go to **Objects** tab → **Upload**
- Upload `index.html` and `error.html`
- Click **Upload**

### 6. Access Your Site
- Go back to **Properties** → **Static website hosting**
- Your URL will look like:
  `http://YOUR-BUCKET-NAME.s3-website-ap-southeast-1.amazonaws.com`

That's it — your site is live! 🎉

---

## ✏️ Customise It

- Edit road names, peak hours, and tips directly in `index.html`
- Replace Subang Jaya data with your own city's roads
- The site uses no external dependencies except Google Fonts

---

## 📝 Medium Article

A full step-by-step walkthrough of this project is available on Medium:
👉 [Read the article](https://medium.com/@jacquelinastanley/how-i-built-a-free-public-traffic-info-site-for-subang-jaya-using-aws-s3-71bb5c2d182d) 

---

## 📄 License

MIT — free to fork, modify, and share.
