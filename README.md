# 🚨 RescueGrid

### AI-Powered Dynamic Disaster Response & Resource Optimization

> **RescueGrid** is an AI-assisted disaster-response decision-support system that helps response teams prioritize emergencies, allocate limited resources, and dynamically optimize rescue routes as situations change in real time.

---

## 📌 Overview

During disasters, response teams often face hundreds of emergency requests while having limited rescue teams, ambulances, boats, medical kits, and other resources.

At the same time:

* 🚧 Roads and bridges can become blocked
* 🌦️ Environmental conditions can change rapidly
* 🚑 Rescue resources are limited
* 📩 Emergency requests arrive through multiple channels
* ⏱️ Delayed decisions can increase response time

**RescueGrid** addresses this challenge by combining AI-based emergency understanding, dynamic prioritization, smart resource allocation, route optimization, and a real-time command center into a single workflow.

---

## 🎯 Problem Statement

> **How can disaster-response teams prioritize emergencies, allocate limited resources, and dynamically reroute rescue operations in real time?**

Existing approaches often focus on displaying information rather than continuously optimizing response decisions.

RescueGrid aims to close this gap through a continuous:

**Understand → Prioritize → Assign → Route → Monitor → Re-optimize**

response loop.

---

## 💡 Key Features

### 1. 📩 Multi-Modal Emergency Requests

Emergency requests can be received through:

* SMS
* Web Forms
* WhatsApp
* Voice

The AI request parser extracts important information such as:

* Number of people affected
* Injuries
* Vulnerability
* Location
* Emergency type
* Required assistance

---

### 2. 🧠 AI Emergency Prioritization

RescueGrid calculates a dynamic risk/priority score using factors such as:

* Severity
* Number of people affected
* Vulnerability
* Environmental danger
* Waiting time

Incidents can then be categorized into:

**Critical → High → Medium → Low**

---

### 3. 🚑 Smart Resource Allocation

The system matches emergencies with suitable available resources, including:

* Rescue teams
* Ambulances
* Boats
* Medical kits
* Specialized resources

Matching considers:

* Capability
* Availability
* Location
* Capacity

---

### 4. 🗺️ Real-Time Disaster Map & Dynamic Routing

The command center can monitor:

* Emergency incidents
* Rescue team locations
* Blocked roads
* Bridges
* Hazard zones

The routing engine provides:

* Feasible routes
* Estimated Time of Arrival (ETA)
* Dynamic rerouting

The proposed routing approach uses **A*** / **Dijkstra's algorithm** on a road-network graph.

---

### 5. 🖥️ Real-Time Command Center

A centralized dashboard enables operators to:

* Monitor active incidents
* Re-prioritize emergencies
* Escalate incidents
* Reassign resources
* Monitor rescue operations

### Human-in-the-Loop

AI recommendations do **not** automatically make the final deployment decision.

> **AI recommends — human responders approve final deployment.**

---

## 🔄 How RescueGrid Works

```text
Emergency Request
       ↓
AI Request Parser
       ↓
Risk & Priority Score
       ↓
Resource Matching
       ↓
Safe Route + ETA
       ↓
Command Center Monitoring
       ↓
Real-Time Re-optimization
       ↺
```

Changes in the field feed back into prioritization, allocation, and routing.

---

## 🏗️ System Architecture

```text
                    ┌──────────────────────────┐
                    │     External Inputs      │
                    │                          │
                    │ Road / Infrastructure    │
                    │ Weather / Hazard Data    │
                    │ Resource Availability    │
                    │ Team Locations           │
                    └────────────┬─────────────┘
                                 │
                                 ▼
┌────────────────────────────────────────────────────────┐
│                  INPUT CHANNELS                        │
│       SMS   │   Web Form   │   WhatsApp   │   Voice   │
└───────────────────────────┬────────────────────────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │ AI Request Parser    │
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │ AI Priority Engine  │
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │ Resource Allocation  │
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │ Route Optimization   │
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │ Command Center       │
                 └──────────┬──────────┘
                            │
                            ▼
                     Re-optimization
                            │
                            └──────↺
```

---

## 🛠️ Technology Stack

| Component     | Technology                                |
| ------------- | ----------------------------------------- |
| Frontend      | React.js, Tailwind CSS                    |
| Backend       | Python, FastAPI                           |
| AI / NLP      | Python NLP, LLM API / AI extraction layer |
| Database      | PostgreSQL                                |
| Mapping       | Leaflet.js, OpenStreetMap                 |
| Routing       | A* / Dijkstra                             |
| Real-Time     | WebSockets                                |
| Communication | SMS / WhatsApp API                        |
| Voice         | Speech-to-Text API                        |
| Deployment    | Cloud Platform                            |

