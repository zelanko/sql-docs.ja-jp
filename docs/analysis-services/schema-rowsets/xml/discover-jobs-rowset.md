---
title: "DISCOVER_JOBS 行セット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DISCOVER_JOBS rowset
ms.assetid: b4d83bb6-aed3-4513-b516-cefadf95dad2
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 0fd27205ff919130eed2e7708031b0268f35408f
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="discoverjobs-rowset"></a>DISCOVER_JOBS 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]サーバーで実行されているアクティブなジョブに関する情報を提供します。 ジョブはコマンドの一部であり、コマンドに代わって特定のタスクを実行します。  
  
## <a name="rowset-columns"></a>行セットの列  
 **DISCOVER_JOBS**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|Description|  
|-----------------|--------------------|------------|-----------------|  
|**JOB_CREATION_TIME**|**DBTYPE_DBTIMESTAMP**||ジョブが作成されたときのサーバーの UTC 日時。|  
|**JOB_DESCRIPTION**|**DBTYPE_WSTR**||サーバー サービスから割り当てられたジョブの説明。|  
|**JOB_EXECUTION_TIME_MS**|**DBTYPE_I8**||ジョブがアクティブである時間 (ミリ秒単位)。|  
|**JOB_ID**|**DBTYPE_I4**||ジョブの一意の識別子。|  
|**JOB_START_TIME**|**DBTYPE_DBTIMESTAMP**||ジョブが開始されたときのサーバーの UTC 日時。|  
|**JOB_THREADPOOL_ID**|**DBTYPE_I4**||現在のジョブの開始元であるスレッド プール。|  
|**JOB_TOTAL_TIME_MS**|**DBTYPE_I8**||ジョブが開始されてからの時間 (ミリ秒単位)。|  
|**SPID**|**DBTYPE_I4**||セッション ID。|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="restriction-columns"></a>制限の列  
 **DISCOVER_JOBS**行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|SPID|DBTYPE_I4|省略可。|  
|JOB_ID|DBTYPE_I4|省略可。|  
|JOB_DESCRIPTION|DBTYPE_WSTR|省略可。|  
|JOB_THREADPOOL_ID|DBTYPE_I4|省略可。|  
|JOB_MIN TOTAL_TIME_MS|DBTYPE_I8|省略可。|  
  
## <a name="see-also"></a>参照  
 [XML for Analysis Schema 行セット](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
