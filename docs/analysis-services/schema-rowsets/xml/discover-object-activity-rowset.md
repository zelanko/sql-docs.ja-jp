---
title: DISCOVER_OBJECT_ACTIVITY 行セット |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DISCOVER_OBJECT_ACTIVITY rowset
ms.assetid: 100f7de1-ad5c-4973-b863-3c10df1245c4
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 573b41cb848ee7a8e93bfdc4625b8a05857f2d61
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="discoverobjectactivity-rowset"></a>DISCOVER_OBJECT_ACTIVITY 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]サービスの開始以降には、オブジェクトごとのリソースの利用状況を提供します。  
  
## <a name="rowset-columns"></a>行セットの列  
 **DISCOVER_OBJECT_ACTIVITY**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|Description|  
|-----------------|--------------------|------------|-----------------|  
|**OBJECT_AGGREGATION_HIT**|**DBTYPE_I8**||サービスの開始以降にオブジェクトの集計がヒットした回数。|  
|**OBJECT_AGGREGATION_MISS**|**DBTYPE_I8**||サービスの開始以降にオブジェクトの既存の集計が見つからなかった (つまり使用されなかった) 回数。|  
|**OBJECT_CPU_TIME_MS**|**DBTYPE_I8**||サービスの開始以降にオブジェクトによって使用された CPU 時間 (ミリ秒単位)。|  
|**OBJECT_DATA_VERSION**|**DBTYPE_I4**||オブジェクト内のデータの系列番号。この番号は、オブジェクトが処理されるたびに増加します。|  
|**OBJECT_HIT**|**DBTYPE_I8**||サービスの開始以降にキャッシュ内でオブジェクトがヒットした回数。|  
|**OBJECT_ID**|**DBTYPE_WSTR**||作成時に定義されているオブジェクトの ID|  
|**OBJECT_MISS**|**DBTYPE_I8**||サービスの開始以降にキャッシュ内でオブジェクトが見つからなかった回数。|  
|**OBJECT_PARENT_PATH**|**DBTYPE_WSTR**||現在のオブジェクトの親へのパス。|  
|**OBJECT_READ_KB**|**DBTYPE_I8**||サービスの開始以降にオブジェクトによって読み取られたデータの累積値 (KB 単位)。|  
|**OBJECT_READS**|**DBTYPE_I8**||サービスの開始以降にオブジェクトによって行われた読み取り操作の累積数。|  
|**OBJECT_ROWS_RETURNED**|**DBTYPE_I8**||サービスの開始以降にオブジェクトによって呼び出し元に返された行数。|  
|**OBJECT_ROWS_SCANNED**|**DBTYPE_I8**||サービスの開始以降にオブジェクトによってスキャンされた行数。|  
|**OBJECT_VERSION**|**DBTYPE_I4**||オブジェクトのメタデータ バージョン番号。この番号は、オブジェクトが変更されるたびに変わります。|  
|**OBJECT_WRITE_KB**|**DBTYPE_I8**||サービスの開始以降にオブジェクトによって書き込まれたデータの累積値 (KB 単位)。|  
|**OBJECT_WRITES**|**DBTYPE_I8**||サービスの開始以降にオブジェクトによって行われた書き込み操作の累積数。|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="restriction-columns"></a>制限の列  
 **DISCOVER_OBJECT_ACTIVTY**行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|OBJECT_PARENT_PATH|DBTYPE_WSTR|省略可。|  
|OBJECT_ID|DBTYPE_WSTR|省略可。|  
  
## <a name="see-also"></a>参照  
 [XML for Analysis Schema 行セット](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
