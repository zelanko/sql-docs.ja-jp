---
title: "Xml データ型に対する XQuery 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/09/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: xquery
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
dev_langs: XML
helpviewer_keywords:
- XQuery, functions
- xml data type [SQL Server], XQuery
- functions [SQL Server], XQuery
ms.assetid: 8df0877d-a03f-4ca9-b84e-908c4bb42b5e
caps.latest.revision: "37"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 6a9f6887894745f737cce1eb134b4076339861af
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="xquery-functions-against-the-xml-data-type"></a>xml データ型に対する XQuery 関数
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  このトピックとサブトピックに対して XQuery を指定するときに使用できる関数を記述、 **xml**データ型。 W3C 仕様では、次を参照してください。 [http://www.w3.org/TR/2004/WD-xpath-functions-20040723](http://go.microsoft.com/fwlink/?LinkId=4873)です。  
  
 XQuery 関数は http://www.w3.org/2004/07/xpath-functions 名前空間に属します。 W3C 仕様では、これらの関数を表すために "fn:" という名前空間プレフィックスを使用しています。 この関数を使用するときに、"fn:" 名前空間プレフィックスを明示的に指定する必要はありません。 名前空間プレフィックスは明示的に指定する必要がないので、ここでは、読みやすさを考慮して名前空間プレフィックスは省略します。  
  
 次の表は、XQuery 関数に対してはサポートされている、 **xml**データ型。  
  
|カテゴリ|関数名|  
|--------------|-------------------|  
|[数値の値に対する関数](http://msdn.microsoft.com/library/d5740a32-b174-43b9-b64d-1cc6edc50cff)|[ceiling](../xquery/numeric-values-functions-ceiling.md)|  
||[floor](../xquery/numeric-values-functions-floor.md)|  
||[丸める](../xquery/numeric-values-functions-round.md)|  
|[文字列値に XQuery 関数](http://msdn.microsoft.com/library/2dccefef-5d90-4f56-bda7-4c1954d8a730)|[concat](../xquery/functions-on-string-values-concat.md)|  
||[含まれています](../xquery/functions-on-string-values-contains.md)|  
||[部分文字列](../xquery/functions-on-string-values-substring.md)|  
||[lower-case 関数 &#40;です。XQuery と #41 です。](../xquery/functions-on-string-values-lower-case.md)|  
||[文字列長](../xquery/functions-on-string-values-string-length.md)|  
||[大文字関数と #40 です。XQuery と #41 です。](../xquery/functions-on-string-values-upper-case.md)|  
|ブール値に対する関数|[じゃない](../xquery/functions-on-boolean-values-not-function.md)|  
|[ノードの関数](http://msdn.microsoft.com/library/09a8affa-3341-4f50-aebc-fdf529e00c08)|[数](../xquery/functions-on-nodes-number.md)|  
||[local-name 関数 (XQuery)](../xquery/functions-on-nodes-local-name.md)|  
||[名前空間 uri 関数 (XQuery)](../xquery/functions-on-nodes-namespace-uri.md)|  
|[コンテキスト関数](http://msdn.microsoft.com/library/f7d8af33-9de9-450c-a667-23dee3129b5f)|[前の](../xquery/context-functions-last-xquery.md)|  
||[位置](../xquery/context-functions-position-xquery.md)|  
|[シーケンスの関数](http://msdn.microsoft.com/library/672d2795-53ab-49c2-bf24-bc81a47ecd3f)|[空](../xquery/functions-on-sequences-empty.md)|  
||[個別の値](../xquery/functions-on-sequences-distinct-values.md)|  
||[id 関数 (XQuery)](../xquery/functions-on-sequences-id.md)|  
|[集計関数と #40 です。XQuery と #41 です。](http://msdn.microsoft.com/library/be647ef1-291e-4a5d-ab18-07c759efe176)|[count](../xquery/aggregate-functions-count.md)|  
||[avg](../xquery/aggregate-functions-avg.md)|  
||[最小値](../xquery/aggregate-functions-min.md)|  
||[max](../xquery/aggregate-functions-max.md)|  
||[合計](../xquery/aggregate-functions-sum.md)|  
|[コンス トラクター関数 &#40;です。XQuery と #41 です。](../xquery/constructor-functions-xquery.md)|[コンス トラクター関数](../xquery/constructor-functions-xquery.md)|  
|[データ アクセサー関数](../xquery/data-accessor-functions.md)|[string](../xquery/data-accessor-functions-string-xquery.md)|  
||[data](../xquery/data-accessor-functions-data-xquery.md)|  
|[ブール値コンス トラクター関数 &#40;です。XQuery と #41 です。](http://msdn.microsoft.com/library/fa907f39-d4b7-4495-b829-c788928e0f64)|[true 関数 (XQuery)](../xquery/boolean-constructor-functions-true-xquery.md)|  
||[false 関数 (XQuery)](../xquery/boolean-constructor-functions-false-xquery.md)|  
|[Qname &#40; に関連する関数XQuery と #41 です。](http://msdn.microsoft.com/library/7e07eb26-f551-4b63-ab77-861684faff71)|[Expanded-qname() (XQuery)](../xquery/functions-related-to-qnames-expanded-qname.md)|  
||[ローカル名-からの QName (XQuery)](../xquery/functions-related-to-qnames-local-name-from-qname.md)|  
||[名前空間 uri の QName の (XQuery)](../xquery/functions-related-to-qnames-namespace-uri-from-qname.md)|  
|[SQL Server XQuery 拡張関数します。](http://msdn.microsoft.com/library/4bc5d499-5fec-4c3f-b11e-5ab5ef9d8f97)|[sql:column() 関数 (XQuery)](../xquery/xquery-extension-functions-sql-column.md)|  
||[sql:variable() 関数 (XQuery)](../xquery/xquery-extension-functions-sql-variable.md)|  
  
## <a name="see-also"></a>参照  
 [xml データ型メソッド](../t-sql/xml/xml-data-type-methods.md)   
 [XQuery 言語リファレンス &#40;SQL Server&#41;](../xquery/xquery-language-reference-sql-server.md)   
 [XML Data &#40;SQL Server&#41;](../relational-databases/xml/xml-data-sql-server.md)  
  
  
