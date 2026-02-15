# 📦 Warehouse Order Fulfillment Optimization

![R](https://img.shields.io/badge/Language-R-blue) ![Algorithm](https://img.shields.io/badge/Algorithm-Greedy-green) ![Domain](https://img.shields.io/badge/Domain-Logistics-orange)

> **⚠️ Note:** This repository serves as a **technical case study** for a project developed during my client. Due to company confidentiality agreements, the source code and proprietary datasets are not shared. This document details the algorithmic logic and problem solving approach.

## 🎯 The Problem
In a high volume shoe warehouse, inventory is stored in **Master Cartons** (Large Boxes). Each master carton contains a mixed or uniform assortment of shoes.

**The Challenge:**
When a customer order arrives (e.g., *2x SKU_A Size 42, 1x SKU_B Size 40*), the warehouse staff needs to decide **which master cartons to open**.
* **Naive Approach:** Opening random boxes that contain the requested items leads to many partially empty master cartons, creating clutter, increasing handling time and cost.
* **Optimization Goal:** Satisfy the order list by opening the **minimum number of master cartons** possible.

## 📊 Data Structure
The optimization model utilized two main data inputs:

1.  **Inventory Data (Master Cartons):**
    * `MasterBox_ID`: Unique identifier for the large box.
    * `SKU`: Stock Keeping Unit of the shoe inside.
    * `Size`: Shoe size (e.g., 42, 44).
    * `Quantity`: Number of items of that specific SKU/Size in the box.
    
2.  **Order List:**
    * Target list of SKUs and Sizes required for shipment.

## 💡 The Solution: Greedy Algorithm with R
Since finding the absolute optimal solution in real time is an NP-Hard problem (Set Cover Problem variant), I implemented a **Greedy Heuristic approach using R**.

### Algorithmic Logic
The algorithm iterates through the order list and selects the "best" box at each step:

1.  **Input:** Receive `Target_Order` and `Available_Inventory`.
2.  **Score Calculation:** For every available Master Carton, calculate a "Utility Score".
    * *Score = Number of items in the Master Carton that match the current needs of the Target Order.*
3.  **Selection (Greedy Step):** Pick the Master Carton with the **highest Score**.
    * *If Box A covers 5 needed items and Box B covers 2, pick Box A.*
4.  **Update:**
    * Remove selected items from `Target_Order`.
    * Mark the chosen Master Carton as "Opened/Used".
5.  **Loop:** Repeat steps 2-4 until `Target_Order` is empty.

## 🛠 Tech Stack & Implementation
* **Language:** R
* **Key Libraries:** `dplyr` (for data manipulation and filtering), `data.table` (for high-performance calculation on large inventory datasets).

## 🚀 Business Impact
* **Operational Efficiency:** Reduced the number of boxes opened per wave of orders.
* **Waste Reduction:** Minimized the movement of partially filled boxes back to storage.
* **Automation:** Replaced manual decision-making with a data-driven script.
* **Cost:** reduce the cost by minimizing the number of opened boxes.

---
*Authored by Fatih Dallı*
