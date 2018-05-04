---
title: パス式の構文の省略形を使用して |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql
ms.service: ''
ms.component: xquery
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- axis step [XQuery]
- abbreviated syntax [XQuery]
ms.assetid: f83c2e41-5722-47c3-b5b8-bf0f8cbe05d3
caps.latest.revision: 23
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 9751d48c38ae96f85d0cc97992f5dd5acfef9b2f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="path-expressions---using-abbreviated-syntax"></a>パス式の省略構文の使用
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  すべての例で[xquery パス式について](../xquery/path-expressions-xquery.md)パス式の省略構文を使用します。 パス式の軸ステップの省略構文では、軸名とノード テストを 2 つのコロン (::) で区切り、その後にステップ修飾子を指定します。ステップ修飾子は、指定しなくてもかまいません。  
  
 以下に例を示します。  
  
```  
child::ProductDescription[attribute::ProductModelID=19]  
```  
  
 XQuery は、パス式で次の省略をサポートしています。  
  
-   **子**軸は既定の軸です。 したがって、**子::** 軸は、式のステップから省略できます。 たとえば、`/child::ProductDescription/child::Summary`として記述できます`/ProductDescription/Summary`です。  
  
-   **属性**と軸を短縮できる@です。 たとえば、`/child::ProductDescription[attribute::ProductModelID=10]`として記述できます`/ProudctDescription[@ProductModelID=10]`です。  
  
-   A **/descendant-or-self::node()/** と短縮できる//です。 たとえば、`/descendant-or-self::node()/child::act:telephoneNumber`として記述できます`//act:telephoneNumber`です。  
  
     上記のクエリは、Contact テーブルの AdditionalContactInfo 列に格納されているすべての電話番号を取得しています。 AdditionalContactInfo のスキーマが方法で定義されている、 \<telephoneNumber > 要素は、ドキュメントのどこに表示できます。 したがって、すべての電話番号を取得するには、ドキュメント内のすべてのノードを検索する必要があります。 検索は、ドキュメントのルートから開始され、続いてすべての子孫ノードが検索されます。  
  
     次のクエリは、特定の顧客の電話番号をすべて取得します。  
  
    ```  
    SELECT AdditionalContactInfo.query('             
                declare namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";             
                declare namespace crm="http://schemas.adventure-works.com/Contact/Record";             
                declare namespace ci="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";             
                /descendant-or-self::node()/child::act:telephoneNumber             
                ') as result             
    FROM Person.Contact             
    WHERE ContactID=1             
    ```  
  
     省略形の構文では、パス式に置き換えた場合`//act:telephoneNumber`、同じ結果を受信します。  
  
-   **Self::node()** の手順では、1 つのドット (.) を省略できます。 ただし、ドットは同等またはで交換可能で、 **self::node()** です。  
  
     たとえば、次のクエリでは、ドットを使用して、ノードではなく値を表しています。  
  
    ```  
    ("abc", "cde")[. > "b"]  
    ```  
  
-   **Parent::node()** の手順では、2 つのドット (.) を省略できます。  
  
  
