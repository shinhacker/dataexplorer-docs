---
title: ".alter database streaming ingestion policy command - Azure Data Explorer"
description: "This article describes the .alter database streaming ingestion policy command in Azure Data Explorer."
services: data-explorer
author: orspod
ms.author: orspodek
ms.reviewer: yonil
ms.service: data-explorer
ms.topic: reference
ms.date: 11/29/2021
---
# .alter database streaming ingestion policy

Change the database streaming ingestion policy. Use the [streaming policy](../management/streamingingestionpolicy.md) to manage streaming ingestion for databases and tables.  

Use in low latency scenarios, where ingestion time is less than 10 seconds for varying data volume. You can optimize processing for many tables in one or more databases, when tables receive a few records per second, whereas the ingestion volume is thousands of records per second.

Use the classic bulk ingestion instead of streaming ingestion when the amount of data grows to more than 4 Gb per hour per table. 

To learn how to implement streaming ingestion, see [streaming ingestion](../../ingest-data-streaming.md). Streaming ingestion must be enabled at the cluster level before it can be used at the database level.

## Syntax

`.alter` `database` *DatabaseName* `policy` `streamingingestion` *ArrayOfPolicyObjects*

## Arguments

*DatabaseName* - Specify the name of the database.
*ArrayOfPolicyObjects* - An array with one or more policy objects defined.

## Returns

Returns a JSON representation of the policy.

## Example

The following command enables streaming ingestion and determines the suggestion allocated rate for the database:

```kusto
.alter database MyDatabase policy streamingingestion 
'{"IsEnabled": true, "HintAllocatedRate": 2.1}'
```
