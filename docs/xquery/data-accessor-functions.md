---
title: データアクセサー関数 |Microsoft Docs
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
ms.openlocfilehash: b3726686a2c0e5229a0fccf4d9f51c0e1404f1a3
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68038952"
---
# <a name="data-accessor-functions"></a>データ アクセサー関数
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  このセクションのトピックでは、データアクセサー関数のサンプルコードについて説明します。  
  
## <a name="understanding-fndata-fnstring-and-text"></a>fn:data()、fn:string()、text() について  
 XQuery には、スカラー値を抽出するための関数**fn: data ()** 、ノードからの型指定された値、テキストノードを返すノードテスト**テキスト (** )、およびノードの文字列値を返す関数**fn: string ()** があります。 この 3 つのアクセサーの使用方法が紛らわしい場合があります。 次に、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] でこれらを使用する場合のガイドラインを示します。 例とし\<て、XML\<インスタンス age>12/age> が使用されています。  
  
-   型指定されていない XML: パス式/age/text () は、テキストノード "12" を返します。 関数 fn: data (/age) は文字列値 "12" を返します。したがって、fn: string (/age) が返されます。  
  
-   型指定された XML: 式/age/text () は、任意の単純\<型の age> 要素に対して静的なエラーを返します。 一方、fn: data (/age) は整数12を返します。 fn:string(/age) は文字列 "12" を返します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [string 関数 &#40;XQuery&#41;](../xquery/data-accessor-functions-string-xquery.md)  
  
-   [データ関数 &#40;XQuery&#41;](../xquery/data-accessor-functions-data-xquery.md)  
  
## <a name="see-also"></a>参照  
 [パス式 &#40;XQuery&#41;](../xquery/path-expressions-xquery.md)  
  
  
