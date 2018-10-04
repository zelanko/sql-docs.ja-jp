---
title: ConnectionString 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ConnectionString Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.connectionstring
- urn:schemas-microsoft-com:xml-analysis#ConnectionString
- http://schemas.microsoft.com/analysisservices/2003/engine#ConnectionString
helpviewer_keywords:
- ConnectionString element
ms.assetid: 3b0575aa-79ed-4f14-ae7e-dd587af4cdb1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6b4f186e7beebedd11a9100d1091fc38acaa9dc0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48061492"
---
# <a name="connectionstring-element-xmla"></a>ConnectionString 要素 (XMLA)
  親で使用される接続文字列を含む[場所](location-element-xmla.md)または[ソース](source-element-xmla.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Location> <!-- or Source -->  
   ...  
   <ConnectionString>...</ConnectionString>  
   ...  
</Location>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|カーディナリティの先祖または親|Cardinality|  
|[[場所]](location-element-xmla.md)|1-1 : 必須要素で、1 回だけ出現します|  
|[Source](source-element-xmla.md)|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[場所](location-element-xmla.md)、[ソース](source-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `Location` 要素の場合、`ConnectionString` 要素は、ローカル データ ソースの更新またはリモート インスタンスへの接続のために `Restore` または `Synchronize` コマンドで使用される接続文字列を含みます。  
  
 `Source` 要素の場合、`ConnectionString` 要素は、同期元インスタンスへの接続のために `Synchronize` コマンドで使用される接続文字列を含みます。  
  
 バックアップと復元のオブジェクトの詳細については、次を参照してください。[データベースのバックアップ、復元、およびデータベースの同期&#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)します。  
  
## <a name="see-also"></a>参照  
 [Restore 要素&#40;XMLA&#41;](../xml-elements-commands/restore-element-xmla.md)   
 [Synchronize 要素&#40;XMLA&#41;](../xml-elements-commands/synchronize-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
