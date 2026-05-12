
Algal Bloom IoT Monitoring System
This repository contains the technical documentation, firmware, and machine learning models for an inexpensive, IoT-based water quality monitoring system designed to predict the risk of harmful algal blooms.  
+3

Project Overview
Harmful Algal Blooms (HABs) pose significant risks to recreational water quality and aquatic ecosystems. This project demonstrates a low-cost, field-deployable solution that uses physical water sensors to predict chlorophyll-a (Chla) levels—a key indicator of algal growth—using Random Forest and Gradient Boosting machine learning models.  
+3

Features

Real-Time Monitoring: Collects pH, conductivity, temperature, and turbidity data.  
+4


Active Sampling: Features a reservoir and pump system for consistent sample acquisition.  


Automated Alerting: Sends email alerts via Gmail when high-risk algal growth is detected.  
+1


Predictive Analytics: Uses supervised learning with surrogate thresholds to classify bloom risk into three levels: algae_absent, algae_may_be_present, and algae_present.  
+1

Repository Structure

/firmware: Arduino/ESP32 source code for sensor data acquisition and pump control.  
+1


/Documentation: Hardware schematics, 3D models for the reservoir, and calibration notes.  


/ML_Code: Python scripts for model training and inference (Linked via submodule).  
+1

Bill of Materials (BOM)
The system is built using the following core components identified in the technical report:

Component	Description	Notes
Microcontroller	IoT-enabled board (Arduino/ESP32)	
Manages sensors and connectivity.

pH Probe	Analog pH measurement probe	
Requires frequent maintenance.

Conductivity Sensor	Proxy-indicator for nutrient enrichment	
Key indicator for algal growth.

Turbidity Sensor	Measures physical water cloudiness	
Inexpensive sensor used for training.

Temperature Sensor	Waterproof probe	
Monitors thermal conditions.

Reservoir System	Custom housing for water samples	
Requires 12V solenoid for drainage.

Active Pump	Micro vacuum pump	
Pulls samples into the reservoir.

Power Supply	3.3V Input with XL6009 Boost Converter	
Converts 3.3V to 12V for solenoid.

Machine Learning Results
The system utilizes a surrogate threshold approach based on Chlorophyll-a (Chla) guidelines from the "Guidelines for Canadian Recreational Water Quality" (33 µg/L cutoff for primary contact).  
+2


Model Agreement Rate: 84.74% between Random Forest and Gradient Boosting on test data.  


Key Metric: Focused on Precision to minimize false alarms while ensuring high sensitivity for dangerous cases.  
+1

Installation & Setup
Clone the Repository: git clone https://github.com/DorkyJuice/algalbloom_IOT.git

Initialize Submodules: git submodule update --init --recursive

Install Python Requirements: pip install -r requirements.txt

Flash Firmware: Upload the code in /firmware to your microcontroller using the Arduino IDE.

Recommendations for Field Deployment
Based on initial testing, future iterations should prioritize:


Optimization: Reducing reservoir size to save energy and reagent volume.  


Power Efficiency: Replacing the 12V solenoid with a 3.3V version to remove the need for an inefficient boost converter.  


Data Quality: Utilizing more robust pH measurement methods.  

References
This project was developed based on guidelines from the BC Ministry of Environment and Health Canada. Full references are available in the technical report.
