---
title: パス式での省略構文の使用 |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- axis step [XQuery]
- abbreviated syntax [XQuery]
ms.assetid: f83c2e41-5722-47c3-b5b8-bf0f8cbe05d3
author: rothja
ms.author: jroth
ms.openlocfilehash: 8e75db08f283631cf9b5daf064790786a1abc10f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67946414"
---
# <a name="path-expressions---using-abbreviated-syntax"></a>パス式 - 省略構文の使用
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [XQuery のパス式を理解](../xquery/path-expressions-xquery.md)するすべての例では、パス式の省略構文を使用します。 パス式の軸ステップの省略構文では、軸名とノード テストを 2 つのコロン (::) で区切り、その後にステップ修飾子を指定します。ステップ修飾子は、指定しなくてもかまいません。  
  
 次に例を示します。  
  
```  
child::ProductDescription[attribute::ProductModelID=19]  
```  
  
 XQuery は、パス式で次の省略をサポートしています。  
  
-   **子**軸は既定の軸です。 したがって、式のステップでは、 **child::** axis を省略できます。 たとえば、 `/child::ProductDescription/child::Summary`はとして`/ProductDescription/Summary`書き込むことができます。  
  
-   **属性**軸はとして@省略できます。 たとえば、 `/child::ProductDescription[attribute::ProductModelID=10]`はとして`/ProudctDescription[@ProductModelID=10]`書き込むことができます。  
  
-   **/Descendant-or-self:: node ()/** は//のように省略できます。 たとえば、 `/descendant-or-self::node()/child::act:telephoneNumber`はとして`//act:telephoneNumber`書き込むことができます。  
  
     上記のクエリは、Contact テーブルの AdditionalContactInfo 列に格納されているすべての電話番号を取得します。 AdditionalContactInfo のスキーマは、ドキュメント内の任意の場所\<で telephoneNumber> 要素を表示できる方法で定義されます。 したがって、すべての電話番号を取得するには、ドキュメント内のすべてのノードを検索する必要があります。 検索は、ドキュメントのルートから開始され、続いてすべての子孫ノードが検索されます。  
  
     次のクエリは、特定の顧客の連絡先のすべての電話番号を取得します。  
  
    ```  
    SELECT AdditionalContactInfo.query('             
                declare namespace act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";             
                declare namespace crm="https://schemas.adventure-works.com/Contact/Record";             
                declare namespace ci="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";             
                /descendant-or-self::node()/child::act:telephoneNumber             
                ') as result             
    FROM Person.Contact             
    WHERE ContactID=1             
    ```  
  
     パス式を省略構文に置き換えると`//act:telephoneNumber`、同じ結果が得られます。  
  
-   ステップの**self:: node ()** は、1つのドット (.) に省略できます。 ただし、ドットは、**自己:: node ()** と同等ではないか、交換できません。  
  
     たとえば、次のクエリでは、ドットを使用して、ノードではなく値を表しています。  
  
    ```  
    ("abc", "cde")[. > "b"]  
    ```  
  
-   ステップの**parent:: node ()** は、二重のドット (..) に省略できます。  
  
  
