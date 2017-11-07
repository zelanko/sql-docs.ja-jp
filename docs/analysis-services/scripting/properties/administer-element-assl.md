---
title: "Administer 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Administer Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Administer
helpviewer_keywords:
- Administer element
ms.assetid: 52924cd6-6176-47c8-ab17-4ee0e0ce42b1
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 38f477ef873f841698755561f14740433b6e9cfa
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="administer-element-assl"></a>Administer 要素 (ASSL)
  関連付けられたアクセス許可を管理する権限が含まれるかどうかを示します、[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DatabasePermission>  
      ...  
      <Administer>...</Administer>  
   ...  
</DatabasePermission>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|ブール値|  
|既定値|False|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DatabasePermission](../../../analysis-services/scripting/objects/databasepermission-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **Administer**要素は、ユーザーが、指定されたデータベースでのみ管理機能を実行できるかどうかを示します。 サーバー管理者ロールは、インスタンスに含まれているすべてのデータベースに対して管理機能を実行できます。  
  
 親に対応する要素**Administer**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.DatabasePermission>します。  
  
## <a name="see-also"></a>参照  
 [Permission データ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)   
 [Role 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/role-element-assl.md)   
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

