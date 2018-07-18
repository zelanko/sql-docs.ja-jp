---
title: DISCOVER_JOBS 行セット |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- DISCOVER_JOBS rowset
ms.assetid: b4d83bb6-aed3-4513-b516-cefadf95dad2
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6a23a3e3dae0a03bf31a7b73b8cb505e834cff27
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37246062"
---
# <a name="discoverjobs-rowset"></a>DISCOVER_JOBS 行セット
  サーバーで実行されているアクティブなジョブに関する情報を提供します。 ジョブはコマンドの一部であり、コマンドに代わって特定のタスクを実行します。  
  
## <a name="rowset-columns"></a>行セットの列  
 `DISCOVER_JOBS`行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|説明|  
|-----------------|--------------------|------------|-----------------|  
|`JOB_CREATION_TIME`|`DBTYPE_DBTIMESTAMP`||ジョブが作成されたときのサーバーの UTC 日時。|  
|`JOB_DESCRIPTION`|`DBTYPE_WSTR`||サーバー サービスから割り当てられたジョブの説明。|  
|`JOB_EXECUTION_TIME_MS`|`DBTYPE_I8`||ジョブがアクティブである時間 (ミリ秒単位)。|  
|`JOB_ID`|`DBTYPE_I4`||ジョブの一意の識別子。|  
|`JOB_START_TIME`|`DBTYPE_DBTIMESTAMP`||ジョブが開始されたときのサーバーの UTC 日時。|  
|`JOB_THREADPOOL_ID`|`DBTYPE_I4`||現在のジョブの開始元であるスレッド プール。|  
|`JOB_TOTAL_TIME_MS`|`DBTYPE_I8`||ジョブが開始されてからの時間 (ミリ秒単位)。|  
|`SPID`|`DBTYPE_I4`||セッション ID。|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="restriction-columns"></a>制限の列  
 `DISCOVER_JOBS`行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|SPID|DBTYPE_I4|任意。|  
|JOB_ID|DBTYPE_I4|任意。|  
|JOB_DESCRIPTION|DBTYPE_WSTR|任意。|  
|JOB_THREADPOOL_ID|DBTYPE_I4|任意。|  
|JOB_MIN TOTAL_TIME_MS|DBTYPE_I8|任意。|  
  
## <a name="see-also"></a>参照  
 [XML for Analysis Schema 行セット](xml-for-analysis-schema-rowsets.md)  
  
  
