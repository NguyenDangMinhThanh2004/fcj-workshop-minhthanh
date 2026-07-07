---
title: "Event 2"
date: 2026-06-06
weight: 2
chapter: false
pre: " <b> 4.2. </b> "
---




# Summary Report: "Meetup Event"

## Purpose of the Event

The Meetup event on June 6, 2026 was organized as a knowledge-sharing session for the technology community. The event provided attendees with practical insights into software development, cloud computing, cybersecurity, artificial intelligence, graph-based knowledge systems, and career development in Cloud and DevOps.

The event aimed to help participants understand how modern technologies are applied in real-world systems. Topics covered included Docker for application deployment, AWS WebSocket for multiplayer communication, AWS WAF combined with Machine Learning for cyber attack detection, AWS Neptune for GraphRAG, and the career path from IT Helpdesk to Cloud/DevOps.

Through different sessions, attendees had the opportunity to learn from practical demonstrations, technical explanations, and real career experiences. The event was valuable not only for technical knowledge but also for helping participants shape their learning direction and future career goals.

## General Information

* **Event name:** Meetup Event
* **Time:** June 6, 2026
* **Location:** 26th Floor, Bitexco Tower, 02 Hai Trieu Street, Saigon Ward, Ho Chi Minh City
* **Role:** Attendee

## Speakers / Main Presenters

* **Nguyễn Quốc Bảo** – Multiplayer in the Cloud: Connecting Godot Clients with AWS WebSockets
* **Bảo Huỳnh** – Docker: A Containerization Technology
* **Việt Phát** – AWS Neptune for Building a Graph Knowledge Base for GraphRAG
* **Lê Hoàng Gia Đại** – Combining AWS WAF with Machine Learning for Cyber Attack Detection on AWS
* **Trần Trung Vinh** – From IT Helpdesk to Senior Sysadmin: First Steps Toward Cloud and DevOps

## Key Topics & Learnings

### Docker and Containerization

The Docker session introduced containerization and explained why Docker is widely used in modern software development. The speaker compared traditional virtual machines with containers, showing that containers are lighter, faster to start, and easier to move across different environments.

Docker helps package an application together with its dependencies, runtime, and configuration. This allows the application to run consistently on a developer’s machine, a testing environment, or a production server.

Important concepts such as Docker Image, Docker Container, Dockerfile, image layers, build cache, and basic Docker commands were also introduced. Through this session, attendees understood how Docker supports CI/CD pipelines, microservices, cloud-native applications, testing environments, and legacy system modernization.

### Multiplayer in the Cloud with AWS WebSockets

This session focused on building a cloud-based multiplayer system using Godot clients and AWS WebSocket. The speaker introduced different communication approaches such as UDP/ENet, WebSocket, and HTTP Polling.

WebSocket was presented as a suitable option for turn-based games, lobby systems, chat features, and lightweight real-time games. The proposed architecture included Godot Client, API Gateway WebSocket, AWS Lambda, DynamoDB, and CloudWatch.

DynamoDB was used to store connection information and player states, while Lambda handled connection events, disconnection events, matchmaking, player choices, and game results. The demo showed two clients connecting to the system, being matched together, sending Rock-Paper-Scissors choices, and receiving results in real time.

This session helped attendees understand how serverless AWS services can support simple real-time applications without managing traditional backend servers.

### AWS WAF and Machine Learning for Cyber Attack Detection

The cybersecurity session explained how AWS WAF can be combined with Machine Learning to improve cyber attack detection. AWS WAF is commonly used to protect web applications from common attacks by using rule-based and signature-based protection.

However, fixed rules may not always detect new, complex, or unusual attack patterns. Because of that, Machine Learning can be used to support anomaly detection and improve the ability to identify suspicious behavior.

The speaker introduced a Network Intrusion Detection System model using the CSE-CIC-IDS2018 dataset. The session also mentioned tools and services such as Python, scikit-learn, pandas, AWS WAF, Amazon S3, AWS Lambda, Kinesis Data Firehose, GuardDuty, Security Hub, and CloudWatch.

Important issues such as real-time dashboards, alert visualization, class imbalance, false positives, and model optimization were also discussed. From this session, attendees learned that cybersecurity should be designed in layers, combining rule-based protection, monitoring, logging, and intelligent detection.

### AWS Neptune and GraphRAG

The AWS Neptune session introduced GraphRAG and explained how graph databases can improve knowledge-based AI systems. The speaker first explained Retrieval-Augmented Generation, which allows large language models to retrieve external knowledge before generating responses.

Traditional RAG is useful for retrieving relevant text, but it may have limitations when questions require understanding relationships between multiple entities. GraphRAG improves this by storing entities and relationships in a graph structure, allowing better multi-step reasoning.

