---
title: "データ アクセサー関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- data-accessor functions [XQuery]
ms.assetid: 31bad04f-7c74-4773-9f83-612704fdd21c
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 456d359fd407e305bc8bfb3b85bd29b7bada8382
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="data-accessor-functions"></a>データ アクセサー関数
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  このセクションのトピックでは、データ アクセサー関数のサンプル コードについて説明し、そのコードを提供します。  
  
## <a name="understanding-fndata-fnstring-and-text"></a>fn:data()、fn:string()、text() について  
 XQuery 関数を持つ**fn:data()**値を抽出するスカラー、型指定されたノード、ノード テストから**text()**テキスト ノード、および関数を返す**fn:string()**を返す、ノードの文字列値です。 この 3 つのアクセサーの使用方法が紛らわしい場合があります。 次に、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] でこれらを使用する場合のガイドラインを示します。 XML インスタンス\<age > 12 \< /有効期間の > は、わかりやすくするために使用します。  
  
-   型指定されていない XML : パス式 /age/text() はテキスト ノード "12" を返します。 関数 fn:data(/age) および fn:string(/age) は文字列値 "12" を返します。  
  
-   型指定された XML: 式/age/text() は、任意の単純型の静的なエラーを返します\<age > 要素。 一方、fn:data(/age) は整数 12 を返します。 fn:string(/age) は文字列 "12" を返します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [文字列関数 & #40 です。XQuery と #41 です。](../xquery/data-accessor-functions-string-xquery.md)  
  
-   [data 関数 & #40 です。XQuery と #41 です。](../xquery/data-accessor-functions-data-xquery.md)  
  
## <a name="see-also"></a>参照  
 [パス式 & #40 です。XQuery と #41 です。](../xquery/path-expressions-xquery.md)  
  
  

