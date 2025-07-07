# Summer-Analytics---Melvin

# 🚗 Dynamic Pricing for Smart Parking Spaces

This project implements two real-time dynamic pricing models for smart parking lots using streaming data. The models compute fair, bounded, and adaptive prices for parking spaces based on occupancy, traffic, events, and vehicle types.

---

## 📌 Overview

As urban parking demand grows, static pricing leads to congestion, underutilization, or user dissatisfaction. This project solves that using dynamic pricing models built with streaming data pipelines using **Pathway**.

Two pricing models are implemented:

- **Model 1:** Basic occupancy-driven pricing
- **Model 2:** Advanced multi-factor demand-based pricing

---

## 🧩 Models

### ✅ Model 1: Occupancy-Based Dynamic Pricing

- Computes price based on occupancy-to-capacity ratio.
- Normalizes demand between 0 and 1.
- Formula:
          Price = BasePrice × (1 + λ × NormalizedDemand)


- Pricing is bounded within [0.5×, 2×] of BasePrice.

### ✅ Model 2: Multi-Factor Demand-Based Pricing

- Uses:
- Occupancy / Capacity
- Queue Length
- Traffic Level
- Special Day Indicator
- Vehicle Type Weight

- Demand formula:  D = α×(Occ/Cap) + β×Queue - γ×Traffic + δ×Special + ε×VehicleWeight
                
- Final price is again calculated using: Price = BasePrice × (1 + λ × NormalizedDemand)


---

## ⚙️ Technologies Used

- [Pathway](https://github.com/pathwaycom/pathway) for real-time stream processing
- Python (Pandas, NumPy)
- Bokeh for real-time visualization
- CSV stream simulation

---

## 📊 Visualizations

- Line charts showing price evolution over time
- Comparison with simulated competitor pricing
- Interactive Bokeh plots for each parking lot

---

## 🧠 Difficulties Faced

- **Pathway learning curve**: Understanding Pathway’s streaming logic and table joining was initially challenging.
- **Type errors**: Pathway is strict with types — improper usage of `.alias()`, `.apply()` or `pw.this` led to multiple runtime bugs.
- **GroupBy logic**: Handling unnamed keys in `groupby().reduce()` required custom fixes like `get_key()` usage.
- **Joining issues**: Joining a table with itself or accessing both left and right columns correctly was tricky.
- **Real-time plotting**: Ensuring the visualizations reflected streaming changes while being accurate and clean.

---

## 📁 Project Structure

├── model1_notebook.ipynb # Implementation of Model 1

├── model2_notebook.ipynb # Implementation of Model 2

├── dataset.csv # Input dataset

├── model1_prices.csv # Model 1 output

├── model2_prices.csv # Model 2 output

├── visualizations/ # Real-time Bokeh plots

├── Dynamic_Pricing_Report.pdf # Final project report

└── README.md # You're here!
