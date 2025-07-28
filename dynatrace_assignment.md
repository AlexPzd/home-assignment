---
title: Set up Data Separation and Processing in OpenPipeline
description: Tutorial on how to use pipelines to separate data in OpenPipeline
keywords:
  - OpenPipeline   
  - Dynatrace     
  - Data Separation
date: 2025-07-28
lastmod: 2025-07-29
author: Alex Pozdejev
type: tutorial
audience: administrator
draft: true
published: false
---

# Set up Data Separation and Processing in OpenPipeline

## Who this is for

This tutorial is intended for Dynatrace administrators controlling ingestion configuration, data storage and enrichment, and transformation policies.

## What you will learn

As Dynatrace supports data ingestion from different sources, the raw incoming data comes in a wide variety of formats. Analysing such data can be an improbable task. With OpenPipeline, you can separate, clean up, and reshape your data for the ease of processing and analysis. Data separation also comes in handy if you're only interested in certain parts of your raw data. 

## Prior knowledge

   * Dynatrace Query Language
   * OpenPipeline key concepts. 

## Prerequisites

   * Latest Dynatrace environment

## Context

OpenPipelines enables you to split incoming data streams into pipelines and route your ingested data into a specific pipeline. This can help you focus on the data in a given pipeline at a time.

Pipelines process data in stages, each stage letting you use configurable processors to define tasks to perform as part of the stage. Processors are pre-formatted instructions that either modify or extract data. 

**Note**: When setting up the pipelines, keep in mind different data sources require different processors. To learn more about processors, see [Processor](https://docs.dynatrace.com/docs/shortlink/openpipeline-processing#processor).

## Steps

To create a pipeline:

1. Go to **Settings > Process and contextualize > OpenPipeline**.
2. In the **OpenPipeline** menu, select the data type for ingestion. 
3. On the **Pipelines** tab, select **+Pipeline** and provide a name for your pipeline.
4. On the **Processing** tab, select and set up processors to handle your data. 
**Note**: To avoid unexpected results, we recommend that you preview processor output with your sample data.
1. On the **Metric Extraction** tab, define metrics to create and aggregate from your data. To learn more about metrics, see [Metrics](https://docs.dynatrace.com/docs/analyze-explore-automate/metrics). 
2. On the **Data Extraction** tab, extract data from your pipeline to re-ingest it as a different data type into another pipeline.
3. On the **Permission** tab, specify the security context for your data. To learn more about this, see [Permissions in Grail].(https://docs.dynatrace.com/docs/discover-dynatrace/platform/grail/data-model/assign-permissions-in-grail#grail-permissions-record)
4. On the **Storage** tab, specify Grail buckets to which your data should be assigned. See [Grail data model](https://docs.dynatrace.com/docs/discover-dynatrace/platform/grail/data-model) to learn more.
5.  **Save** the pipeline and verify if it's been added to the **Pipelines** table.

To set up dynamic routing for your pipeline:

1. Go to **Settings > Process and contextualize > OpenPipeline**.
2. Select the pipeline's data type for ingestion.
3. On the **Dynamic Routing** tab, select **+Dynamic Route**.
4. Add the name, matching condition, and select the pipeline from the drop-down.
5. **Add** the new dynamic route and verify if it's been saved to the **Dynamic routing** table.

## Result

You've successfully configured a new pipeline to separate your data. To learn how to verify the result, see [Verify the configuration](https://docs.dynatrace.com/docs/shortlink/openpipeline-log-processing#verify).

## Related topics
---
[Data Flow](https://docs.dynatrace.com/docs/discover-dynatrace/platform/openpipeline/concepts/data-flow) \
[Processing](https://docs.dynatrace.com/docs/shortlink/openpipeline-processing) \
[OpenPipeline processing examples](https://docs.dynatrace.com/docs/discover-dynatrace/platform/openpipeline/use-cases/processing-examples) \
[Configure a processing pipeline](https://docs.dynatrace.com/docs/discover-dynatrace/platform/openpipeline/getting-started/tutorial-configure-processing)
---