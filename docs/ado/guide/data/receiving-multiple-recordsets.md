---
title: "複数のレコード セットを受け取る |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receiving multiple Recordsets [ADO]
- Recordset object [ADO], receiving multiple Recordsets
ms.assetid: 2a7ad7a6-f00d-4355-b0b5-d0ab957b0566
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ab72906b1f36e22bba58b58ca7917b3399ebc458
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="receiving-multiple-recordsets"></a>複数のレコード セットの受信
[Microsoft OLE DB Provider for SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md)返す複数サポート**レコード セット**オブジェクト、複数の SQL ステートメントを含む 1 つのコマンドを 1 つ**Recordset**SQL ステートメントに 1 です。 順序、 **Recordset**が返されます、コマンド テキストで SQL ステートメントが配置される順序に従います。  
  
 Microsoft OLE DB Provider for SQL Server は、コマンドには、COMPUTE 句が含まれている場合も複数の結果セットと ADO を返します。 たとえば、次の SQL ステートメントを含むコマンドは結果を返す 2 つ**Recordset**オブジェクト: 1 つの行セット (*ProductID*、 *ProductName*、*UnitPrice*)、およびその他のテーブルのすべての製品の平均価格。  
  
```  
SELECT ProductID, ProductName, UnitPrice   
  FROM PRODUCTS   
  COMPUTE AVG(UnitPrice)  
```  
  
 使用することができます、 **Recordset.NextRecordset** 2 つのオブジェクトを列挙するメソッド。  
  
 詳細については、次を参照してください。 [NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)です。

