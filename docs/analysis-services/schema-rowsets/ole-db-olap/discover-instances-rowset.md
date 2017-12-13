---
title: "DISCOVER_INSTANCES 行セット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DISCOVER_INSTANCES
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DISCOVER_INSTANCES rowset
ms.assetid: e0842e63-089d-468d-869f-634da343d9fb
caps.latest.revision: "30"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f26f34988ebea8279120947154f3acbd9339a3fe
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="discoverinstances-rowset"></a>DISCOVER_INSTANCES 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]サーバー上のインスタンスについて説明します。  
  
## <a name="rowset-columns"></a>行セットの列  
 **DISCOVER_INSTANCES**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|Description|  
|-----------------|--------------------|------------|-----------------|  
|**INSTANCE_NAME**|**DBTYPE_WSTR**||インスタンスの名前。|  
|**INSTANCE_PORT_NUMBER**|**DBTYPE_I4**||インスタンスがリッスンするポート番号。|  
|**INSTANCE_STATE**|**DBTYPE_I4**||サーバー インスタンスの状態。<br /><br /> **開始**<br /><br /> **停止**<br /><br /> **開始**<br /><br /> **停止しています**<br /><br /> **一時停止**|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="restriction-columns"></a>制限の列  
 **DISCOVER_INSTANCES**行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**INSTANCE_NAME**|**DBTYPE_WSTR**|省略可。|  
  
## <a name="see-also"></a>参照  
 [OLE DB for OLAP Schema 行セット](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
