---
title: "名前空間 uri の QName の (XQuery) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
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
- fn:namespace-uri-from-QName function
- namespace-uri-from-QName function
ms.assetid: 4ab3f003-2a3b-4268-9e88-b615e35701b2
caps.latest.revision: "13"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 11e9a535a3cd2e8af3f6db1533b0cb35312905db
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="functions-related-to-qnames---namespace-uri-from-qname"></a>Qname の名前空間 uri から QName に関連する関数
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  指定された QName の名前空間 uri を表す文字列を返します*$arg*です。 結果には、空のシーケンスがある場合は*$arg*空のシーケンスします。  
  
## <a name="syntax"></a>構文  
  
```  
namespace-uri-from-QName($arg as xs:QName?) as xs:string?  
```  
  
## <a name="arguments"></a>引数  
 *$arg*  
 名前空間 URI が返される QName です。  
  
## <a name="examples"></a>使用例  
 このトピックでは、さまざまなに格納されている XML インスタンスに対して XQuery の例は、 **xml** AdventureWorks データベース内の列を入力します。  
  
### <a name="a-retrieve-the-namespace-uri-from-a-qname"></a>A. QName からの名前空間 URI の取得  
 作業用サンプルについては、次を参照してください。 [QName のローカル名 &#40;です。XQuery と #41 です。](../xquery/functions-related-to-qnames-local-name-from-qname.md)  
  
### <a name="implementation-limitations"></a>実装の制限事項  
 制限事項を次に示します。  
  
-   **Namespace-uri-from-QName()**関数 xs:anyURI ではなく xs:string のインスタンスを返します。  
  
## <a name="see-also"></a>参照  
 [Qname &#40; に関連する関数XQuery と #41 です。](http://msdn.microsoft.com/library/7e07eb26-f551-4b63-ab77-861684faff71)  
  
  
