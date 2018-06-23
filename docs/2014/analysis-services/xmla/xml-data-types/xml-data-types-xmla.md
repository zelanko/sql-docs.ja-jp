---
title: XML データ型 (XMLA) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
- apinav
helpviewer_keywords:
- XML data types [XMLA]
- data types [XML for Analysis]
- XMLA, data types
- XML for Analysis, data types
ms.assetid: 979b5384-90d9-4e09-9286-1d1eafdc4864
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: d7a21691474e890ba8614715b18e972d1353b2c6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36085501"
---
# <a name="xml-data-types-xmla"></a>XML データ型 (XMLA)
  XML for Analysis (XMLA) 1.1 仕様では、XML 1.0 勧告で定義された標準的なプリミティブ型および派生型に加えて、多次元データおよび表形式データの表記をサポートする追加のデータ型が定義されています。  
  
 XMLA は、次の表に示されているデータ型を使用します。  
  
|データ型|説明|  
|----------------|-----------------|  
|ブール値|標準的な XML の `boolean` データ型。|  
|Decimal|標準的な XML の `decimal` データ型。|  
|[EmptyResult](emptyresult-data-type-xmla.md)|`root` 要素上の名前空間。 エラーが発生したためか、いずれかの XMLA コマンドが通常結果を返さないため、XMLA コマンドが結果を返さない場合、この名前空間が返されます、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] XMLA コマンドの実行中にインスタンス。|  
|[EnumString](enumstring-data-type-xmla.md)|特定の列挙子に関連した名前付き文字列定数のセット。|  
|Integer|標準的な XML の `int` データ型。|  
|[MDDataSet](mddataset-data-type-xmla.md)|によって返される多次元データ、*結果*のパラメーター、 [Execute](../xml-elements-methods-execute.md)メソッドです。|  
|[結果セット](resultset-data-type-xmla.md)|`Execute` メソッドによって返される自己記述型 XML 結果セット。|  
|[行セット](rowset-data-type-xmla.md)|によって返される、埋め込みの XML スキーマによって構造化されたデータ ソースから行、 [Discover](../xml-elements-methods-discover.md)メソッドです。|  
|String|XML の `string` データ型。|  
|UnsignedInt|XML の `unsignedInt` スキーマ型。|  
  
 標準的な XML データ型の詳細な説明については、World Wide Web Consortium (W3C) 勧告候補を参照してください。  
  
## <a name="see-also"></a>参照  
 [XML 要素&#40;XMLA&#41;](../../dev-guide/xml-elements-xmla.md)   
 [XML for Analysis &#40;XMLA&#41;参照](../xml-for-analysis-xmla-reference.md)  
  
  