---
title: Process Data in OpenPipeline
description: Tutorial on how to separate and process incoming data in OpenPipeline for further use
keywords:
  - OpenPipeline   
  - Dynatrace     
  - Data Separation
  - Reshape data
  - Clean up data
  - Pipeline configuration
  - Dynamic routing
  - Extraction
  - Transformation
  - Load
  - Ingestion
  - DQL
  - Dynatrace Query Language
  - Tutorial
  - Data quality
  - Processors
  - Stages
date: 2025-07-28
lastmod: 2025-07-31
author: Alex Pozdejev
type: tutorial
audience: administrator
draft: true
published: false
---

# Process Data in OpenPipeline

## Before you begin

<details>
<summary>Who this is for</summary>

   * This tutorial is intended for Dynatrace administrators controlling data ingestion configuration.
  
</details>

<details>
<summary>What you'll learn</summary>

   * You'll learn how to process your incoming raw data using OpenPipeline for further use.

</details>

<details>
<summary>Use cases</summary>

   * Data preparation, transformation (processing), and storage in Grail.
  
</details>

<details>
<summary>Prior knowledge</summary>

   * [Dynatrace Query Language](https://docs.dynatrace.com/docs/discover-dynatrace/references/dynatrace-query-language)

</details>

<details>
<summary>Prerequisites</summary>

   * Latest Dynatrace environment
   * Data for ingestion
  
</details>

<details>
<summary>Applies to</summary>

   * Davis AI
   * Dashboards
   * Grail 
   * OpenPipeline
   * Notebooks
  
</details>

<details>
<summary>Glossary</summary>

|Term|Description| 
|:-----|:------|
|Ingest source| Data from the provider for the Dynatrace Platform, for example, API endpoints or OneAgent.|
|Pipeline| Collection of processing instructions to structure, separate, and store data.|
|Processor| Pre-formatted processing instructions to apply to the data in the pipeline.|
|Routing| Assignation of data to a pipeline, based either on matching conditions (dynamic routing) or directly configured (static).|
|Stage| Part of the pipeline sequence defined by the processors it contains.|

</details>

## Steps

### Context

Raw data often requires processing before it can be stored or used for analysis. Using OpenPipeline, you can separate data into different subsets and process them independently: clean them up, extract new data, reshape, or enrich them with additional fields. Processed data can then be stored in Grail buckets and fed to our analytical tools. 

To process your data with OpenPipeline: 
1. Configure a pipeline. Pipelines use instructions to process your data.
2. Configure a dynamic route. They direct your data into specific pipelines, based on the matching conditions.

> **Note**: to help with routing and processing your data from custom ingest sources, you can pre-process it. To learn more about this, see [Pre-processing](https://docs.dynatrace.com/docs/shortlink/openpipeline-dataflow#pre-processing).


### Configure a pipeline

Pipelines process data in stages. Each stage lets you use configurable **processors** to define the future shape of your data. 

> **Note**: When setting up the pipelines, keep in mind that different data sources use different processors. To learn more about processors, see [Processor](https://docs.dynatrace.com/docs/shortlink/openpipeline-processing#processor).

To configure a pipeline:
1. Go to **Settings > Process and contextualize > OpenPipeline**.
2. Select the data type for ingestion.
3. On the **Pipelines** tab, select **+Pipeline** and provide a name for your pipeline.
4. Configure the pipeline stages where applicable:
   
|Stage|Description|  
| :----- | :----- |
| Processing | Select and set up processors to remove or mask sensitive data, add or remove fields, drop records, reshape data formats, or parse values.|
| Data extraction | Extract data from your pipeline to re-ingest it as a different data type into another pipeline.|
| Metric extraction | Capture new data from your source (e.g. data object string length) and save it as a metric. To learn more about metric extraction, see [Parse log lines and extract a metric](https://docs.dynatrace.com/docs/discover-dynatrace/platform/openpipeline/use-cases/tutorial-log-processing-pipeline#prior-knowledge).|
| Permission | Define the security context for your data. To learn more about security, see [Permissions in Grail](https://docs.dynatrace.com/docs/discover-dynatrace/platform/grail/data-model/assign-permissions-in-grail#grail-permissions-record). |
| Storage | Assign data containers (Grail buckets) to your data. See [Grail data model](https://docs.dynatrace.com/docs/discover-dynatrace/platform/grail/data-model) to learn more.|

> **Note**: To avoid unexpected results, we recommend previewing processor output using your sample data.

1.  **Save** the pipeline and verify that it's been added to the **Pipelines** table.

### Route data to a pipeline

You can configure OpenPipeline to dynamically route incoming data into different downstream pipelines based on conditions you define.

To configure dynamic routing for your pipeline:
1. Go to **Settings > Process and contextualize > OpenPipeline**.
2. Select the data type used for the pipeline.
3. On the **Dynamic Routing** tab, select **+Dynamic Route**.
4. Specify:
   * Route name
   * Matching condition
   * Target pipeline.
5. **Add** the new dynamic route and verify that it's been saved to the **Dynamic routing** table.

## Result

You've successfully configured a new pipeline to separate your data. Once you've ingested and processed your data, it becomes available for storage and further analysis. 

## Related topics
[Data Flow](https://docs.dynatrace.com/docs/discover-dynatrace/platform/openpipeline/concepts/data-flow) \
[What is Dynatrace Grail data lakehouse?](https://docs.dynatrace.com/docs/discover-dynatrace/platform/grail/dynatrace-grail) \
[Processing](https://docs.dynatrace.com/docs/shortlink/openpipeline-processing) \
[OpenPipeline processing examples](https://docs.dynatrace.com/docs/discover-dynatrace/platform/openpipeline/use-cases/processing-examples) \
[Configure a processing pipeline](https://docs.dynatrace.com/docs/discover-dynatrace/platform/openpipeline/getting-started/tutorial-configure-processing)
