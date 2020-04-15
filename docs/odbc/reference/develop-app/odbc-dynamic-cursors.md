---
title: ODBC 動的カーソル |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- cursors [ODBC], dynamic
- dynamic cursors [ODBC]
ms.assetid: de709fd3-9eb2-44e1-a2f0-786e2b9602a6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f94b83ef1458cd9f8368d1bea3a39682bd80b1a2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302324"
---
# <a name="odbc-dynamic-cursors"></a>ODBC 動的カーソル
動的カーソルは、動的なカーソルだけです。 カーソルを開いた後に結果セットのメンバーシップ、順序、および値に加えられた変更を検出できます。 たとえば、動的カーソルで 2 つの行がフェッチされた後、別のアプリケーションによって一方の行は更新され、他の行は削除されたものとします。 動的カーソルがそれらの行を再フェッチしようとすると、削除された行は見つかりませんが、更新された行の新しい値を返します。  
  
 動的カーソルは、それ自身と他の人が行った更新、削除、および挿入をすべて検出します。 (これは、SQL_ATTR_TXN_ISOLATION接続属性で設定されたトランザクションの分離レベルに従います。SQL_ATTR_ROW_STATUS_PTR ステートメント属性で指定された行の状態配列は、これらの変更を反映し、SQL_ROW_SUCCESS、SQL_ROW_SUCCESS_WITH_INFO、SQL_ROW_ERROR、SQL_ROW_UPDATED、およびSQL_ROW_ADDEDを含めることができます。 動的カーソルは行セットの外部で削除された行を返さないため、削除された行が結果セット内に存在するか、または行の状態配列内に対応する要素が存在することを認識しないため、SQL_ROW_DELETEDを返すことはできません。 SQL_ROW_ADDEDは、別のカーソルによって更新された場合ではなく **、SQLSetPos**の呼び出しによって行が更新された場合にのみ返されます。  
  
 データベースに動的カーソルを実装する方法の 1 つは、結果セットのメンバーシップと順序を定義する選択的インデックスを作成することです。 他のユーザーが変更を加えたときにインデックスが更新されるため、そのようなインデックスに基づくカーソルはすべての変更に影響を受けます。 このインデックスで定義された結果セット内で、インデックスに沿った処理によって、追加の選択が可能です。  
  
 動的カーソルは、結果セットを一意のキーで並べ替えることを要求することによってシミュレートできます。 このような制限では、カーソルが行をフェッチするたびに**SELECT**ステートメントを実行することによってフェッチが行われます。 たとえば、結果セットが次のステートメントで定義されているとします。  
  
```  
SELECT * FROM Customers ORDER BY Name, CustID  
```  
  
 この結果セットの次の行セットをフェッチするには、シミュレートされたカーソルは、次の**SELECT**ステートメントのパラメータを現在の行セットの最後の行の値に設定し、それを実行します。  
  
```  
SELECT * FROM Customers WHERE (Name > ?) AND (CustID > ?)  
   ORDER BY Name, CustID  
```  
  
 このステートメントは、元の結果セットの次の行セットである最初の行セットである 2 番目の結果セットを作成します。 カーソルは、この行セットをアプリケーションに返します。  
  
 この方法で実装された動的カーソルは、実際には多くの結果セットを作成し、元の結果セットに対する変更を検出できることに注意してください。 アプリケーションは、これらの補助結果セットの存在を決して知らない。カーソルが元の結果セットに対する変更を検出できるかのように見えます。
