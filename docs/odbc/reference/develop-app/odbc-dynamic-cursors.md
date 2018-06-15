---
title: ODBC カーソルが動的 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ODBC], dynamic
- dynamic cursors [ODBC]
ms.assetid: de709fd3-9eb2-44e1-a2f0-786e2b9602a6
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 706bf3a92122e025977d092c06668fc646f2b6e8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32912877"
---
# <a name="odbc-dynamic-cursors"></a>ODBC の動的カーソル
動的カーソルは、その: 動的です。 メンバーシップ、順序、および、カーソルが開かれた後に結果セットの値に加えられた変更を検出できます。 たとえば、動的カーソルが 2 つの行をフェッチし、別のアプリケーションは、これらの行のいずれかを更新し、もう一方を削除します。 動的カーソルは、し、それらの行の再フェッチを試みると、削除された行は見つかりませんが、更新された行の新しい値を返します。  
  
 動的カーソルは、すべての更新を検出を削除、および挿入する場合に、どちらも、自分と他のユーザーによるです。 (これは、分離の対象 SQL_ATTR_TXN_ISOLATION 接続属性によって設定された、トランザクションのレベルです。)SQL_ATTR_ROW_STATUS_PTR ステートメント属性によって指定された行の状態配列では、これらの変更を反映し、SQL_ROW_SUCCESS、SQL_ROW_SUCCESS_WITH_INFO、SQL_ROW_ERROR、SQL_ROW_UPDATED、および SQL_ROW_ADDED に含めることができます。 動的カーソルは、行セット外の削除された行を返さないしたがって結果セットの削除された行または行の状態配列内の対応する要素の存在を認識しないために、SQL_ROW_DELETED に返すことはできません。 呼び出しによって行が更新された場合にのみ、SQL_ROW_ADDED が返される**SQLSetPos**別のカーソルによって更新されたときではなく、します。  
  
 データベースでの動的カーソルの実装方法の 1 つは、メンバーシップを定義する選択的インデックスを作成して、結果の順序によって設定されます。 他のユーザーが変更を加えると、インデックスが更新されるため、このようなインデックスに基づくカーソルは、すべての変更に機密性の高い。 このインデックスが定義されている結果セット内の追加の選択は、インデックスに沿った処理によって可能性があります。  
  
 セットを一意のキーで並べ替える結果を要求することによって、動的カーソルをシミュレートできます。 このような制限は、フェッチが実行することによって行われた、**選択**ステートメントごとに、カーソルに行がフェッチされます。 たとえば、このステートメントによって結果セットが定義されているとします。  
  
```  
SELECT * FROM Customers ORDER BY Name, CustID  
```  
  
 この結果セット内の次の行セットをフェッチするには、シミュレートされたカーソルでは、次のパラメーターを設定**選択**ステートメント、現在の行セットの最後の行の値をそれを実行および。  
  
```  
SELECT * FROM Customers WHERE (Name > ?) AND (CustID > ?)  
   ORDER BY Name, CustID  
```  
  
 このステートメントを作成する最初の行セットは、元の結果セット内の次の行セット、2 つ目の結果セット: この場合は、Customers テーブル内の行のセット。 カーソルは、この行セットをアプリケーションに返します。  
  
 興味深いは、この方法で実装される動的カーソルは、多くの結果セットを実際に作成して、元の結果セットに変更を検出することができます。 アプリケーションはこれら補助次の結果セットの存在を学習します。カーソルが元の結果セットへの変更を検出できない場合は、単が表示されます。
