---
title: データ アクセサー関数 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- data-accessor functions [XQuery]
ms.assetid: 31bad04f-7c74-4773-9f83-612704fdd21c
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 1c28f61a39e45ea101f2e999d5787dfa23cb29c2
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56031793"
---
# <a name="data-accessor-functions"></a>データ アクセサー関数
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  このセクションのトピックでは、データ アクセサー関数のサンプル コードについて説明し、そのコードを提供します。  
  
## <a name="understanding-fndata-fnstring-and-text"></a>fn:data()、fn:string()、text() について  
 XQuery 関数を持つ**fn:data()** ノード、ノード テストからスカラー、型指定された値を抽出する**text()** テキスト ノード、および関数を返す**fn:string()** を返す、ノードの文字列値。 この 3 つのアクセサーの使用方法が紛らわしい場合があります。 次に、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] でこれらを使用する場合のガイドラインを示します。 XML インスタンス\<age > 12\<age/> の図のために使用されます。  
  
-   型指定されていない XML:パスの式/age/text() はテキスト ノード「12」を返します。 関数 fn:data(/age) および fn:string(/age) は文字列値 "12" を返します。  
  
-   型指定された XML:式/age/text() は任意の単純型の静的なエラーを返します\<age > 要素。 一方、fn:data(/age) は整数 12 を返します。 fn:string(/age) は文字列 "12" を返します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [string 関数&#40;XQuery&#41;](../xquery/data-accessor-functions-string-xquery.md)  
  
-   [data 関数&#40;XQuery&#41;](../xquery/data-accessor-functions-data-xquery.md)  
  
## <a name="see-also"></a>参照  
 [パス式&#40;XQuery&#41;](../xquery/path-expressions-xquery.md)  
  
  
