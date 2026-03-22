
# 🚀 AWS S3 Hands-on Lab | Cloud Fundamentals

![AWS](https://img.shields.io/badge/AWS-S3-orange?logo=amazonaws&logoColor=white)
![CLI](https://img.shields.io/badge/AWS%20CLI-Used-blue)
![Level](https://img.shields.io/badge/Level-Beginner--Intermediate-green)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

---

## 📌 Overview

This repository documents a hands-on lab using **Amazon S3**, focusing on core cloud storage operations via AWS CLI.

It demonstrates practical experience with object storage, access control, and troubleshooting real-world permission scenarios.

---

## 🎯 Objectives

- Create an S3 bucket  
- Upload an object to the bucket  
- Configure public access to a specific object  
- Access the object via web browser  
- List bucket contents using AWS CLI  

---

## 🛠️ Tech Stack

- Amazon S3  
- AWS CLI  
- Amazon EC2 (CLI Host)  

---

## ⚙️ Implementation Steps

### 1. Create S3 Bucket

```bash
aws s3 mb s3://your-bucket-name --region us-west-2
```

### 2. Upload Object

```md
aws s3 cp your-file.ext s3://your-bucket-name
```

### 3. Validate Private Access
Attempting to access the object via browser initially resulted in:
```md
Access Denied
```
This confirms that the object is private by default.

### 4. Configure Public Access (Object-level ACL)

Public access was initially blocked due to S3 Block Public Access settings.

After adjusting the bucket configuration, the following command was executed:
```md
aws s3api put-object-acl \
  --bucket your-bucket-name \
  --key your-file.png \
  --acl public-read
```

### 5. Access Object via Browser
```md
https://your-bucket-name.s3.us-west-2.amazonaws.com/your-file.png
```
The object became publicly accessible after applying the ACL.

### 6. List Bucket Contents
```md
aws s3 ls s3://your-bucket-name
```

## ⚠️ Challenges & Troubleshooting

- ❌ Error: `AccessDenied` when applying object ACL  
- 🔍 Root cause: S3 Block Public Access (BlockPublicAcls) enabled  
- ✅ Resolution: Disabled Block Public Access at the bucket level to allow ACL configuration  

---

## 🧠 Key Learnings

- Amazon S3 blocks public access by default  
- Object-level permissions differ from bucket-level configurations  
- `aws s3` and `aws s3api` operate at different abstraction levels  
- ACLs are functional but not recommended for production use  
- Best practice: use **Bucket Policies** for scalable and secure access control  

---

## 🔗 References

- [AWS CLI S3 Command Reference](https://docs.aws.amazon.com/cli/latest/reference/s3/)
- [Amazon S3 Getting Started Guide](https://aws.amazon.com/pt/s3/getting-started/)
- [How to Grant Public Read Access to S3 Objects](https://repost.aws/knowledge-center/read-access-objects-s3-bucket)
- [Connect to Your Linux EC2 Instance](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/connect-to-linux-instance.html)

---

## 💼 Professional Context

This lab demonstrates practical experience with:

- Cloud storage provisioning  
- Access control and security configuration  
- AWS CLI-based resource management  
- Troubleshooting real-world permission issues

---

## 📄 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

