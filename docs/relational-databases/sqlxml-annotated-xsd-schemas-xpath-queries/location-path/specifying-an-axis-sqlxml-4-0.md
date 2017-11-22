---
title: "軸 (SQLXML 4.0) を指定する |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], axes
- XPath queries [SQLXML], location paths
- self axis
- attribute axis [SQLXML]
- axis [SQLXML]
- child axis
- parent axis
- location path for XPath query
- axes [SQLXML]
ms.assetid: 65631795-3389-40cf-90ea-85e9438956c5
caps.latest.revision: "22"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 40deac488a6a5d793689668e3acc5f0971bb3a61
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="specifying-an-axis-sqlxml-40"></a>軸の指定 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
    
-   軸によって、ロケーション ステップで選択されるノードと、コンテキスト ノードの間のツリー リレーションシップが指定されます。 次の軸がサポートされます:**子**  
  
     コンテキスト ノードの子を含みます。  
  
     すべての現在のコンテキスト ノードから次の XPath 式 (ロケーション パス) を選択、 **\<顧客 >**子。  
  
    ```  
    child::Customer  
    ```  
  
     この XPath クエリでは、`child` は軸で、 `Customer` はノード テストです。  
  
-   **親**  
  
     コンテキスト ノードの親を含みます。  
  
     次の XPath 式は、すべてを選択、 **\<顧客 >**の親、 **\<順序 >**子。  
  
    ```  
    child::Customer/child::Order[parent::Customer/@customerID="ALFKI"]  
    ```  
  
     これは、`child::Customer` を指定した場合と同じです。 この XPath クエリでは、`child` と `parent` は軸で、 `Customer` と `Order` はノード テストです。  
  
-   **属性**  
  
     コンテキスト ノードの属性を含みます。  
  
     次の XPath 式を選択、 **CustomerID**コンテキスト ノードの属性。  
  
    ```  
    attribute::CustomerID  
    ```  
  
-   **self**  
  
     コンテキスト ノードそのものを含みます。  
  
     いる場合、次の XPath 式は、現在のノードを選択、 **\<順序 >**ノード。  
  
    ```  
    self::Order  
    ```  
  
     この XPath クエリでは、`self` は軸で、`Order` はノード テストです。  
  
  
