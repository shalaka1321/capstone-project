# capstone-project
Dynamic Pricing for Urban Parking Lots A real-time pricing engine for 14 lots using custom models that adjust rates based on occupancy, traffic, and demand — built with pandas, numpy, and matplotlib.
## 📌 Project Overview

Urban parking resources are limited and high in demand. Static pricing strategies lead to underutilized or overcrowded parking spaces. This project aims to design and simulate a *real-time dynamic pricing engine* that adjusts parking rates based on:

- *Occupancy levels*
- *Traffic conditions*
- *Queue lengths*
- *Special event days*
- *Vehicle types*
- *Nearby competitor pricing*

We developed *three pricing models* from scratch and simulated their impact on pricing across *14 parking lots* using historical time-series data.  
The models are implemented entirely with core Python tools and visualized using matplotlib.

---

## 🛠 Tech Stack

| Category            | Tools Used             |
|---------------------|------------------------|
| Language            | Python 3.x             |
| Data Processing     | pandas, numpy      |
| Visualization       | matplotlib           |
| Notebook Execution  | Jupyter / Google Colab |
| Real-Time Ready     | (Optionally) pathway |

---

## 🧠 Architecture Diagram

```mermaid
flowchart TD
    A[📥 Raw Data: 14 Lots × 73 Days] --> B[🧹 Data Preprocessing]
    B --> C1[📈 Model 1: Linear Pricing]
    B --> C2[📊 Model 2: Demand-Based Pricing]
    B --> C3[⚖ Model 3: Competitive Pricing]
    C1 --> D[🧾 Price Timeline]
    C2 --> D
    C3 --> D
    D --> E[📉 Visualization with Matplotlib]

    subgraph Features Extracted
        B1[Occupancy Ratio]
        B2[Queue Length]
        B3[Traffic Level]
        B4[Special Day Indicator]
        B5[Vehicle Type Weight]
        B6[Competitor Prices (Simulated)]
    end

    A --> B1
    A --> B2
    A --> B3
    A --> B4
    A --> B5
    A --> B6
    B1 --> B
    B2 --> B
    B3 --> B
    B4 --> B
    B5 --> B
    B6 --> C3
```



⚙ Project Architecture & Workflow
1. Data Input
•	The dataset contains occupancy data for 14 parking spaces sampled 18 times daily over 73 days.
•	Each record includes:
o	Occupancy count and lot capacity
o	Queue length
o	Vehicle type
o	Special event indicator
o	Traffic congestion level
o	GPS coordinates for proximity modeling
2. Feature Engineering
•	Encoded categorical variables:
o	Traffic → (low=0, medium=1, high=2)
o	Vehicle type → weight values (bike=0.8, car=1.0, truck=1.2)
•	Normalized key features like occupancy ratio and demand
3. Model Implementations
✅ Model 1: Linear Occupancy-Based Pricing
python
CopyEdit
Price_t+1 = Price_t + α * (Occupancy / Capacity)
✅ Model 2: Demand Function
A weighted linear demand function:
python
CopyEdit
Demand = α * (Occupancy / Capacity) + β * QueueLength - γ * Traffic + δ * IsSpecialDay + ε * VehicleWeight
Price = BasePrice × (1 + λ × NormalizedDemand)
✅ Model 3: Competitive Pricing
•	Uses simulated competitor pricing
•	Adjusts prices up or down depending on:
o	Nearby lot prices
o	Own occupancy
o	Opportunity to undercut or price higher
4. Visualization
•	All 3 models are plotted for each parking lot
•	Each lot has its own subplot with real-time price line graphs
