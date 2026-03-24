# 🚀 Deploy to Cloud Storage Bucket

Your Crackhouse Cleanup games website is ready for bucket deployment!

## 📦 Files to Upload

Upload these files to your bucket:

```
├── index.html          (main page - TESTED AND WORKING)
└── games/
    ├── chc1.swf
    ├── chc2.swf
    ├── chc3.swf
    └── chc4.swf
```

**That's it!** Just 5 files total.

---

## ☁️ Quick Deployment Guide

### AWS S3 (Recommended)

```bash
# 1. Create bucket (if needed)
aws s3 mb s3://your-bucket-name

# 2. Upload files
aws s3 cp index.html s3://your-bucket-name/
aws s3 cp games/ s3://your-bucket-name/games/ --recursive

# 3. Enable static website hosting
aws s3 website s3://your-bucket-name/ --index-document index.html

# 4. Make public
aws s3api put-bucket-policy --bucket your-bucket-name --policy '{
  "Version": "2012-10-17",
  "Statement": [{
    "Sid": "PublicReadGetObject",
    "Effect": "Allow",
    "Principal": "*",
    "Action": "s3:GetObject",
    "Resource": "arn:aws:s3:::your-bucket-name/*"
  }]
}'
```

Your site will be live at: `http://your-bucket-name.s3-website-REGION.amazonaws.com`

### Azure Blob Storage

```bash
# 1. Enable static website
az storage blob service-properties update \
  --account-name yourstorageaccount \
  --static-website --index-document index.html

# 2. Upload files
az storage blob upload-batch \
  -s . -d '$web' \
  --account-name yourstorageaccount \
  --pattern "*.html" "games/*.swf"
```

Your site will be live at: `https://yourstorageaccount.z13.web.core.windows.net/`

### Google Cloud Storage

```bash
# 1. Create and configure bucket
gsutil mb gs://your-bucket-name
gsutil web set -m index.html gs://your-bucket-name

# 2. Upload files
gsutil cp index.html gs://your-bucket-name/
gsutil cp -r games gs://your-bucket-name/

# 3. Make public
gsutil iam ch allUsers:objectViewer gs://your-bucket-name
```

Your site will be live at: `https://storage.googleapis.com/your-bucket-name/index.html`

---

## ⚙️ Important Settings

### 1. CORS Configuration (Required!)

Ruffle needs CORS enabled to load the .swf files.

**AWS S3 - Add this CORS policy:**
```json
[
    {
        "AllowedHeaders": ["*"],
        "AllowedMethods": ["GET", "HEAD"],
        "AllowedOrigins": ["*"],
        "ExposeHeaders": []
    }
]
```

**Azure - CORS is enabled by default for static websites ✓**

**GCS - Create cors.json:**
```json
[
    {
        "origin": ["*"],
        "method": ["GET"],
        "responseHeader": ["Content-Type"],
        "maxAgeSeconds": 3600
    }
]
```
Apply with: `gsutil cors set cors.json gs://your-bucket-name`

### 2. Content Types (Usually automatic)

Verify these MIME types are set:
- `index.html` → `text/html`
- `*.swf` → `application/x-shockwave-flash`

### 3. Public Access

Make sure the bucket policy allows public read access to all files.

---

## ✅ Testing Before Upload

The site is currently running at: **http://localhost:8080**

If it works there, it will work in your bucket!

---

## 🎯 Post-Deployment

After uploading, you can:
- ✅ Access via bucket URL immediately
- 🌐 Add custom domain (optional)
- 🔒 Add CloudFront/CDN with HTTPS (optional)
- 📊 Enable access logging (optional)

---

## 💡 Why This Works

- ✅ **100% Static** - No server code, just HTML/JS/CSS
- ✅ **Ruffle from CDN** - Loaded from unpkg.com (no upload needed)
- ✅ **Small files** - Total size ~1MB
- ✅ **No dependencies** - Everything self-contained
- ✅ **Tested locally** - Working on localhost = will work in bucket

---

## 📝 Deployment Checklist

Before deploying:
- [ ] index.html is present
- [ ] All 4 .swf files in games/ folder
- [ ] Tested locally (works on localhost:8080) ✓
- [ ] Bucket created
- [ ] CORS configured
- [ ] Public read access enabled

After deploying:
- [ ] Navigate to bucket URL
- [ ] Verify all 4 games load
- [ ] Test gameplay

---

## 🆘 Troubleshooting

**Games show black boxes in bucket:**
→ Check CORS configuration

**404 errors:**
→ Verify file paths are correct (case-sensitive)

**Games don't load:**
→ Check browser console (F12) for errors
→ Verify .swf files uploaded correctly

**Need help?**
→ The site works locally, so the issue is bucket configuration (CORS, permissions, or MIME types)

---

## 🎮 You're Ready!

The website is **tested and working**. Just upload to your bucket with CORS enabled and you're done!
