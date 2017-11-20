---
title: "Update ステートメントと Delete ステートメントに配置されているシミュレート |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- positioned deletes [ODBC]
- data updates [ODBC], positioned update or delete
- row identifiers [ODBC]
- positioned updates [ODBC]
- updating data [ODBC], positioned update or delete
ms.assetid: b24ed59f-f25b-4646-a135-5f3596abc1a4
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 99d022dd56700a3e6441413eb43c06bc1c51cb70
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="simulating-positioned-update-and-delete-statements"></a>位置指定更新ステートメントと Delete ステートメントをシミュレートします。
場合は、データ ソースは位置指定更新はサポートされず、delete ステートメント、ドライバーはこれらをシミュレートできます。 たとえば、ODBC カーソル ライブラリは、位置指定更新をシミュレートし、ステートメントを削除します。 位置指定更新ステートメントと delete ステートメントをシミュレートするための一般的な戦略は、位置指定のステートメントを検索したものに変換するは。 これは、置き換えることで、 **WHERE CURRENT OF** 、検索結果を含む句**場所**現在の行を識別する句。  
  
 たとえば、CustID 列は、Customers テーブルの各行を一意に識別、ため、位置指定削除ステートメント  
  
```  
DELETE FROM Customers WHERE CURRENT OF CustCursor  
```  
  
 変換する可能性があります。  
  
```  
DELETE FROM Customers WHERE (CustID = ?)  
```  
  
 ドライバーは、次のいずれかを使用して可能性があります*行識別子*で、**場所**句。  
  
-   列がテーブルのすべての行に一意に識別する値を持つサービスを提供します。 たとえば、呼び出し**SQLSpecialColumns** SQL_BEST_ROWID で最適な列またはこの目的に使用する列のセットを返します。  
  
-   すべての行を一意に識別するために、一部のデータ ソースによって提供される擬似列です。 これは、場合もありますなりませんこのフィールドは文字列フィールドでで取得可能なければなりませんこのフィールドは、インデックス付けで格納されている各ドキュメントの一意の id を表しますを呼び出して**SQLSpecialColumns**です。  
  
-   一意のインデックス、使用可能な場合です。  
  
-   結果セットのすべての列です。  
  
 のどの列だけで、ドライバーを使用する必要があります、**場所**句を構成します。 は、ドライバーによって異なります。 一部のデータで行識別子を決定する、ソースはコストが高くなることができます。 ただし、高速化は、実行して、シミュレートされたステートメントを更新または最大で 1 行を削除することを保証します。 基になる DBMS の機能によっては、行識別子を使用してコストを設定するがあります。 ただしは高速実行して、シミュレートされたステートメントは更新または 1 行のみを削除することを保証します。 結果セット内のすべての列を使用するオプションは通常の設定をより簡単です。 ただしが実行に時間がかかると、列の行を一意に識別されない、誤って更新または削除される行につながる場合、結果の select リストが設定した場合に特にが含まれていない、基になるテーブルに存在するすべての列には。  
  
 サポートによっては、上記の方法のうち、ドライバー、アプリケーション戦略を必要がある SQL_ATTR_SIMULATE_CURSOR ステートメント属性で使用するドライバーを選択することができます。 アプリケーションのリスクの意図しない更新または行を削除するのには奇数ように見えますが、アプリケーションは、結果セット内の列は、結果セット内の各行を一意に識別できるようにしてこのリスクを削除できます。 これは、ドライバーに、これを行う手間を節約できます。  
  
 途中受信、ドライバーは、行識別子を使用するが場合、 **SELECT FOR UPDATE**結果セットを作成するステートメント。 選択リスト内の列は行を効率的に識別しない場合、ドライバーは、選択リストの末尾に必要な列を追加します。 一部のデータ ソースの Oracle; ROWID 列などの行を常に一意に識別する 1 つの列があります。このような列がある場合、これが、ドライバーに使用します。 それ以外の場合、ドライバーを呼び出す**SQLSpecialColumns**の各テーブルに対して、 **FROM**各行を一意に識別する列の一覧を取得する句。 この方法に起因する一般的な制限はカーソル シミュレーションは失敗で 1 つ以上のテーブルがある場合、 **FROM**句。  
  
 削除、通常のドライバーが行を特定する方法に関係なく、 **FOR UPDATE OF** off 句、 **SELECT FOR UPDATE**データ ソースに送信する前にステートメントです。 **更新の**だけで優位性を update および delete ステートメントに句を使用します。 データ ソースをサポートしていない更新プログラムの配置し、delete ステートメントの通常ではサポートされません。  
  
 アプリケーションでは、位置指定の update または delete ステートメントの実行を送信すると、ドライバーによって置き換えられます、 **WHERE CURRENT OF**句、**場所**行識別子を含む句。 これらの列の値を使用して各列用のドライバーで保持されているキャッシュから取得されます、**場所**句。 ドライバーを表示した後、**場所**句、送信、ステートメント実行のデータ ソースにします。  
  
 たとえば、アプリケーションが結果セットを作成する次のステートメントを送信するとします。  
  
```  
SELECT Name, Address, Phone FROM Customers FOR UPDATE OF Phone, Address  
```  
  
 アプリケーションが要求の一意性を保証する SQL_ATTR_SIMULATE_CURSOR 設定し、データ ソースに行を常に一意に識別する擬似列が提供していない場合、ドライバーを呼び出す場合**SQLSpecialColumns**用、CustID Customers テーブルにキーと、選択リストに追加そのが取り除かが customers テーブルには、検出、 **FOR UPDATE OF**句。  
  
```  
SELECT Name, Address, Phone, CustID FROM Customers  
```  
  
 ドライバーによってのみが除去アプリケーションに一意性を保証が要求されていない場合、 **FOR UPDATE OF**句。  
  
```  
SELECT Name, Address, Phone FROM Customers  
```  
  
 ここで、カーソルの名前、結果セットでは Cust アプリケーションは、結果セットをスクロールし、実行のための次の位置指定の update ステートメントを送信するとします。  
  
```  
UPDATE Customers SET Address = ?, Phone = ? WHERE CURRENT OF Cust  
```  
  
 アプリケーションに一意性を保証が要求されていない場合、ドライバーは置き換えられます、**場所**句し、そのキャッシュ内の変数に CustID パラメーターをバインドします。  
  
```  
UPDATE Customers SET Address = ?, Phone = ? WHERE (CustID = ?)  
```  
  
 アプリケーションに一意性を保証が要求されていない場合、ドライバーは置き換えられます、**場所**句と、キャッシュ内の変数にこの句の名前、アドレス、および電話のパラメーターをバインドします。  
  
```  
UPDATE Customers SET Address = ?, Phone = ?  
   WHERE (Name = ?) AND (Address = ?) AND (Phone = ?)  
```

