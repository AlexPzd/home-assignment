---
title: Configure Data Separation and Processing in OpenPipeline
description: Tutorial on separating and processing incoming raw data with OpenPipeline
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
lastmod: 2025-07-29
author: Alex Pozdejev
type: tutorial
audience: administrator
draft: true
published: false
---

# Configure Data Separation and Processing in OpenPipeline

## Before you begin

### Who this is for

This tutorial is intended for Dynatrace administrators controlling data ingestion configuration, data storage, enrichment, and transformation policies.

### What you will learn

In this tutorial, you'll learn how to separate and process your incoming raw data using OpenPipeline.

### Prior knowledge

   * Dynatrace Query Language.
   * 

### Prerequisites

   * Latest Dynatrace environment
   * Raw data for ingestion.

### Glossary

|Term|Description| 
|:-----|:------|
|Ingest sources|Source of ingestion for a data type, collecting data from the provider into Dynatrace Platform, for example, API endpoints or OneAgent.|
|Pipeline|Collection of processing instructions to structure, separate, and store data.|
|Processor|Pre-formatted processing instruction.|
|Routing|Assignation of data to a pipeline, based either on matching conditions (dynamic routing) or directly configured (static).|
|Stage|Phase in a pipeline sequence, focused on a task and defined by processors.|



## Steps

### Context: Data Separation

Data-driven organizations often face the challenge of data quality issues. They may encounter inconsistency, duplication, missing values, incompatible formats, or lack of structure in their raw data, which may lead to additional costs. Whether you're a retail company looking to improve their data to reduce the cost of a marketing campaign or a e-commerce platform trying to pinpoint the root cause of performance slowdowns and failed transactions, OpenPipeline provides a solution for your data quality issues. It separates, cleans up, and reshapes your incoming data, preparing it for its intended use and enabling you to focus on its specific subsets. OpenPipeline makes observability, security, and business analysis easier and more streamlined. 

OpenPipeline enables you to split and direct incoming data streams into pipelines for the ease of transformation and storage. To configure data separation in OpenPipeline, you need to:

1. Configure a pipeline.
2. Configure a dynamic route for the pipeline.

### Configure a pipeline

Pipelines process data in stages. Each stage lets you use configurable **processors** — pre-formatted instructions that either modify or extract data —  to define the future shape of your data. OpenPipeline uses dynamic routing to direct data to specific pipelines.

**Note**: When setting up the pipelines, keep in mind that different data sources use different processors. To learn more about processors, see [Processor](https://docs.dynatrace.com/docs/shortlink/openpipeline-processing#processor).

1. Go to **Settings > Process and contextualize > OpenPipeline**.
2. In the **OpenPipeline** menu, select the data type for ingestion. 
3. On the **Pipelines** tab, select **+Pipeline** and provide a name for your pipeline.
4. Configure pipeline stages where applicable: 
| Stage | Action |  
| :----- | :----- |
| Processing | Select and set up processors to handle your data.  |
| Metric extraction | Capture new data from your raw data (e.g. data object string length) by defining metrics to create and aggregate from your data. To learn more about metrics, see [Metrics](https://docs.dynatrace.com/docs/analyze-explore-automate/metrics).|
| Data extraction | Extract data from your pipeline to re-ingest it as a different data type into another pipeline. |
| Permission | Specify the security context for your data. To learn more about security, see [Permissions in Grail](https://docs.dynatrace.com/docs/discover-dynatrace/platform/grail/data-model/assign-permissions-in-grail#grail-permissions-record). |
| Storage | Specify data containers (Grail buckets) where your data should be stored. See [Grail data model](https://docs.dynatrace.com/docs/discover-dynatrace/platform/grail/data-model) to learn more. |

**Note**: To avoid unexpected results, we recommend that you preview processor output with your sample data.

1. On the **Metric Extraction** tab, define metrics to create and aggregate from your data. To learn more about metrics, see [Metrics](https://docs.dynatrace.com/docs/analyze-explore-automate/metrics). 
2. On the **Data Extraction** tab, extract data from your pipeline to re-ingest it as a different data type into another pipeline.
3. On the **Permission** tab, specify the security context for your data. To learn more about this, see [Permissions in Grail](https://docs.dynatrace.com/docs/discover-dynatrace/platform/grail/data-model/assign-permissions-in-grail#grail-permissions-record).
4. On the **Storage** tab, specify Grail buckets to which your data should be assigned. See [Grail data model](https://docs.dynatrace.com/docs/discover-dynatrace/platform/grail/data-model) to learn more.
5.  **Save** the pipeline and verify if it's been added to the **Pipelines** table.

To set up dynamic routing for your pipeline:

1. Go to **Settings > Process and contextualize > OpenPipeline**.
2. Select the pipeline's data type for ingestion.
3. On the **Dynamic Routing** tab, select **+Dynamic Route**.
4. Add the name, matching condition, and select the pipeline from the drop-down.
5. **Add** the new dynamic route and verify that it's been saved to the **Dynamic routing** table.

## Result

You've successfully configured a new pipeline to separate your data. Once you've ingested and processed your data, it becomes available for analysis in Grail. 

To learn how to verify the result, see [Verify the configuration](https://docs.dynatrace.com/docs/shortlink/openpipeline-log-processing#verify).

## Related topics

[Data Flow](https://docs.dynatrace.com/docs/discover-dynatrace/platform/openpipeline/concepts/data-flow) \
[Processing](https://docs.dynatrace.com/docs/shortlink/openpipeline-processing) \
[OpenPipeline processing examples](https://docs.dynatrace.com/docs/discover-dynatrace/platform/openpipeline/use-cases/processing-examples) \
[Configure a processing pipeline](https://docs.dynatrace.com/docs/discover-dynatrace/platform/openpipeline/getting-started/tutorial-configure-processing)
---
