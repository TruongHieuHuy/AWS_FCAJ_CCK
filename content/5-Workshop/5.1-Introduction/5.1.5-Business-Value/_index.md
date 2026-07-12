---
title: "5.1.5 Business Assessment & Vision"
weight: 5
chapter: false
---


### 1. Cost Optimization - BA/SA Perspective

The greatest power of Serverless is transforming fixed costs (CapEx) into variable operational costs (OpEx). From a business management perspective, this is a superior financial model:

- **Pay-as-you-go (Scale-to-zero):** You do not have to pay for an EC2 server idling all night. When the system has no user traffic, compute costs are virtually zero.
- **Demand-based Optimization:** DynamoDB On-Demand automatically scales data capacity. The CloudFront CDN system caches Frontend content helping minimize the number of requests hitting the origin server, saving a massive amount of Data Transfer Out costs.
- **Operational Optimization:** No need to hire a specialized System Admin team to patch OS vulnerabilities or maintain physical servers. The team can dedicate its full strength to developing profit-generating features.

### 2. Current Limitations

Despite its superiority, the current architecture trades off certain factors in exchange for rapid development speed:

- **Single Region Dependency:** The system is currently only running in `ap-southeast-1`. Comprehensive regional Disaster Recovery (DR) capabilities have not been established.
- **Compute Layer Constraints:** AWS Lambda has a maximum timeout limit of 15 minutes. If heavy data processing tasks arise that extend beyond this, the architecture must transition to AWS Fargate or Amazon EKS.
- **Risk of Sudden Cost Spikes:** Although optimized for low or fluctuating traffic, if the application reaches a scale of tens of millions of continuous requests daily, the costs paid for API Gateway and Lambda could be higher compared to renting a dedicated physical server.

### 3. Future Work - BA/SA Perspective

To elevate Budget Tracker from a personal application into a professional financial SaaS solution, the strategic roadmap could include:

- **B2B & Freemium Business Models:** Opening the API for other banking/Fintech applications to embed the financial management platform into their ecosystems.
- **Integrated AI Financial Advisor:** Deeply applying generative AI models (Google Gemini/Amazon Bedrock) to analyze user cash flow habits to automatically advise saving plans rather than merely categorizing transactions.
- **Multi-Region Architecture:** Deploying DynamoDB Global Tables and CloudFront Route 53 Geolocation to create an exceptional user experience across multiple countries, aiming for a 99.99% SLA.
- **Data Modernization (Data Lake):** Building an aggregate data warehouse on Amazon S3 and using Amazon QuickSight to provide real-time smart financial reporting charts (Data-driven Insights) for the Board of Directors.

### 4. Conclusion

The Budget Tracker Workshop project is not simply an AWS configuration technical exercise. It is a benchmark blueprint representing the intersection between **Cloud Engineering** and **Solution Architecture** thinking.

Practitioners will master the design philosophy of applications with flexible scalability, high security, and most importantly, thoroughly solving business problems with the most optimized budget.
