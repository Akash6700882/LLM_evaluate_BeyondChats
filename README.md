## LLM Evaluation Pipeline — BeyondChats Internship Assignment

This project implements a **scalable LLM evaluation pipeline** designed to analyze conversations between users and AI systems.  
The pipeline focuses on **Quality Evaluation**, **Human-like Scoring**, and **Automated Metrics** that can be run at scale (millions of conversations per day).

---

##  Project Overview

The goal of this project is to build an automated system that:

1. **Reads conversation transcripts** (user ↔ AI messages)
2. **Evaluates them using custom-defined scoring rules**
3. **Generates structured output (JSON)**
4. **Runs efficiently at scale using batching & streaming**
5. **Provides clean modular code for easy expansion**

This project replicates the type of evaluation engine used in real AI startups (like BeyondChats, Intercom, Forethought, etc.)

---

##  System Architecture

```

/beyondchats-evaluator
│
├── data/                  # Sample input conversations
├── evaluation/
│   ├── rules.py           # All evaluation rules & scoring logic
│   ├── evaluator.py       # Main evaluation engine
│   └── utils.py           # Reusable helper functions
│
├── pipeline.py            # Orchestrates entire evaluation flow
├── config.py              # Configurations (batch size, paths, etc.)
├── README.md              # Project documentation
└── requirements.txt       # Python dependencies

````

###  Key Components

#### **1. Rule-Based Evaluation**
The pipeline scores conversations based on dimensions like:
- **Helpfulness**
- **Accuracy**
- **Safety**
- **Relevance**
- **Politeness**
- **Completeness**

Each rule returns:
```json
{
  "score": 4,
  "explanation": "AI provided a clear and actionable answer."
}
````

---

##  How the Pipeline Works

### **Step 1: Load Conversations**

Conversations are stored as JSON:

```json
{
  "conversation_id": "123",
  "messages": [
    {"role": "user", "text": "How can I reset my password?"},
    {"role": "assistant", "text": "Click settings → reset password."}
  ]
}
```

### **Step 2: Apply Evaluation Rules**

The evaluator loops through each rule, scoring messages.

### **Step 3: Produce Structured Output**

```json
{
  "conversation_id": "123",
  "scores": {
    "helpfulness": 4,
    "politeness": 5,
    "accuracy": 4
  },
  "final_score": 4.3
}
```

### **Step 4: Batch Processing**

To reduce latency & cost:

* Conversations are processed in **batches of 300**
* Results are streamed to output
* Ensures efficiency at scale

---

##  Installation

### **1. Clone the repo**

```bash
git clone https://github.com/Akash6700882/LLM_evaluate_BeyondChats.git
cd LLM_evaluate_BeyondChats
```

### **2. Install dependencies**

```bash
pip install -r requirements.txt
```

---

##  Run Evaluation

### **Run pipeline on sample data**

```bash
python pipeline.py
```

### **Output stored in:**

```
/output/results.json
```

---

##  Why This Architecture?

###  Scalable

Handles **millions of evaluations/day** by batching & streaming.

###  Modular

Each rule lives in its own function, easy to modify or expand.

###  Maintainable

Clean folders, documented functions, and clear logic.

###  Real-World Ready

This structure matches evaluation engines used in production ML teams.

---

##  Future Improvements

* Integrate **LLM-based evaluators** (GPT-4o, Claude, Llama)
* Add **metric tracking dashboards**
* Add **semantic similarity scoring**
* Deploy using **FastAPI + Docker**
* Add **Redis queue** for high-volume processing

---

## Author

**Akash Malothu**
9392847778
codes.akash@gmail.com
BeyondChats Internship Assignment — LLM Evaluation Pipeline
2025


