---
title: "DISCOVER_LITERALS 行セット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DISCOVER_LITERALS
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DISCOVER_LITERALS rowset
ms.assetid: 1bf0a2e2-a419-4c25-b271-37dfa44de2ea
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 95037ba44f93df3aa0dbe5ad4279ca1ca9a1bf28
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="discoverliterals-rowset"></a>DISCOVER_LITERALS 行セット
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
 [DISCOVER_KEYWORDS 行セット & #40 です。XMLA &#41;](../../../analysis-services/schema-rowsets/xml/discover-keywords-rowset-xmla.md)  
  
  
