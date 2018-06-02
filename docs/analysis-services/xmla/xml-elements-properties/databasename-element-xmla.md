---
title: DatabaseName 要素 (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: adc35002f6d5f7cb129131529359e667fb53fdb3
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34573614"
---
# <a name="databasename-element-xmla"></a>DatabaseName 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  親を復元する Analysis Services データベースを識別[復元](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)コマンド。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Restore>  
   ...  
   <DatabaseName>...</DatabaseName>  
   ...  
</Restore>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[[復元]](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 **DatabaseName**要素は、先のデータベースを識別、**復元**コマンドは、バックアップ ファイルを復元します。 この要素が指定されない場合、あるいは空の文字列が含まれる場合には、バックアップ ファイル内に含まれるデータベースの名前が使用されます。  
  
 対象のインスタンスにデータベースが既に存在するエラーが発生しない限り、 **AllowOverwrite**親要素**復元**コマンドに設定されている**True**です。  
  
## <a name="see-also"></a>参照
 [AllowOverwrite 要素&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/allowoverwrite-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
