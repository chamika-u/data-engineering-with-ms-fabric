# 1.1 Create and use Dataflows (Gen2) in Microsoft Fabric

**Module:** Ingest Data with Microsoft Fabric  
**Estimated Time:** 30 minutes  
**Goal:** Create a Fabric workspace, create a Lakehouse, configure a Dataflow Gen2 to load CSV data, route it to a Lakehouse destination, and execute it from a Data Pipeline.

---

## Lab reference

- [mslearn-fabric home](https://microsoftlearning.github.io/mslearn-fabric)
- [Create a workspace](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/05-dataflows-gen2.html#create-a-workspace)
- [Create a lakehouse](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/05-dataflows-gen2.html#create-a-lakehouse)
- [Create a Dataflow (Gen2) to ingest data](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/05-dataflows-gen2.html#create-a-dataflow-gen2-to-ingest-data)
- [Add data destination for Dataflow](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/05-dataflows-gen2.html#add-data-destination-for-dataflow)
- [Add a dataflow to a pipeline](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/05-dataflows-gen2.html#add-a-dataflow-to-a-pipeline)
- [Clean up resources](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/05-dataflows-gen2.html#clean-up-resources)

---

## Overview

This lab demonstrates how to create a Dataflow (Gen2) in Microsoft Fabric to ingest data from a CSV file, transform it in Power Query, and load it into a Lakehouse. I then added the dataflow into a Data Pipeline to orchestrate the ingestion process and verified the resulting table in the Lakehouse.

---

## My implementation: 15-step walkthrough

### 1) Open Microsoft Fabric and navigate to the home page

![Step 1](./screenshots/1.png)

### 2) Open the workspaces view

![Step 2](./screenshots/2.png)

### 3) Create a new Fabric workspace

![Step 3](./screenshots/3.png)

### 4) Name the workspace and choose a Fabric-capable license mode

![Step 4](./screenshots/4.png)

### 5) Create a Lakehouse inside the workspace

![Step 5](./screenshots/5.png)

### 6) Open the new Lakehouse and create a Dataflow Gen2

![Step 6](./screenshots/6.png)

### 7) Select the CSV source and configure the file URL

![Step 7](./screenshots/7.png)

### 8) Preview the CSV data in Power Query

![Step 8](./screenshots/8.png)

### 9) Add a custom column for MonthNo using `Date.Month([OrderDate])`

![Step 9](./screenshots/9.png)

### 10) Confirm the transformation and applied query steps

![Step 10](./screenshots/10.png)

### 11) Configure the Lakehouse as the data destination

![Step 11](./screenshots/11.png)

### 12) Select the Lakehouse and table name `orders`

![Step 12](./screenshots/12.png)

### 13) Set destination settings to append and save the dataflow

![Step 13](./screenshots/13.png)

### 14) Save and run the Dataflow, then create a Data Pipeline to trigger it

![Step 14](./screenshots/14.png)

### 15) Verify the pipeline success and inspect the loaded `orders` table in the Lakehouse

![Step 15](./screenshots/15.png)

---

## What I learned

- Dataflows (Gen2) are ideal for low-code ETL processes in Microsoft Fabric.
- Power Query Online makes it easy to cleanse and transform raw files before loading them.
- Lakehouse destinations support direct analytical loading into a table-based structure.
- Data Pipelines can orchestrate dataflow execution and make ingestion repeatable and operationalized.
- The final `orders` table is a clean, usable analytical dataset ready for downstream reporting and transformation.

---

## Key takeaway

This exercise showed how a CSV file can be transformed and ingested into a Fabric Lakehouse using a Dataflow Gen2, then executed from a Data Pipeline for repeatable, production-ready ingestion. This is a strong foundation for building scalable data engineering workflows in Microsoft Fabric.

---

## Clean up resources

If I no longer need the test environment, I can remove the workspace from the Fabric portal:

1. Open the workspace settings.
2. Navigate to **General**.
3. Select **Remove this workspace**.
4. Confirm deletion.

---

*This README documents my hands-on learning journey in Microsoft Fabric Data Engineering.*