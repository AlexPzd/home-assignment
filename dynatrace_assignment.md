---
title: Separate and Process Data in OpenPipeline
description: Tutorial on how to separate and process incoming raw data in OpenPipeline for further use
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
lastmod: 2025-07-30
author: Alex Pozdejev
type: tutorial
audience: administrator
draft: true
published: false
---

# Separate and Process Data in OpenPipeline

## Before you begin

<details>
<summary>Who this is for</summary>
This tutorial is intended for Dynatrace administrators controlling data ingestion configuration.
</details>

<details>
<summary>What you'll learn</summary>

You'll learn how to separate and process your incoming raw data using OpenPipeline.

</details>

<details>
<summary>Use cases</summary>
   * Preparation, transformation, and data storage in Grail.
</details>

<details>
<summary>Prior knowledge</summary>

   * [Dynatrace Query Language](https://docs.dynatrace.com/docs/discover-dynatrace/references/dynatrace-query-language)
</details>

<details>
<summary>Prerequisites</summary>

   * Latest Dynatrace environment
   * Raw data for ingestion
</details>

<details>
<summary>Applies to</summary>

   * Davis AI
   * Grail 
   * Notebooks
</details>

<details>
<summary>Glossary</summary>

|Term|Description| 
|:-----|:------|
|Ingest sources| Data source for a data type, collecting data from the provider for the Dynatrace Platform.|
|Pipeline| Collection of processing instructions to structure, separate, and store data.|
|Processor| Pre-formatted processing instructions to apply to the data in the pipeline.|
|Routing| Assignation of data to a pipeline, based either on matching conditions (dynamic routing) or directly configured (static).|
|Data separation| The process of diving incoming data into pipelines|
|Stage| Part of the pipeline sequence defined by the processors it contains.|
</details>

## Steps

### Context: Data Separation

OpenPipeline provides a solution for your data quality issues. 

It can separate, clean up, reshape, and enrich your incoming data with additional fields, preparing it for storage in Grail and analysis. Using OpenPipeline, you can address data quality issues such as inconsistencies, duplication, missing values, incompatible formats, or a lack of structure in your incoming data.

To separate and process data in OpenPipeline:

1. Configure a pipeline to separate and process the incoming data streams.
2. Configure a dynamic route to direct any incoming data to a specific pipeline matching your pre-defined conditions.

### Configure a pipeline

Pipelines process separated data in stages. Each stage lets you use configurable **processors** to define the future shape of your data. 

**Note**: When setting up the pipelines, keep in mind that different data sources use different processors. To learn more about processors, see [Processor](https://docs.dynatrace.com/docs/shortlink/openpipeline-processing#processor).

To configure a pipeline:
1. Go to **Settings > Process and contextualize > OpenPipeline**.
2. Select the data type for ingestion.
3. On the **Pipelines** tab, select **+Pipeline** and provide a name for your pipeline.
4. Set up pipeline stages where applicable:
   
|Stage|Action|  
| :----- | :----- |
| Processing | Select and set up processors to handle your data.  |
| Metric extraction | Capture new data from your raw data (e.g. data object string length) by defining metrics to create and aggregate from your data. To learn more about metrics, see [Metrics](https://docs.dynatrace.com/docs/analyze-explore-automate/metrics).|
| Data extraction | Extract data from your pipeline to re-ingest it as a different data type into another pipeline.|
| Permission | Specify the security context for your data. To learn more about security, see [Permissions in Grail](https://docs.dynatrace.com/docs/discover-dynatrace/platform/grail/data-model/assign-permissions-in-grail#grail-permissions-record). |
| Storage | Specify data containers (Grail buckets) where your data should be stored. See [Grail data model](https://docs.dynatrace.com/docs/discover-dynatrace/platform/grail/data-model) to learn more.|

**Note**: To avoid unexpected results, we recommend that you preview processor output with your sample data.

1.  **Save** the pipeline and verify if it's been added to the **Pipelines** table.

### Route data to a pipeline

You can configure OpenPipeline to dynamically route incoming data into different downstream pipelines/targets/destinations based on conditions you define.

To configure dynamic routing for your pipeline:
1. Go to **Settings > Process and contextualize > OpenPipeline**.
2. Select the data type used for the pipeline.
3. On the **Dynamic Routing** tab, select **+Dynamic Route**.
4. Specify:
   * Name
   * Matching condition
   * Target pipeline.
5. **Add** the new dynamic route and verify that it's been saved to the **Dynamic routing** table.

## Result

You've successfully configured a new pipeline to separate your data. Once you've ingested and processed your data, it becomes available for analysis in Grail. 

To learn how to verify the result, see [Verify the configuration](https://docs.dynatrace.com/docs/shortlink/openpipeline-log-processing#verify).

## Related topics
[Data Flow](https://docs.dynatrace.com/docs/discover-dynatrace/platform/openpipeline/concepts/data-flow) \
[What is Dynatrace Grail data lakehouse?](https://docs.dynatrace.com/docs/discover-dynatrace/platform/grail/dynatrace-grail)
[Processing](https://docs.dynatrace.com/docs/shortlink/openpipeline-processing) \
[OpenPipeline processing examples](https://docs.dynatrace.com/docs/discover-dynatrace/platform/openpipeline/use-cases/processing-examples) \
[Configure a processing pipeline](https://docs.dynatrace.com/docs/discover-dynatrace/platform/openpipeline/getting-started/tutorial-configure-processing)
