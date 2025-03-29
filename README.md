# CommunicationPatterns

### Publish-Subscribe

Publish-Subscribe (Pub-Sub) can work in **two different modes**:  

1️⃣ **Instant Message/Event Broadcasting (Fire-and-Forget, No Queue)**  
2️⃣ **Queued Message Processing (Ensured Delivery, FIFO/At-least-once Processing)**  

---

## **1️⃣ Instant Message/Event Broadcasting (Real-Time, No Queue)**
📌 **How It Works:**  
- Messages are **delivered instantly** to all active subscribers.  
- **No message persistence** – if a subscriber is offline, it **misses the message**.  
- Ideal for **real-time notifications, chat apps, live dashboards**.  

📌 **Example Technologies:**  
- **Redis Pub/Sub** (pure real-time).  
- **Google Pub/Sub (pull mode, no persistence)**.  
- **WebSockets (direct push to clients)**.  

📌 **Example Use Cases:**  
✅ Live chat applications (e.g., WhatsApp, Slack).  
✅ Stock price updates.  
✅ Live sports scores.

**publisher -> (broadcast) channel -> subscriber**

---

## **2️⃣ Queued Message Processing (Guaranteed Delivery)**
📌 **How It Works:**  
- Messages are **stored in a queue** until a subscriber processes them.  
- Ensures **at-least-once delivery** (or **exactly-once**, depending on the system).  
- Ideal for **reliable event processing, task queues, microservices**.  

📌 **Example Technologies:**  
- **Kafka** (distributed event streaming, durable logs).  
- **RabbitMQ** (message queue with acknowledgments).  
- **Google Pub/Sub (ack-based delivery, message persistence)**.  

📌 **Example Use Cases:**  
✅ Order processing systems (e.g., Amazon order events).  
✅ Background jobs (e.g., sending emails after user registration).  
✅ Log aggregation and analytics.

**publisher -> queue -> consumer(subscriber)**

---

## **🔹 Pub-Sub Modes Comparison**
| **Feature** | **Instant Broadcasting (No Queue)** | **Queued Processing (Guaranteed Delivery)** |
|------------|------------------------------------|--------------------------------|
| **Persistence** | ❌ No (lost if subscriber is offline) | ✅ Yes (stored until consumed) |
| **Delivery Guarantee** | ❌ No (fire-and-forget) | ✅ Yes (at-least-once / exactly-once) |
| **Message Ordering** | ❌ No guarantee | ✅ Ordered (FIFO in Kafka, RabbitMQ) |
| **Use Case** | Real-time updates, notifications | Task processing, event-driven systems |
| **Examples** | Redis Pub/Sub, WebSockets | Kafka, RabbitMQ, Google Pub/Sub |

---

### **🚀 Which One Should You Use?**
✔ **Need real-time updates, no need to store messages?** → **Use instant broadcasting (Redis, WebSockets).**  
✔ **Need guaranteed delivery and message queuing?** → **Use queued processing (Kafka, RabbitMQ).**  
