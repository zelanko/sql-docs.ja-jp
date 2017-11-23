---
title: "DISCOVER_OBJECT_MEMORY_USAGE 行セット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: schema-rowsets
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DISCOVER_OBJECT_MEMORY_USAGE rowset
ms.assetid: 211cfa04-7bd6-43fe-8bd5-bfbff78bdafb
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 1a312ed6538be5e639283ade4f77a848ed6e9893
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="discoverobjectmemoryusage-rowset"></a>DISCOVER_OBJECT_MEMORY_USAGE 行セット
  オブジェクトによって使用されたメモリ リソースに関する情報を提供します。  
  
## <a name="rowset-columns"></a>行セットの列  
 **DISCOVER_OBJECT_MEMORY_USAGE**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|Description|  
|-----------------|--------------------|------------|-----------------|  
|**OBJECT_PARENT_PATH**|**DBTYPE_WSTR**||現在のオブジェクトの親へのパス。|  
|**OBJECT_ID**|**DBTYPE_WSTR**||作成時に定義されたオブジェクトの ID。|  
|**OBJECT_MEMORY_SHRINKABLE**|**DBTYPE_I8**||現在のオブジェクトが直接所有するすべての圧縮可能オブジェクトによって使用されたメモリの総量 (バイト)。 現在の値では、現在のオブジェクトによって所有されている名前付きのオブジェクトが所有するオブジェクトからメモリは含まれません。|  
|**OBJECT_MEMORY_NONSHRINKABLE**|**DBTYPE_I8**||現在のオブジェクトが直接所有するすべての非圧縮可能オブジェクトのメモリ量 (バイト)。 現在の値には、現在のオブジェクトが所有する名前付きオブジェクトが所有するオブジェクトのメモリは含まれません。|  
|**OBJECT_VERSION**|**DBTYPE_I4**||オブジェクトのメタデータ バージョン番号。 この番号は、オブジェクトが変更されるたびに変わります。|  
|**OBJECT_DATA_VERSION**|**DBTYPE_I4**||オブジェクト内のデータの系列番号。 この番号は、オブジェクトが処理されるたびに増加します。|  
|**OBJECT_TYPE_ID**|**DBTYPE_I4**||内部使用のために予約されています。|  
|**OBJECT_TIME_CREATED**|**DBTYPE_DBTIMESTAMP**||オブジェクトが作成されたときの UTC サーバー時刻。|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="restriction-columns"></a>制限の列  
 **DISCOVER_OBJECT_MEMORY_USAGE**行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**OBJECT_PARENT_PATH**|**DBTYPE_WSTR**|省略可。|  
|**OBJECT_ID**|**DBTYPE_WSTR**|省略可|  
  
## <a name="see-also"></a>参照  
 [XML for Analysis Schema 行セット](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
