---
title: "DataSourceType 要素 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DataSourceType Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#DataSourceType
- microsoft.xml.analysis.datasourcetype
- http://schemas.microsoft.com/analysisservices/2003/engine#DataSourceType
helpviewer_keywords: DataSourceType element
ms.assetid: f5a348b1-911b-4139-832e-4bcb6d80a728
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 0474881e6ca90b395bd908a8e152688b8784557b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="datasourcetype-element-xmla"></a>DataSourceType 要素 (XMLA)
  示すかどうか、[場所](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)の指定された要素、[復元](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)または[同期](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)コマンドは、ローカルまたはリモートです。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Location>  
   ...  
   <DataSourceType>...</DataSourceType>  
   ...  
</Location>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*リモート*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[場所](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **%Datasourcetype**要素によって、データ ソースを定義するかどうかを決定する、**場所**要素には、ローカル データ ソースまたはリモート データ ソースが含まれています。 バックアップと、リモート パーティションの復元の詳細については、次を参照してください。[データベースのバックアップ、復元、およびデータベースの同期 (&) #40 です。XMLA &#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|Description|  
|-----------|-----------------|  
|*地元の*|**場所**要素のローカル データ ソースを定義します。 この値が使用されている場合、**復元**と**同期**コマンドで定義されている情報を使用して、**場所**いずれかからデータ ソースを更新する要素が取得された、指定されたバックアップ ファイル、**ファイル**要素を**バックアップ**コマンドまたはで指定されたデータベース、**ソース**要素を**同期**で識別されるコマンド、 **DataSourceID**の要素、**場所**要素。<br /><br /> この値を使用すれば、リレーショナル OLAP (ROLAP) ストレージを使用するオブジェクトで、復元後または同期後に、データおよびメタデータ用に異なるデータベースを使用できます。<br /><br /> メモ: ディメンション テーブルや書き戻しテーブル内のデータなど、ROLAP データがない復元または同期します。 ROLAP オブジェクトのメタデータだけが復元または同期されます。|  
|*リモート*|**場所**要素は、リモート データ ソースを定義します。 この値が使用されている場合、**復元**と**同期**コマンドで定義されている情報を使用して、**場所**復元またはリモートのパーティションを同期する要素指定されたバックアップ ファイルのいずれかから取得した、**ファイル**の要素、**バックアップ**コマンドまたはで指定されたデータベース、**ソース**要素を**同期**で識別されるリモート インスタンスに、コマンド、 **DataSourceID**の**場所**要素。|  
  
## <a name="see-also"></a>参照  
 [ConnectionString 要素 &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/connectionstring-element-xmla.md)   
 [DataSourceID 要素 &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/datasourceid-element-xmla.md)   
 [プロパティ &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
