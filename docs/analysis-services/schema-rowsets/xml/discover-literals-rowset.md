---
title: DISCOVER_LITERALS 行セット |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6b27704678a817bf3288aa72b9d8e4b091bb6c00
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="discoverliterals-rowset"></a>DISCOVER_LITERALS 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis (XMLA) プロバイダーによってサポートされているデータ型や値などを含むリテラルに関する情報を返します。  
  
 呼び出す場合は、 [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md)メソッドを**DISCOVER_LITERALS**の列挙値に、 [RequestType](../../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md)要素、 **Discover**メソッドを返します、 **DISCOVER_LITERALS**行セット。  
  
## <a name="rowset-columns"></a>行セットの列  
 **DISCOVER_LITERALS**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|Description|  
|-----------------|--------------------|------------|-----------------|  
|**LiteralName**|**DBTYPE_WSTR**||行に記述されているリテラルの名前。<br /><br /> 例: **DBLITERAL_LIKE_PERCENT**|  
|**LiteralValue**|**DBTYPE_WSTR**||実際のリテラル値。<br /><br /> たとえば場合、 **LiteralName**は**DBLITERAL_LIKE_PERCENT**で、パーセント記号 (**%**) 値、LIKE 句に 0 個以上の文字と一致します。**LiteralValue**列が"**%**"です。|  
|**LiteralInvalidChars**|**DBTYPE_WSTR**||リテラルで有効でない文字。<br /><br /> たとえば、テーブル名には、文字の数字以外のものを含めることができます、この文字列は"**0123456789**"です。|  
|**LiteralInvalidStartingChars**|**DBTYPE_WSTR**||リテラルの先頭文字として有効でない文字。 これは、そのリテラルは、任意の有効な文字で開始できる場合、 **null**です。|  
|**LiteralMaxLength**|**DBTYPE_I4**||リテラルの最大文字数。 最大値がないか、不明な場合、この値は -1 となります。|  
|**LiteralNameEnumValue**|**DBTYPE_I4**|||  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="restriction-columns"></a>制限の列  
 **DISCOVER_LITERALS**行セットは、次の表の列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**LiteralName**|**DBTYPE_WSTR**|省略可。|  
  
## <a name="see-also"></a>参照  
 [XML for Analysis スキーマ行セット](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)   
 [DISCOVER_KEYWORDS 行セット & #40 です。XMLA & #41;](../../../analysis-services/schema-rowsets/xml/discover-keywords-rowset-xmla.md)  
  
  
