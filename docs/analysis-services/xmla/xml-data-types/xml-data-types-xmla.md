---
title: XML データ型 (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c52717a6f061f4708b2d3e46c6d34f837b2039af
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34573784"
---
# <a name="xml-data-types-xmla"></a>XML データ型 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  XML for Analysis (XMLA) 1.1 仕様では、XML 1.0 勧告で定義された標準的なプリミティブ型および派生型に加えて、多次元データおよび表形式データの表記をサポートする追加のデータ型が定義されています。  
  
 XMLA は、次の表に示されているデータ型を使用します。  
  
|データ型|説明|  
|----------------|-----------------|  
|ブール値|標準 XML**ブール**データ型。|  
|Decimal|標準 XML **decimal**データ型。|  
|[EmptyResult](../../../analysis-services/xmla/xml-data-types/emptyresult-data-type-xmla.md)|上の名前空間、**ルート**要素。 結果の値が、XMLA コマンドによって通常返されなかったため、または XMLA コマンドの実行中に、Analysis Services インスタンスでエラーが発生したため、XMLA コマンドが結果を返さない場合は、この名前空間が返されます。|  
|[EnumString](../../../analysis-services/xmla/xml-data-types/enumstring-data-type-xmla.md)|特定の列挙子に関連した名前付き文字列定数のセット。|  
|Integer|標準 XML **int**データ型。|  
|[MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md)|によって返される多次元データ、*結果*のパラメーター、 [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドです。|  
|[結果セット](../../../analysis-services/xmla/xml-data-types/resultset-data-type-xmla.md)|自己記述型 XML 結果セットがによって返される、 **Execute**メソッドです。|  
|[行セット](../../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md)|によって返される、埋め込みの XML スキーマによって構造化されたデータ ソースから行、 [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md)メソッドです。|  
|String|XML**文字列**データ型。|  
|UnsignedInt|XML **unsignedInt**スキーマの型。|  
  
 標準的な XML データ型の詳細な説明については、World Wide Web Consortium (W3C) 勧告候補を参照してください。  
  
## <a name="see-also"></a>参照
 [XML 要素&#40;XMLA&#41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)   
 [XML for Analysis &#40;XMLA&#41;参照](../../../analysis-services/xmla/xml-for-analysis-xmla-reference.md)  
  
  
