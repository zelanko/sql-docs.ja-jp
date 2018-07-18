---
title: 軸の指定 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b97dc99b7de5d8829f88faad6a6df282e9cecd5e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37234782"
---
# <a name="specifying-an-axis-sqlxml-40"></a>軸の指定 (SQLXML 4.0)
    
-   軸によって、ロケーション ステップで選択されるノードと、コンテキスト ノードの間のツリー リレーションシップが指定されます。 `child` 軸がサポートされます。  
  
     コンテキスト ノードの子を含みます。  
  
     すべての現在のコンテキスト ノードから次の XPath 式 (ロケーション パス) を選択、 **\<顧客 >** 子。  
  
    ```  
    child::Customer  
    ```  
  
     この XPath クエリでは、`child` は軸で、 `Customer` はノード テストです。  
  
-   `parent`  
  
     コンテキスト ノードの親を含みます。  
  
     次の XPath 式は、すべてを選択、 **\<顧客 >** の親、 **\<順序 >** 子。  
  
    ```  
    child::Customer/child::Order[parent::Customer/@customerID="ALFKI"]  
    ```  
  
     これは、`child::Customer` を指定した場合と同じです。 この XPath クエリでは、`child` と `parent` は軸で、 `Customer` と `Order` はノード テストです。  
  
-   `attribute`  
  
     コンテキスト ノードの属性を含みます。  
  
     次の XPath 式を選択、 **CustomerID**コンテキスト ノードの属性。  
  
    ```  
    attribute::CustomerID  
    ```  
  
-   `self`  
  
     コンテキスト ノードそのものを含みます。  
  
     いる場合、次の XPath 式は、現在のノードを選択、 **\<順序 >** ノード。  
  
    ```  
    self::Order  
    ```  
  
     この XPath クエリでは、`self` は軸で、`Order` はノード テストです。  
  
  
