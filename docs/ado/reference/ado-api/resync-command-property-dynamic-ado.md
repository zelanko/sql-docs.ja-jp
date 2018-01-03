---
title: "コマンドのプロパティ-動的 (ADO) を再同期 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords: Resync Command property [ADO]
ms.assetid: 4e2bb601-0fe8-4d61-b00e-38341d85a6bb
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2545b52883ef01ae0715c7412fdac9b06a559784
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="resync-command-property-dynamic-ado"></a>コマンドのプロパティ-動的 (ADO) を再同期します。
文字列をユーザーが指定したコマンドを指定します、[再同期](../../../ado/reference/ado-api/resync-method.md)でという名前のテーブル内のデータを更新するメソッドの問題、[一意テーブル](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)動的なプロパティです。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、**文字列**コマンド文字列である値。  
  
## <a name="remarks"></a>解説  
 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトが複数のベース テーブルで実行される結合操作の結果を示します。 影響を受ける行によって異なります、 *AffectRecords*のパラメーター、[再同期](../../../ado/reference/ado-api/resync-method.md)メソッドです。 標準**再同期**メソッドが実行される場合、[一意テーブル](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)と**コマンドを再同期**プロパティが設定されていません。  
  
 コマンド文字列、**コマンドを再同期**プロパティは、パラメーター化コマンドまたは更新される行を一意に識別するストアド プロシージャでありするのには行として、同じ数と列の順序を含む 1 つの行を返します更新されます。 コマンド文字列には各主キー列のパラメーターが含まれています、**一意テーブル**以外の場合、実行時エラーが返されます。 パラメーターには、更新する行の主キーの値が自動的に入力します。  
  
 SQL に基づく 2 つの例を次に示します。  
  
 1\) 、 **Recordset**コマンドによって定義されます。  
  
```  
SELECT * FROM Customers JOIN Orders ON   
   Customers.CustomerID = Orders.CustomerID  
   WHERE city = 'Seattle'  
   ORDER BY CustomerID  
```  
  
 **コマンドを再同期**プロパティに設定します。  
  
```  
"SELECT * FROM   
   (SELECT * FROM Customers JOIN Orders   
   ON Customers.CustomerID = Orders.CustomerID  
   city = 'Seattle' ORDER BY CustomerID)  
WHERE Orders.OrderID = ?"  
```  
  
 **一意テーブル**は*Orders*その主キー、 *OrderID*がパラメーター化します。 サブクエリの select では、プログラムによって、同じ数と列の順序が元のコマンドによって返されることを確認する簡単な方法を提供します。  
  
 2\) 、 **Recordset**ストアド プロシージャによって定義されます。  
  
```  
CREATE PROC Custorders @CustomerID char(5) AS   
SELECT * FROM Customers JOIN Orders ON   
Customers.CustomerID = Orders.CustomerID   
WHERE Customers.CustomerID = @CustomerID  
```  
  
 **再同期**メソッドは、次のストアド プロシージャを実行する必要があります。  
  
```  
CREATE PROC CustordersResync @ordid int AS   
SELECT * FROM Customers JOIN Orders ON   
Customers.CustomerID = Orders.CustomerID  
WHERE Orders.ordid  = @ordid  
```  
  
 **コマンドを再同期**プロパティに設定します。  
  
```  
"{call CustordersResync (?)}"  
```  
  
 もう一度、**一意テーブル**は*Orders*その主キー、 *OrderID*がパラメーター化します。  
  
 **コマンドを再同期**に動的なプロパティが追加、 **Recordset**オブジェクト[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)コレクションと、 [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)プロパティに設定**adUseClient**です。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
