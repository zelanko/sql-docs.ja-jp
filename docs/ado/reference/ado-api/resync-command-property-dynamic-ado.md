---
title: 再同期コマンドプロパティ-動的 (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Resync Command property [ADO]
ms.assetid: 4e2bb601-0fe8-4d61-b00e-38341d85a6bb
author: rothja
ms.author: jroth
ms.openlocfilehash: 916afef294a76e62702dbbd7cc413a0540484f62
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82756478"
---
# <a name="resync-command-property-dynamic-ado"></a>Resync Command プロパティ - 動的 (ADO)
[一意のテーブル](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)動的プロパティに指定されたテーブル内のデータを更新するために再[同期](../../../ado/reference/ado-api/resync-method.md)メソッドによって発行される、ユーザーが指定したコマンド文字列を指定します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 コマンド文字列である**文字列**値を設定または返します。  
  
## <a name="remarks"></a>解説  
 [レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトは、複数のベーステーブルに対して実行される結合操作の結果です。 影響を受ける行は、 [Resync](../../../ado/reference/ado-api/resync-method.md)メソッドの反映された*レコード*のパラメーターによって異なります。 [一意のテーブル](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)と再**同期コマンド**のプロパティが設定されていない場合は、標準の再**同期**メソッドが実行されます。  
  
 再**同期コマンド**プロパティのコマンド文字列は、更新対象の行を一意に識別するパラメーター化されたコマンドまたはストアドプロシージャで、更新する行と同じ数と順序の列を含む単一の行を返します。 コマンド文字列には、**一意テーブル**の主キー列ごとのパラメーターが含まれています。それ以外の場合は、実行時エラーが返されます。 パラメーターは、更新する行の主キーの値で自動的に入力されます。  
  
 SQL に基づく2つの例を次に示します。  
  
 1 \) **レコードセット**はコマンドによって定義されます。  
  
```  
SELECT * FROM Customers JOIN Orders ON   
   Customers.CustomerID = Orders.CustomerID  
   WHERE city = 'Seattle'  
   ORDER BY CustomerID  
```  
  
 再**同期コマンド**のプロパティは次のように設定されています。  
  
```  
"SELECT * FROM   
   (SELECT * FROM Customers JOIN Orders   
   ON Customers.CustomerID = Orders.CustomerID  
   city = 'Seattle' ORDER BY CustomerID)  
WHERE Orders.OrderID = ?"  
```  
  
 **一意のテーブル**は*Orders*で、その主キーである*OrderID*がパラメーター化されます。 サブ選択を使用すると、元のコマンドと同じ数および順序の列が返されるようにプログラムで簡単に確認できます。  
  
 2 \) **レコードセット**は、ストアドプロシージャによって定義されます。  
  
```  
CREATE PROC Custorders @CustomerID char(5) AS   
SELECT * FROM Customers JOIN Orders ON   
Customers.CustomerID = Orders.CustomerID   
WHERE Customers.CustomerID = @CustomerID  
```  
  
 再**同期**メソッドでは、次のストアドプロシージャを実行する必要があります。  
  
```  
CREATE PROC CustordersResync @ordid int AS   
SELECT * FROM Customers JOIN Orders ON   
Customers.CustomerID = Orders.CustomerID  
WHERE Orders.ordid  = @ordid  
```  
  
 再**同期コマンド**のプロパティは次のように設定されています。  
  
```  
"{call CustordersResync (?)}"  
```  
  
 この場合も、**一意のテーブル**は*Orders*で、その主キー *OrderID*がパラメーター化されます。  
  
 再**同期コマンド**は、[カーソル位置](../../../ado/reference/ado-api/cursorlocation-property-ado.md)プロパティが**adUseClient**に設定されている場合に、**レコードセット**オブジェクトの[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)コレクションに追加される動的プロパティです。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
