---
title: DataSourceID 要素 (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 883fa5df355874516ffd6f0cac01ff50d727d737
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34573764"
---
# <a name="datasourceid-element-xmla"></a>DataSourceID 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  によって使用されるデータ ソースを識別、[場所](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)実行中に、[バックアップ](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)、[復元](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)、または[同期](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)コマンド。  
  
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
|親要素|[[場所]](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 **DataSourceID**要素には、リモート パーティションの情報にバックアップ、復元、または同期されているリモート インスタンスを識別するソース インスタンス上のデータ ソースの名前が含まれています。  
  
 バックアップと、リモート パーティションの復元の詳細については、次を参照してください。[データベースのバックアップ、復元、およびデータベースの同期&#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)です。  
  
## <a name="see-also"></a>参照
 [ConnectionString 要素&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/connectionstring-element-xmla.md)   
 [DataSourceType 要素&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/datasourcetype-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
