---
title: 軸の指定 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 651b7899e104fe5a7dbc6d584ceba6e5cf8de570
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85055115"
---
# <a name="specifying-an-axis-sqlxml-40"></a>軸の指定 (SQLXML 4.0)
    
-   軸によって、ロケーション ステップで選択されるノードと、コンテキスト ノードの間のツリー リレーションシップが指定されます。 `child` 軸がサポートされます。  
  
     コンテキスト ノードの子を含みます。  
  
     次の XPath 式 (ロケーションパス) では、現在のコンテキストノードからすべての子が選択され **\<Customer>** ます。  
  
    ```  
    child::Customer  
    ```  
  
     この XPath クエリでは、`child` は軸で、 `Customer` はノード テストです。  
  
-   `parent`  
  
     コンテキスト ノードの親を含みます。  
  
     次の XPath 式は、子のすべての親を選択し **\<Customer>** **\<Order>** ます。  
  
    ```  
    child::Customer/child::Order[parent::Customer/@customerID="ALFKI"]  
    ```  
  
     これは、`child::Customer` を指定した場合と同じです。 この XPath クエリでは、`child` と `parent` は軸で、 `Customer` と `Order` はノード テストです。  
  
-   `attribute`  
  
     コンテキスト ノードの属性を含みます。  
  
     次の XPath 式では、コンテキストノードの**CustomerID**属性が選択されます。  
  
    ```  
    attribute::CustomerID  
    ```  
  
-   `self`  
  
     コンテキスト ノードそのものを含みます。  
  
     次の XPath 式は、ノードの場合、現在のノードを選択し **\<Order>** ます。  
  
    ```  
    self::Order  
    ```  
  
     この XPath クエリでは、`self` は軸で、`Order` はノード テストです。  
  
  