AWS Neptune was presented as a graph database service that can be used to build a graph knowledge base. The speaker introduced two possible implementation approaches: using Amazon Bedrock Knowledge Bases with Neptune Analytics, or building a custom pipeline with tools such as LlamaIndex and storing graph data in Amazon Neptune.

This session helped attendees understand that knowledge systems are not only about storing documents, but also about modeling relationships between data points.

### Career Path from IT Helpdesk to Cloud and DevOps

The final session shared a practical career path from IT Helpdesk to Senior Sysadmin and then toward Cloud/DevOps. The speaker explained that Helpdesk is an important starting point because it builds troubleshooting skills, communication skills, user support experience, and basic IT operations knowledge.

As professionals move toward System Administrator roles, they need stronger knowledge of servers, networking, monitoring, patching, backup, security, and automation.

For Cloud and DevOps roles, the speaker emphasized cloud mindset, AWS fundamentals, elastic scalability, pay-as-you-go pricing, managed services, Infrastructure as Code with Terraform, version control, CI/CD, Docker, monitoring, and DevOps culture.

This session also highlighted the importance of practical projects, a clear portfolio, and continuous hands-on learning. It helped attendees understand that a Cloud/DevOps career requires both technical depth and real operational experience.

## Key Takeaways

### Docker and Deployment Consistency

Docker helps applications run consistently across different environments. This is useful for development, testing, deployment, and team collaboration.

### Real-Time Cloud Architecture

AWS WebSocket, Lambda, and DynamoDB can be used to build simple real-time systems such as chat applications, lobby systems, turn-based games, and lightweight multiplayer features.

### Layered Security Mindset

AWS WAF can block known threats, while Machine Learning can support the detection of abnormal behavior. A secure system should combine filtering, logging, monitoring, alerting, and anomaly detection.

### Value of GraphRAG

GraphRAG is useful when a system needs to understand relationships between entities. It is suitable for knowledge-based applications, internal chatbots, relationship analysis, and document question-answering systems.

### Cloud and DevOps Career Direction

A strong foundation in troubleshooting, networking, Linux, servers, Docker, automation, monitoring, and AWS is important before moving deeper into Cloud and DevOps.

## Applying to Work

The knowledge from this Meetup can be applied to learning, personal projects, and future career development.

Docker can be used to containerize web applications, APIs, and databases, making projects easier to run, share, and deploy. This is especially useful when working in teams or preparing a project for demo or production.

The AWS WebSocket session gave ideas for building real-time features such as chat rooms, multiplayer lobbies, notification systems, or simple online games using serverless AWS services.

The AWS WAF and Machine Learning session improved my security mindset. When designing web applications, I should not only focus on features but also consider request filtering, log collection, monitoring, alerting, and abnormal behavior detection.

The AWS Neptune and GraphRAG session suggested a direction for building knowledge-based systems, internal chatbots, document analysis tools, or systems that need to understand relationships between data.

The career sharing session helped me build a clearer learning roadmap. I should focus on Linux, networking, Git, Docker, AWS fundamentals, CI/CD, monitoring, Infrastructure as Code, and real hands-on projects.

## Personal Action Plan

* Practice Docker by containerizing a small web application and database.
* Build a simple real-time demo using WebSocket concepts.
* Learn more about AWS WAF, CloudWatch, GuardDuty, and Security Hub.
* Study the basic concepts of RAG, GraphRAG, and graph databases.
* Explore Amazon Neptune or graph modeling through a small knowledge base project.
* Improve Cloud/DevOps skills through Linux, networking, Git, Docker, CI/CD, and Terraform.
* Build a portfolio project that demonstrates cloud deployment, monitoring, and automation.

## Personal Reflection

The Meetup event on June 6, 2026 was a valuable experience because it covered many modern technology topics in a practical way. The sessions helped me understand that real systems often require multiple technologies working together, including application deployment, real-time communication, security, data modeling, and cloud operations.

One important lesson I gained is that a good system should not only work correctly, but also be stable, secure, scalable, maintainable, and aligned with real user needs. This changed the way I think about building software projects.

The career session was also meaningful because it showed that the path toward Cloud and DevOps requires a strong foundation and continuous practice. Instead of only learning theory, I need to build real projects, troubleshoot real problems, and gradually improve my technical skills.

After the event, I felt more motivated to continue learning AWS, Docker, Cloud Architecture, DevOps, cybersecurity, and AI-related knowledge systems.

> Overall, the Meetup event was practical and meaningful. It provided useful knowledge about software deployment, cloud architecture, cybersecurity, GraphRAG, and Cloud/DevOps career development. The event helped me gain both technical knowledge and a clearer direction for future learning.