---

## ⚙️ Implementation Approach

### 1. Emergency Understanding

Extract:

* People count
* Vulnerability
* Injury information
* Location
* Emergency type

### 2. Priority Engine

Calculate an explainable risk score based on:

```text
Severity
+ Vulnerability
+ People Affected
+ Environmental Danger
+ Waiting Time
```

### 3. Resource Matching

Match incident requirements with available team capabilities and equipment.

### 4. Routing Engine

Calculate feasible routes on a road-network graph while accounting for blocked roads and bridges.

### 5. Real-Time Optimization

Whenever new information arrives, the system can recalculate:

* Priority
* Resource assignment
* Route

---

## ✨ Innovation

RescueGrid goes beyond simply showing where emergencies are located.

It continuously helps determine:

> **How should limited rescue resources be deployed as the situation changes?**

The system integrates:

**Emergency Intake + AI Prioritization + Resource Allocation + Disaster-Aware Routing + Continuous Re-optimization**

into one response workflow.

---

## 🔐 Safety & Reliability

RescueGrid follows a **human-in-the-loop** approach.

AI-generated recommendations are intended to support response teams rather than replace human decision-making.

Key safeguards include:

* Explainable priority scoring
* Human approval before deployment
* Dynamic updates when conditions change
* Resource availability checks
* Blocked-route handling
* Escalation and reassignment

---

## 📈 Scalability

The proposed architecture can scale from:

```text
Campus
   ↓
City
   ↓
State
   ↓
Multi-Region
```

The modular architecture allows additional data sources, resources, communication channels, and optimization components to be integrated over time.

---

## 🚧 Challenges & Approach

| Challenge                       | Approach                    |
| ------------------------------- | --------------------------- |
| Unstructured emergency messages | NLP / LLM extraction        |
| Limited rescue resources        | Constraint-based allocation |
| Changing road conditions        | Dynamic graph updates       |
| Large number of incidents       | Priority queue              |
| Network disruption              | SMS / degraded-mode support |
| Incorrect AI recommendations    | Human-in-the-loop approval  |

---

## 🔍 Existing Approach Gap

RescueGrid combines capabilities that are often handled separately:

| Existing Approach   | Typical Focus      | RescueGrid                         |
| ------------------- | ------------------ | ---------------------------------- |
| Emergency helplines | Request collection | Request collection + AI extraction |
| Disaster maps       | Visualization      | Visualization + prioritization     |
| Fleet tracking      | Team location      | Team location + resource matching  |
| Route planners      | Navigation         | Disaster-aware routing             |
| Manual coordination | Human dependent    | Real-time optimization             |

> Comparison of approach categories, not of named commercial products.

---

## 📚 Research & References

* [OpenStreetMap](https://www.openstreetmap.org/) — Geographic and map data
* [Leaflet.js](https://leafletjs.com/) — Interactive mapping
* [FastAPI](https://fastapi.tiangolo.com/) — Backend API framework
* [PostgreSQL](https://www.postgresql.org/docs/) — Relational database
* Dijkstra (1959), *Numerische Mathematik*
* Hart, Nilsson & Raphael (1968), *IEEE Transactions on Systems Science and Cybernetics*
* Altay & Green (2006), *European Journal of Operational Research*
* Özdamar, Ekinci & Küçükyazici (2004), *Annals of Operations Research*

---

## 👥 Team

### Team NEXORA

**Galgotias University**

* Anamika
* Anshika Rajput
* Sakshi Patel
* Shivani
* Princess Gupta

---

## 🏆 Hackathon

**BUILD WITH भारत 4.0 — National Level Hackathon**

### Project: RescueGrid

**AI-Powered Dynamic Disaster Response & Resource Optimization**

---

## 🔗 Project Links

| Resource   | Link             |
| ---------- | ---------------- |
| GitHub     | *Add GitHub URL* |
| Live Demo  | *Add Demo URL*   |
| Demo Video | *Optional*       |

---

## 📌 Project Status

🚧 **Prototype / Hackathon Project**

The technology stack and implementation described above represent the proposed prototype architecture.

---

## ❤️ Vision

RescueGrid aims to help disaster-response teams make faster, more informed decisions when emergencies are numerous, resources are limited, and conditions are constantly changing.

**Understand. Prioritize. Assign. Route. Monitor. Re-optimize.**
