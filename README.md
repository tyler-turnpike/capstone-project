# Dynamic Parking Pricing Using Demand-Based Models

This project explores dynamic pricing strategies for urban parking lots using real-time operational data. I developed and compared four models ranging from basic linear adjustments to more advanced demand-driven and revenue-optimized pricing systems.

---

## Project Goal

To design a pricing system that adjusts parking prices dynamically based on factors like occupancy, vehicle type, queue length, and special event days—balancing fairness, responsiveness, and profitability.

---

##  Models Implemented

### Model 1.0 – Basic Linear Model
- Adjusts price based only on occupancy ratio.
- Simple and reactive, but too abrupt for real-world use.

### Model 1.5 – Smoothed Linear Model
- Adds smoothing to Model 1.0 using a weighted approach.
- Limits price fluctuation by gradually adjusting toward the target price.
- Keeps prices between $5 and $20.

### Model 2.0 – Additive Demand-Based Model
- Computes a multi-factor demand score using:
  - Occupancy ratio  
  - Queue length  
  - Vehicle type (scaled by space taken)  
  - Special day flag
- Normalizes demand to [0, 1] and maps to pricing range.

### Model 2.1 – Capitalist-Biased Model
- Builds on Model 2.0 but favors higher pricing for revenue maximization.
- Introduces a bias term and weight adjustments.
- Price is compressed slightly to reduce abrupt spikes.

---

## 📁 Dataset

The dataset represents time-series parking lot usage in 30-minute intervals.

| Column               | Description                               |
|----------------------|-------------------------------------------|
| `Date`               | Date of observation                       |
| `Timestamp`          | 30-minute time slot                       |
| `ParkingLotID`       | Identifier for each parking lot           |
| `Occupancy`          | Number of parked vehicles                 |
| `Capacity`           | Total parking spaces available            |
| `QueueLength`        | Number of waiting vehicles outside lot    |
| `VehicleType`        | Car, Bike, or Truck                       |
| `IsSpecialDay`       | 1 if holiday/special event, else 0        |
| `TrafficConditionNearby` | Low / Average / High (dropped due to multicollinearity) |

---

## Feature Engineering

I created the following new features:
- `OccupancyRatio` = Occupancy / Capacity
- `VehicleTypeNumeric`: Bike = 1, Car = 2, Truck = 4
- `Demand`: Based on weighted formula
- `DemandNormalized`: Scaled to 0–1
- `Price` and `Price_Compressed`: Final computed prices

---

## Visualizations

Each model is visualized using:
- Time-series plots (Price vs. Time)
- Comparison of original and smoothed pricing
- One-day snapshots for close inspection

(Visuals are included in the project report and notebooks)

---

## Report Structure

The full project report includes:
- Problem statement
- Dataset description
- All four models with formulae
- Graphs and tables
- Limitations and observations
- Final conclusion

**View the report in `report.pdf` or notebook sections**

---

## Future Extensions

- Add competitor pricing and geographic proximity (Model 3)
- Integrate real-time traffic conditions
- Use ML/regression to auto-learn α and β
- Build a dashboard for live pricing simulation

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------



