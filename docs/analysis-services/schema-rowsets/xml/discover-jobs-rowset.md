---
title: DISCOVER_JOBS 行セット |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e9d0d836d8fe44041aa541d71d86be327647dab9
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34036323"
---
# <a name="discoverjobs-rowset"></a>DISCOVER_JOBS 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  サーバーで実行されているアクティブなジョブに関する情報を提供します。 ジョブはコマンドの一部であり、コマンドに代わって特定のタスクを実行します。  
  
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
 [XML for Analysis スキーマ行セット](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
