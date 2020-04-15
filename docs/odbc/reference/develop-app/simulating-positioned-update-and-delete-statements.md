---
title: 位置指定更新および削除ステートメントのシミュレーション |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- positioned deletes [ODBC]
- data updates [ODBC], positioned update or delete
- row identifiers [ODBC]
- positioned updates [ODBC]
- updating data [ODBC], positioned update or delete
ms.assetid: b24ed59f-f25b-4646-a135-5f3596abc1a4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e1eb498a99180d145147e67c8955eeb7a0027024
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301993"
---
# <a name="simulating-positioned-update-and-delete-statements"></a>位置指定の UPDATE および DELETE ステートメントのシミュレート
データ ソースが位置指定更新および削除ステートメントをサポートしていない場合、ドライバーはこれらをシミュレートできます。 たとえば、ODBC カーソル ライブラリは位置指定更新および削除ステートメントをシミュレートします。 位置指定更新ステートメントおよび delete ステートメントをシミュレートする一般的な方法は、位置指定ステートメントを検索済みステートメントに変換することです。 これは **、WHERE CURRENT OF**句を、現在の行を識別する検索**WHERE**句に置き換えることによって行われます。  
  
 たとえば、CustID 列は Customers テーブルの各行を一意に識別するため、位置指定削除ステートメント  
  
```  
DELETE FROM Customers WHERE CURRENT OF CustCursor  
```  
  
 に変換される可能性があります  
  
```  
DELETE FROM Customers WHERE (CustID = ?)  
```  
  
 ドライバーは **、WHERE**句で次の*行の識別子*のいずれかを使用できます。  
  
-   テーブル内のすべての行を一意に識別する値を持つ列。 たとえば、SQL_BEST_ROWIDを指定**して SQLSpecialColumns を**呼び出すと、この目的に適した列または列のセットが返されます。  
  
-   すべての行を一意に識別するために、一部のデータ ソースによって提供される疑似列。 これらは **、SQLSpecialColumns**を呼び出すことによっても取得可能な場合があります。  
  
-   一意のインデックス (使用可能な場合)。  
  
-   結果セット内のすべての列。  
  
 ドライバーが構築する**WHERE**句で使用する必要がある列は、ドライバーによって異なります。 データ ソースによっては、行 ID の決定にコストがかかる場合があります。 ただし、実行速度が速く、シミュレートされたステートメントが 1 行で更新または削除されることを保証します。 基になる DBMS の機能によっては、行識別子を使用すると、設定にコストがかかる場合があります。 ただし、実行速度が速く、シミュレートされたステートメントが 1 行だけ更新または削除されることを保証します。 通常、結果セット内のすべての列を使用するオプションは、設定が非常に簡単です。 ただし、実行速度が遅くなり、列が行を一意に識別しない場合、特に結果セットの選択リストに基になるテーブルに存在するすべての列が含まれていない場合に、行が意図せずに更新または削除される可能性があります。  
  
 ドライバーがサポートする上記の戦略に応じて、アプリケーションは、SQL_ATTR_SIMULATE_CURSOR ステートメント属性でドライバーを使用する戦略を選択できます。 アプリケーションが意図せずに行を更新または削除する危険があるように見えますが、結果セット内の列が結果セット内の各行を一意に識別するようにすることで、アプリケーションはこのリスクを取り除くことができます。 これにより、ドライバーはこれを行う必要がある労力を節約できます。  
  
 ドライバーは、行の識別子を使用することを選択した場合、結果セットを作成する**SELECT FOR UPDATE**ステートメントをインターセプトします。 選択リストの列が行を効果的に識別しない場合、ドライバーは、必要な列を選択リストの最後に追加します。 データ ソースによっては、Oracle の ROWID 列など、常に行を一意に識別する単一列があります。このような列が使用可能な場合、ドライバーはこれを使用します。 それ以外の場合、ドライバーは**FROM**句の各テーブルの**SQLSpecialColumns**を呼び出して、各行を一意に識別する列の一覧を取得します。 この手法の結果として生じる一般的な制限事項は **、FROM**句に複数のテーブルがある場合にカーソル シミュレーションが失敗することです。  
  
 ドライバーが行を識別する方法に関係なく、通常はデータ ソースに送信する前に **、SELECT FOR UPDATE**ステートメントから FOR UPDATE**の句**を削除します。 **FOR UPDATE OF**句は、位置指定更新ステートメントおよび削除ステートメントでのみ使用されます。 位置指定更新および削除ステートメントをサポートしないデータ ソースは、通常、このステートメントをサポートしません。  
  
 アプリケーションが実行のために位置指定更新または削除ステートメントを送信すると、ドライバーは WHERE **CURRENT OF**句を行識別子を含む**WHERE**句に置き換えます。 これらの列の値は **、WHERE**句で使用する各列のドライバーによって保持されるキャッシュから取得されます。 ドライバーは**WHERE**句を置き換えた後、実行のためにステートメントをデータ ソースに送信します。  
  
 たとえば、アプリケーションが結果セットを作成するために次のステートメントを送信するとします。  
  
```  
SELECT Name, Address, Phone FROM Customers FOR UPDATE OF Phone, Address  
```  
  
 アプリケーションが一意性の保証を要求するSQL_ATTR_SIMULATE_CURSORを設定しており、データ ソースが常に行を一意に識別する疑似列を提供しない場合、ドライバーは Customers テーブルの**SQLSpecialColumns**を呼び出し、CustID が Customers テーブルのキーであることを検出して、これを選択リストに追加し **、FOR UPDATE OF**句を削除します。  
  
```  
SELECT Name, Address, Phone, CustID FROM Customers  
```  
  
 アプリケーションが一意性の保証を要求していない場合、ドライバーは**FOR UPDATE OF**句のみを削除します。  
  
```  
SELECT Name, Address, Phone FROM Customers  
```  
  
 アプリケーションが結果セットをスクロールし、次の位置指定更新ステートメントを実行用に実行依頼するとします。  
  
```  
UPDATE Customers SET Address = ?, Phone = ? WHERE CURRENT OF Cust  
```  
  
 アプリケーションが一意性の保証を要求していない場合、ドライバーは**WHERE**句を置き換え、CustID パラメーターをキャッシュ内の変数にバインドします。  
  
```  
UPDATE Customers SET Address = ?, Phone = ? WHERE (CustID = ?)  
```  
  
 アプリケーションが一意性の保証を要求していない場合、ドライバーは**WHERE**句を置き換え、この句の Name、Address、および Phone の各パラメータをキャッシュ内の変数にバインドします。  
  
```  
UPDATE Customers SET Address = ?, Phone = ?  
   WHERE (Name = ?) AND (Address = ?) AND (Phone = ?)  
```
