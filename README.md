# Sustainable-Logistics-Network-Optimization
Optimized GreenCity Logistics’ urban delivery network using MIP and Goal Programming models. Selected 5 fulfillment centers to serve 30 customer zones with an all-electric fleet while balancing costs, emissions, and service constraints. Sensitivity and scenario analyses confirmed a resilient design across fuel, capacity, and sustainability changes.

# Project Objective
GreenCity Logistics needed a more sustainable urban delivery network that could control operating costs while maintaining reliable customer service. The business faced rising transportation expenses, traffic congestion, delivery-time expectations, and environmental restrictions in low-emission districts.

This project used mathematical optimization to determine which fulfillment centers should operate, which customer zones each facility should serve, and which vehicle type should support each assignment. The analysis also evaluated how management priorities affect the trade-off between cost, emissions, service coverage, and facility efficiency.

# Objectives
- Minimize facility, transportation, and vehicle operating costs.
- Determine the optimal fulfillment-center locations.
- Assign every customer zone to one facility and vehicle type.
- Maintain complete service coverage and delivery reliability.
- Require electric vehicles in designated low-emission zones.
- Compare cost-minimizing and sustainability-focused solutions.
- Test whether the recommended network remains stable across business scenarios.

# Data
The project uses five operational datasets representing the major components of the delivery network:

1. location_data.csv - 25 potential fulfillment-center locations, costs, and capacities.
2. demand_data.csv - 30 customer zones and 8,500 total daily packages.
3. vehicle_data.csv - 10 vehicle types with capacity, cost, range, and emissions data.
4. distance_matrix_SAMPLE_50routes.csv - initial facility-to-zone route information.
5. emission_constraints.csv - environmental limits and low-emission-zone requirements.

Since the original distance file contained only 50 sample routes, the project generated a complete matrix of 750 possible connections between 25 facilities and 30 demand zones.

# Technologies Used
- Python
- Jupyter Notebook
- Gurobi
- pandas
- NumPy
- Matplotlib
- Seaborn
- Plotly
- NetworkX
- scikit-learn

# Repository Structure
greencity-logistics-optimization/
├── README.md
├── capstone_project_2_final.ipynb
├── capstone_project_2_final.pdf
├── Capstone Predictive Analysis Presentation.pptx
└── data/
    ├── location_data.csv
    ├── demand_data.csv
    ├── vehicle_data.csv
    ├── distance_matrix_SAMPLE_50routes.csv
    └── emission_constraints.csv

# Business Constraints
1. Assign every customer zone to exactly one fulfillment center.
2. Fulfill the complete daily demand for all selected zones.
3. Limit open facilities to serving no more than six zones.
4. Use electric vehicles in designated low-emission zones.
5. Keep selected routes within the 120-minute delivery window.
6. Confirm assigned vehicles have sufficient capacity and range.
7. Keep total package volume within facility capacity limits.

# Analytical Workflow
1. Loaded and cleaned facility, demand, vehicle, route, and emissions data.
2. Analyzed demand concentration, facility cost-capacity relationships, vehicle emissions, and geographic coverage.
3. Used K-means clustering to identify four natural demand-zone groups.
4. Expanded the incomplete route data into a 750-route facility-zone matrix.
5. Estimated congestion-adjusted travel times and route feasibility.
6. Built an Linear Programming relaxation to establish a lower-cost benchmark and identify binding constraints.
7. Formulated the primary C103 case study mixed-integer programming model in Gurobi.
8. Validated package movement through a network flow model.
9. Applied goal programming and Pareto analysis to compare cost, emissions, and service priorities.
10. Tested fuel-cost, sustainability, service-level, and facility-count scenarios.

# Trade-off Analysis
- The cost-minimizing solution costs approximately $4,939 per day and provides full service with five facilities.
- Goal Programming solution lowers emissions from 1.42 to 1.14 kg CO2 while increasing daily cost by only about $5.14.
- Emission-minimizing solution reduces emissions to approximately 0.82 kg CO2, but raises daily cost to about $7,440 and requires eight facilities.
- Service coverage remains complete across the main alternatives, making cost versus emissions the central management trade-off.

# Key Findings
- Five fulfillment centers are sufficient to serve all 30 zones under the six-stop approximation.
- The recommended facilities are L005, L007, L013, L017, and L024.
- The model serves all 8,500 daily packages without exceeding facility capacity.
- Electric vehicles satisfy low-emission-zone requirements while supporting full service coverage.
- Every selected route meets the two-hour delivery limit and vehicle-range requirements.
- The recommended network remains unchanged across fuel-cost multipliers from 0.75x to 1.50x.
- A sustainability-focused alternative can reduce emissions with only a small daily cost increase.
- Significant additional emissions reductions require a larger cost premium and more facilities.

# Recommendations
GreenCity Logistics should use the C103 cost-minimizing MIP as its baseline operating plan. The model provides the most practical balance of cost, service reliability, and sustainability while satisfying every client requirement.

Management should consider the goal programming solution when emissions reduction becomes a stronger priority. It maintains service for all 8,500 packages and reduces emissions by approximately 0.28 kg CO2 per day for only about $5 more in daily cost.
