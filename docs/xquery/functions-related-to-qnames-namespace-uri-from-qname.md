---
title: 名前空間の uri-から-QName (XQuery) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: sql
ms.component: xquery
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- fn:namespace-uri-from-QName function
- namespace-uri-from-QName function
ms.assetid: 4ab3f003-2a3b-4268-9e88-b615e35701b2
caps.latest.revision: 13
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 67475f0f7e10f8d49e4adefab8b44c2d4cefc272
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37999804"
---
# <a name="functions-related-to-qnames---namespace-uri-from-qname"></a>QName の名前空間 uri QNames に関係する関数
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  指定された QName の名前空間 uri を表す文字列を返します *$arg*します。 場合、結果は空のシーケンス *$arg*は空のシーケンスです。  
  
## <a name="syntax"></a>構文  
  
```  
namespace-uri-from-QName($arg as xs:QName?) as xs:string?  
```  
  
## <a name="arguments"></a>引数  
 *$arg*  
 名前空間 URI が返される QName です。  
  
## <a name="examples"></a>使用例  
 このトピックではさまざまなに格納されている XML インスタンスに対して XQuery の例について**xml**型の列には、AdventureWorks データベース。  
  
### <a name="a-retrieve-the-namespace-uri-from-a-qname"></a>A. QName からの名前空間 URI の取得  
 実際のサンプルでは、次を参照してください。 [QName のローカル名&#40;XQuery&#41;](../xquery/functions-related-to-qnames-local-name-from-qname.md)します。  
  
### <a name="implementation-limitations"></a>実装の制限事項  
 制限事項を次に示します。  
  
-   **Namespace-uri-from-QName()** 関数は、xs:anyURI ではなく xs:string のインスタンスを返します。  
  
## <a name="see-also"></a>参照  
 [QNames に関係する関数&#40;XQuery&#41;](http://msdn.microsoft.com/library/7e07eb26-f551-4b63-ab77-861684faff71)  
  
  
