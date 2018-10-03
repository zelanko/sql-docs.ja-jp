---
title: DataSourceID 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DataSourceID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.datasourceid
- urn:schemas-microsoft-com:xml-analysis#DataSourceID
- http://schemas.microsoft.com/analysisservices/2003/engine#DataSourceID
helpviewer_keywords:
- DataSourceID element
ms.assetid: 695522c7-acca-420a-a5fb-f01f3fd9a96b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2a403655594027599d56490c6bd2456c0713bf34
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48099448"
---
# <a name="datasourceid-element-xmla"></a>DataSourceID 要素 (XMLA)
  使用されるデータ ソースを識別、[場所](location-element-xmla.md)中に要素を[バックアップ](../xml-elements-commands/backup-element-xmla.md)、[復元](../xml-elements-commands/restore-element-xmla.md)、または[同期](../xml-elements-commands/synchronize-element-xmla.md)コマンド。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Location>  
   ...  
   <DataSourceID>...</DataSourceID>  
   ...  
</Location>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[[場所]](location-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `DataSourceID` 要素は、リモート パーティション情報をバックアップ、復元、または同期する場所であるリモート インスタンスを識別するソース インスタンス上のデータ ソースの名前を含みます。  
  
 バックアップおよびリモート パーティションを復元する詳細については、次を参照してください。[データベースのバックアップ、復元、およびデータベースの同期&#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)します。  
  
## <a name="see-also"></a>参照  
 [ConnectionString 要素&#40;XMLA&#41;](connectionstring-element-xmla.md)   
 [DataSourceType 要素&#40;XMLA&#41;](type-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
