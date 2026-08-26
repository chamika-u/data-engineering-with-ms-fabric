# 1.1 Create and use Dataflows (Gen2) in Microsoft Fabric

**Module:** Ingest Data with Microsoft Fabric  
**Estimated Time:** 30 minutes  
**Goal:** Connect to a CSV data source, perform transformations using Power Query Online, set a data destination to a Lakehouse, and orchestrate the execution using a Data Pipeline.

---

## 📝 Overview

In Microsoft Fabric, Dataflows (Gen2) connect to various data sources and perform transformations in Power Query Online. They can then be used in Data Pipelines to ingest data into a lakehouse or other analytical store. This exercise introduces the core elements of Dataflows (Gen2) and pipeline orchestration.

---

## 🚀 Step-by-Step Implementation

### Step 1: Create a Workspace
To begin, a dedicated Fabric workspace is required to host the resources.

1. Navigated to the Microsoft Fabric home page.
2. Selected **Workspaces** from the left menu and created a new workspace with Fabric capacity (Trial/Premium).

![Create Workspace](./screenshots/01_create_workspace.png)
*Screenshot: Creating a new Fabric workspace with capacity enabled.*

### Step 2: Create a Lakehouse
The Lakehouse serves as the destination storage for the ingested data.

1. Inside the new workspace, selected **Create**.
2. Under the Data Engineering section, selected **Lakehouse** and provided a unique name.

![Create Lakehouse](./screenshots/02_create_lakehouse.png)
*Screenshot: The newly created, empty Lakehouse interface.*

### Step 3: Create a Dataflow (Gen2) to Ingest Data
This step encapsulates the Extract, Transform, and Load (ETL) process using Power Query.

1. From the Lakehouse home page, selected **Get data > New Dataflow Gen2**.
2. Chose **Import from a Text/CSV file** with the following configurations:
   * **File URL:** `https://raw.githubusercontent.com/MicrosoftLearning/dp-data/main/orders.csv`
   * **Connection:** Create new connection
   * **Authentication:** Anonymous
3. Previewed the file data and selected **Create**.

![Power Query Source](./screenshots/03_power_query_source.png)
*Screenshot: Power Query editor showing the initial dataset and applied steps.*

4. Added a custom column to extract the month number:
   * Selected **Add column > Custom column**.
   * **Name:** `MonthNo`
   * **Data Type:** `Whole Number`
   * **Formula:** `Date.Month([OrderDate])`
5. Verified that the `OrderDate` column was set to **Date** type and `MonthNo` was set to **Whole Number**.

![Custom Column Added](./screenshots/04_custom_column_monthno.png)
*Screenshot: The Power Query editor showing the newly created MonthNo column.*

### Step 4: Add Data Destination for Dataflow
Configuring where the transformed data will be stored.

1. On the Home tab, selected **Add data destination > Lakehouse**.
2. Authenticated the connection using organizational credentials.
3. Selected the workspace and Lakehouse created in Step 2.
4. Specified a new table named `orders`.
5. In destination settings, disabled "Use automatic settings", selected **Append**, and saved settings.

![Data Destination Config](./screenshots/05_data_destination_settings.png)
*Screenshot: Configuring the Lakehouse data destination and Append settings.*

6. Verified the destination icon in the **Diagram view** and selected **Save & run** to publish `Dataflow 1`.

![Diagram View](./screenshots/06_diagram_view_destination.png)
*Screenshot: Diagram view showing the Lakehouse destination successfully attached.*

### Step 5: Add a Dataflow to a Pipeline
Pipelines orchestrate data ingestion, allowing dataflows to run on automated schedules.

1. Navigated back to the workspace and selected **+ New item > Data pipeline**.
2. Named the pipeline `Load data`.
3. Selected **Pipeline activity** and added a **Dataflow** activity.
4. In the Settings tab, linked the activity to the previously created `Dataflow 1`.

![Pipeline Configuration](./screenshots/07_pipeline_configuration.png)
*Screenshot: The Data pipeline editor with the Dataflow1 activity configured.*

5. Saved the pipeline and clicked **Run**. Waited for the execution to complete successfully.

![Pipeline Execution](./screenshots/08_pipeline_execution_success.png)
*Screenshot: Successful pipeline run status showing completion duration.*

### Step 6: Verify the Data
Confirming the data successfully landed in the Lakehouse.

1. Opened the Lakehouse from the workspace.
2. Refreshed the **Tables** directory.
3. Selected the new `orders` table to view the ingested and transformed data.

![Verified Lakehouse Data](./screenshots/09_verified_lakehouse_data.png)
*Screenshot: The populated 'orders' table in the Lakehouse, including the newly calculated MonthNo column.*

---

## 🧹 Clean Up (Optional)
To manage capacity and keep the environment clean, the workspace and its contents can be deleted from **Workspace settings > General > Remove this workspace** once the exercise is fully documented.

---
*Documented for Microsoft Fabric Data Engineering Portfolio.*