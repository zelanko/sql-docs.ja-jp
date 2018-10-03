---
title: TableNotifications 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- TableNotifications Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#TableNotifications
- microsoft.xml.analysis.tablenotifications
- http://schemas.microsoft.com/analysisservices/2003/engine#TableNotifications
helpviewer_keywords:
- TableNotifications element
ms.assetid: 650f307d-1f11-47ce-9d0e-19cf3b1835b7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 48bb3295144c554e9c1aca297ddcffd19f2a247a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48197902"
---
# <a name="tablenotifications-element-xmla"></a>TableNotifications 要素 (XMLA)
  コレクションを含む[TableNotification](tablenotification-element-xmla.md)によって使用される要素、 [NotifyTableChange](../xml-elements-commands/notifytablechange-element-xmla.md)コマンド。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<NotifyTableChange >  
   ...  
   <TableNotifications>  
      <TableNotification>...</TableNotification>  
   </TableNotifications>  
   ...  
</NotifyTableChange>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[NotifyTableChange](../xml-elements-commands/notifytablechange-element-xmla.md)|  
|子要素|[TableNotification](tablenotification-element-xmla.md)|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>関連項目  
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
