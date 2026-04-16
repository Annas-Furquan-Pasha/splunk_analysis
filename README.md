# 🛡️ API Security Log Analysis using Splunk

## 📌 Project Overview
This project demonstrates how to analyze API log data using *Splunk* to identify security threats, system issues, and user behavior patterns.

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
- Navigate to: *Settings → Add Data → Upload*
- Upload CSV file
- Set source type as *CSV*
- Create index: main_logs

---

### 2. Data Exploration

#### View all logs
```spl
index=main__logs

---

## 🔍 Analysis & Queries
1. Unique Status Codes
index=main_logs | stats count by status_code
2. Error Detection (Status >= 400)
index=main_logs status_code>=400
3. Suspicious IPs (Frequent Errors)
index=main_logs status_code>=400
| stats count by ip_address
| sort -count
4. Unauthorized Access (403)
index=main_logs status_code=403
5. Endpoint Scanning (404)
index=main_logs status_code=404
| stats count by ip_address
6. Server Errors (500)
index=main_logs status_code=500
7. Risky Operations (DELETE Requests)
index=main_logs method=DELETE
8. Bot Activity Detection
index=main_logs user_agent="Python-requests/2.25.1"
9. API Performance Analysis
index=main_logs
| stats avg(response_time_ms) by endpoint
| sort -avg(response_time_ms)
10. Most Accessed Endpoints
index=main_logs
| stats count by endpoint
| sort -count
📊 Key Insights
🔴 Error Analysis
Multiple error codes detected: 400, 403, 404, 500
Indicates system instability and possible misuse
🚨 Security Threats
Unauthorized access attempts (403)
Endpoint scanning behavior (404)
High error frequency from specific IPs
🤖 Bot Activity
Requests from Python-requests indicate automated scripts
Potential for malicious automation
⚠️ Risky API Usage
Multiple DELETE requests on sensitive endpoints
Could indicate misuse or attack attempts
💣 System Issues
Server errors (500) found in:
/api/dashboard
/api/orders
⏱️ Performance Insights
Some endpoints show higher response times (~280ms)
Indicates possible performance bottlenecks
🧠 Conclusion

This project demonstrates how Splunk can be used to:

Monitor API activity in real-time
Detect suspicious behavior and attacks
Identify system errors and performance issues

Even with a small dataset, meaningful insights can be extracted to improve system security and reliability.

📌 Future Improvements
Create Splunk dashboards for visualization
Integrate real-time log streaming
Apply machine learning for anomaly detection
Simulate real-world attacks (brute force, DDoS)
