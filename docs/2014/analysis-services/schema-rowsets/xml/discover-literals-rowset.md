---
title: DISCOVER_LITERALS 行セット |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DISCOVER_LITERALS
topic_type:
- apiref
helpviewer_keywords:
- DISCOVER_LITERALS rowset
ms.assetid: 1bf0a2e2-a419-4c25-b271-37dfa44de2ea
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e218c03cd6d2f8dbf06501dd18a2c4c3e4977eca
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48063218"
---
# <a name="discoverliterals-rowset"></a>DISCOVER_LITERALS 行セット
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis (XMLA) プロバイダーによってサポートされているデータ型や値などを含むリテラルに関する情報を返します。  
  
 呼び出す場合、 [Discover](../../xmla/xml-elements-methods-discover.md)メソッドを`DISCOVER_LITERALS`列挙値、 [RequestType](../../xmla/xml-elements-properties/type-element-xmla.md)要素、`Discover`メソッドを返します。、`DISCOVER_LITERALS`行セット。  
  
## <a name="rowset-columns"></a>行セットの列  
 `DISCOVER_LITERALS`行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|説明|  
|-----------------|--------------------|------------|-----------------|  
|`LiteralName`|`DBTYPE_WSTR`||行に記述されているリテラルの名前。<br /><br /> 例: `DBLITERAL_LIKE_PERCENT`|  
|`LiteralValue`|`DBTYPE_WSTR`||実際のリテラル値。<br /><br /> たとえば、`LiteralName` が `DBLITERAL_LIKE_PERCENT` で、パーセント記号 (`%`) が LIKE 句の 0 個以上の文字と一致する場合、`LiteralValue` 列の値は "`%`" です。|  
|`LiteralInvalidChars`|`DBTYPE_WSTR`||リテラルで有効でない文字。<br /><br /> たとえば、テーブル名に数字を除くすべての文字を含めることができる場合、この文字列は "`0123456789`" となります。|  
|`LiteralInvalidStartingChars`|`DBTYPE_WSTR`||リテラルの先頭文字として有効でない文字。 リテラルの先頭に有効な任意の文字を使用できる場合、これは `null` となります。|  
|`LiteralMaxLength`|`DBTYPE_I4`||リテラルの最大文字数。 最大値がないか、不明な場合、この値は -1 となります。|  
|`LiteralNameEnumValue`|`DBTYPE_I4`|||  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="restriction-columns"></a>制限の列  
 `DISCOVER_LITERALS`行セットは、次の表の列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|`LiteralName`|`DBTYPE_WSTR`|任意。|  
  
## <a name="see-also"></a>参照  
 [XML for Analysis スキーマ行セット](xml-for-analysis-schema-rowsets.md)   
 [DISCOVER_KEYWORDS 行セット&#40;XMLA&#41;](discover-keywords-rowset-xmla.md)  
  
  
