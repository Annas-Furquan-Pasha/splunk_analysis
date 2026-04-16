# 🛡️ API Security Log Analysis using Splunk

## 📌 Project Overview
This project demonstrates how to analyze API log data using **Splunk** to identify security threats, system issues, and user behavior patterns.

The dataset consists of API request logs including HTTP methods, endpoints, status codes, response times, and user agents.

---

## 🎯 Objective
- Analyze API logs using Splunk  
- Detect security threats and anomalies  
- Identify suspicious IP activity  
- Monitor system performance and failures  

---

## 🧾 Dataset Description

The dataset is a CSV file with the following fields:

| Field | Description |
|------|------------|
| timestamp | Time of API request |
| ip_address | Client IP address |
| method | HTTP method (GET, POST, PUT, DELETE) |
| endpoint | API endpoint accessed |
| status_code | HTTP response code |
| response_time_ms | Response time in milliseconds |
| user_agent | Client tool/browser |

---

## ⚙️ Tools Used
- Splunk Enterprise  
- CSV Log Dataset  

---

## 🚀 Steps Performed

### 1. Data Upload
- Navigate to: **Settings → Add Data → Upload**  
- Upload CSV file  
- Set source type as **CSV**  
- Create index: **main_logs**  

---

### 2. Data Exploration

#### View all logs
```spl
index=main_logs

###
