---
title: DISCOVER_INSTANCES 行セット |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4143aa33cc4c09914ffb05aaccbb12f2fe64d440
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="discoverinstances-rowset"></a>DISCOVER_INSTANCES 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  サーバー上のインスタンスについて記述します。  
  
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
 [OLE DB for OLAP スキーマ行セット](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
