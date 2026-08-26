# Dataflow Gen2 ingestion walkthrough

This exercise documents how I built a simple ingestion flow in Microsoft Fabric using a Dataflow Gen2 and a Data Pipeline. The goal was to bring a CSV file into a Lakehouse and verify that the data was loaded correctly.

---

## Reference material

The Microsoft Learn lab was used only as guidance for the process and steps:

- [mslearn-fabric](https://microsoftlearning.github.io/mslearn-fabric)
- [Create and use Dataflows (Gen2) in Microsoft Fabric](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/05-dataflows-gen2.html)

---

## How I did it

### 1. Creating the workspace

I opened Microsoft Fabric and created a new workspace from the workspace view so I had a dedicated environment to build the solution.

![Screenshot](./screenshots/1.png)

### 2. First look after workspace creation

Once the workspace was created, I reviewed the initial layout and confirmed that the environment was ready for the next steps.

![Screenshot](./screenshots/2.png)

### 3. Creating the Lakehouse

I created a new Lakehouse inside the workspace, which would serve as the destination for the ingested data.

![Screenshot](./screenshots/3.png)

### 4. First look after Lakehouse creation

After the Lakehouse was created, I checked the initial interface and confirmed that the destination was ready for data ingestion.

![Screenshot](./screenshots/4.png)

### 5. Creating the Dataflow Gen2

From the Lakehouse, I started a new Dataflow Gen2 to connect to a source file and begin the ETL process.

![Screenshot](./screenshots/5.png)

### 6. First look after creating the dataflow

I opened the Power Query editor and reviewed the initial layout where the source and transformation steps would be defined.

![Screenshot](./screenshots/6.png)

### 7. Adding the custom column

I added a custom column using the formula `Date.Month([OrderDate])` to create a month number field from the order date column.

![Screenshot](./screenshots/7.png)

### 8. Reviewing the new column

After the custom column was added, I reviewed the result to make sure the derived field was created correctly and the data looked valid.

![Screenshot](./screenshots/8.png)

### 9. Viewing the dataflow as a diagram

I switched to the diagram view so I could see the flow of the transformation and confirm that the steps were connected properly.

![Screenshot](./screenshots/9.png)

### 10. Creating the pipeline

I created a new pipeline to orchestrate the ingestion process and connect it to the dataflow activity.

![Screenshot](./screenshots/10.png)

### 11. Adding the dataflow activity in the pipeline

I added the Dataflow activity to the pipeline and configured it to use the dataflow I had already created.

![Screenshot](./screenshots/11.png)

### 12. Running the pipeline

I started the pipeline run and monitored the execution progress while the dataflow processed and loaded the data.

![Screenshot](./screenshots/12.png)

### 13. Pipeline execution succeeded

The pipeline completed successfully, which confirmed that the ingestion process ran without errors.

![Screenshot](./screenshots/13.png)

### 14. Checking the new table in the Lakehouse

I refreshed the Lakehouse and confirmed that a new `orders` table had been created as the output of the dataflow.

![Screenshot](./screenshots/14.png)

### 15. Deleting the workspace

Once the exercise was complete, I cleaned up the environment by deleting the workspace.

![Screenshot](./screenshots/15.png)

---

## What I learned

This exercise helped me understand the end-to-end pattern of data ingestion in Fabric:

- a workspace is needed to host the data engineering assets
- a Lakehouse acts as the destination for analytical data
- a Dataflow Gen2 can read a source file and prepare it for loading
- custom transformations can be applied using Power Query logic
- a pipeline can orchestrate and run the ingestion workflow
- the final loaded table becomes ready for reporting and further processing

---

## Outcome

The workflow was completed successfully: the CSV data was ingested, transformed, loaded into the Lakehouse, and executed through a pipeline. This was a practical example of how Microsoft Fabric supports low-code ETL and orchestration in a modern data engineering setup.

---

## Clean-up

After finishing the exercise, the workspace was removed to keep the environment clean and avoid unnecessary resource usage.
