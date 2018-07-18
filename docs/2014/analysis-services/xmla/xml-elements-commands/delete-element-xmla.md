---
title: Delete 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Delete Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.delete
- urn:schemas-microsoft-com:xml-analysis#Delete
- http://schemas.microsoft.com/analysisservices/2003/engine#Delete
helpviewer_keywords:
- Delete element
ms.assetid: 76201b18-11e9-4815-9287-27a068d8fbc5
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4b308a3fb9c0e2a58c830d614e7b2115b8b0d50c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37173253"
---
# <a name="delete-element-xmla"></a>Delete 要素 (XMLA)
  オブジェクトを削除する[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Command>  
   <Delete IgnoreFailures="boolean">  
      <Object>...</Object>  
   </Delete>  
</Command>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Command](../xml-elements-properties/command-element-xmla.md)|  
|子要素|[Object](../xml-elements-properties/object-element-xmla.md)|  
  
## <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|IgnoreFailures|省略可能な`Boolean`属性。 これを True に設定すると、`Execute` メソッドはネットワーク エラーまたはリモート パーティションに関連するエラーを無視します。|  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>参照  
 [コマンド&#40;XMLA&#41;](xml-elements-commands.md)  
  
  
