---
title: DataSourceType 要素 (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 015a4cfbb70ddb29216a079dffdfd928029033d3
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34575674"
---
# <a name="datasourcetype-element-xmla"></a>DataSourceType 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
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
|親要素|[[場所]](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 **%Datasourcetype**要素によって、データ ソースを定義するかどうかを決定する、**場所**要素には、ローカル データ ソースまたはリモート データ ソースが含まれています。 バックアップと、リモート パーティションの復元の詳細については、次を参照してください。[データベースのバックアップ、復元、およびデータベースの同期&#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)です。  
  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|[値]|説明|  
|-----------|-----------------|  
|*地元の*|**場所**要素のローカル データ ソースを定義します。 この値が使用されている場合、**復元**と**同期**コマンドで定義されている情報を使用して、**場所**いずれかからデータ ソースを更新する要素が取得された、指定されたバックアップ ファイル、**ファイル**要素を**バックアップ**コマンドまたはで指定されたデータベース、**ソース**要素を**同期**で識別されるコマンド、 **DataSourceID**の要素、**場所**要素。<br /><br /> この値を使用すれば、リレーショナル OLAP (ROLAP) ストレージを使用するオブジェクトで、復元後または同期後に、データおよびメタデータ用に異なるデータベースを使用できます。<br /><br /> メモ: ディメンション テーブルや書き戻しテーブル内のデータなど、ROLAP データがない復元または同期します。 ROLAP オブジェクトのメタデータだけが復元または同期されます。|  
|*リモート*|**場所**要素は、リモート データ ソースを定義します。 この値が使用されている場合、**復元**と**同期**コマンドで定義されている情報を使用して、**場所**復元またはリモートのパーティションを同期する要素指定されたバックアップ ファイルのいずれかから取得した、**ファイル**の要素、**バックアップ**コマンドまたはで指定されたデータベース、**ソース**要素を**同期**で識別されるリモート インスタンスに、コマンド、 **DataSourceID**の**場所**要素。|  
  
## <a name="see-also"></a>参照
 [ConnectionString 要素&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/connectionstring-element-xmla.md)   
 [DataSourceID 要素&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/datasourceid-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
