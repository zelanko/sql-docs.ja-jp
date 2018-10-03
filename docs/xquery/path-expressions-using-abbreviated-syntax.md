---
title: パス式の構文を使用して簡略化された |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- axis step [XQuery]
- abbreviated syntax [XQuery]
ms.assetid: f83c2e41-5722-47c3-b5b8-bf0f8cbe05d3
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 7454eb815faf26248b4326487a833f0038f64c1e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47698270"
---
# <a name="path-expressions---using-abbreviated-syntax"></a>パス式 - 省略構文の使用
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  すべての例で[では、XQuery パス式について](../xquery/path-expressions-xquery.md)パス式は省略しない構文を使用します。 パス式の軸ステップの省略構文では、軸名とノード テストを 2 つのコロン (::) で区切り、その後にステップ修飾子を指定します。ステップ修飾子は、指定しなくてもかまいません。  
  
 以下に例を示します。  
  
```  
child::ProductDescription[attribute::ProductModelID=19]  
```  
  
 XQuery は、パス式で次の省略をサポートしています。  
  
-   **子**軸は既定の軸。 そのため、**子::** 軸は、式のステップから省略できます。 たとえば、`/child::ProductDescription/child::Summary`として記述できます`/ProductDescription/Summary`します。  
  
-   **属性**として省略できます@します。 たとえば、`/child::ProductDescription[attribute::ProductModelID=10]`として記述できます`/ProudctDescription[@ProductModelID=10]`します。  
  
-   A **/descendant-or-self::node()** ように短縮できます//。 たとえば、`/descendant-or-self::node()/child::act:telephoneNumber`として記述できます`//act:telephoneNumber`します。  
  
     上記のクエリは、Contact テーブルの AdditionalContactInfo 列に格納されているすべての電話番号を取得しています。 AdditionalContactInfo のスキーマが方法で定義されている、 \<telephoneNumber > 要素がドキュメントにどこでも表示できます。 したがって、すべての電話番号を取得するには、ドキュメント内のすべてのノードを検索する必要があります。 検索は、ドキュメントのルートから開始され、続いてすべての子孫ノードが検索されます。  
  
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
  
     省略構文のパス式に置き換えた場合`//act:telephoneNumber`、同じ結果が表示されます。  
  
-   **Self::node()** の手順では、1 つのドット (.) を省略できます。 ただし、ドットでないと同等か、互換性、 **self::node()** します。  
  
     たとえば、次のクエリでは、ドットを使用して、ノードではなく値を表しています。  
  
    ```  
    ("abc", "cde")[. > "b"]  
    ```  
  
-   **Parent::node()** の手順では、2 つのドット (.) を省略できます。  
  
  
