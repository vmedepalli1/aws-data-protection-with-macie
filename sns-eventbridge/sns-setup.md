# 📣 SNS & EventBridge Setup for Macie Alerts

This guide explains how to configure Amazon SNS and EventBridge to receive email alerts when Amazon Macie generates sensitive data findings.

---

## ✅ SNS Setup

1. Navigate to **Amazon SNS** in the AWS Console.
2. Click **Create Topic**.
   - Type: Standard
   - Name: `macie-alerts`
3. Click **Create Subscription**.
   - Protocol: Email
   - Endpoint: your email address (e.g., `you@example.com`)
4. Check your email and confirm the subscription.

---

## ✅ EventBridge Rule Setup

1. Go to **Amazon EventBridge > Rules**.
2. Click **Create Rule**.
   - Name: `macie-findings-to-sns`
   - Rule type: Rule with an event pattern
   - Event source: AWS services
   - Service provider: AWS
   - Service name: Macie
   - Event type: Macie Finding
3. Paste the JSON event pattern below.
4. Choose SNS as the target and select the `macie-alerts` topic.
5. Click **Create**.

---

## 📘 Additional Notes

- Only high-severity Macie findings matching the pattern will trigger alerts.
- Make sure your SNS topic is in the same region as your EventBridge rule.
- Check IAM permissions for both EventBridge and SNS.
