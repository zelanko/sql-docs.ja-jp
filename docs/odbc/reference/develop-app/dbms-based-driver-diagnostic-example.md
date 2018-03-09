---
title: "DBMS に基づいたドライバーの診断例 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DBMS-based driver diagnostic [ODBC]
- diagnostic information [ODBC], examples
- error messages [ODBC], diagnostic messages
ms.assetid: a80d54b0-43ff-4dfd-b6cb-f4694a5ed765
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 84fa35f438b3dc852d2b8b7ae043e5c1f6402ec5
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="dbms-based-driver-diagnostic-example"></a>DBMS に基づいたドライバーの診断例
DBMS に基づいたドライバーでは、DBMS に要求を送信し、アプリケーション、ドライバー マネージャーを使用する情報を返します。 書式化して、引数を返しますが、ドライバーは、インターフェイスと、ドライバー マネージャーで、コンポーネントであるため**SQLGetDiagRec**です。  
  
 たとえば、Oracle Rdb は、無効なカーソル名を検出しましたには、SQL/Services、Microsoft のドライバーを使用して、返されます次の値を**SQLGetDiagRec**:。  
  
```  
SQLSTATE:         "34000"  
Native Error:      0  
Diagnostic Msg:   "[Microsoft][ODBC Rdb Driver]Invalid cursor name: EMPLOYEE_CURSOR."  
```  
  
 ドライバーで、エラーが発生したため、プレフィックスに追加診断メッセージ ([Microsoft]) のベンダーと、ドライバー ([ODBC Rdb ドライバー])。  
  
 ドライバー可能性があります書式を設定しから次の値を返す場合は、DBMS では、従業員テーブルが見つかりませんでした、 **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1  
Diagnostic Msg:   "[Microsoft][ODBC Rdb Driver][Rdb] %SQL-F-RELNOTDEF, Table EMPLOYEE "  
                  "is not defined in schema."  
```  
  
 データ ソースで、エラーが発生したため、ドライバーは、診断メッセージにデータ ソース識別子 ([Rdb]) のプレフィックスを追加します。 ドライバーが、データ ソースと接続するコンポーネントであるために、診断メッセージにその仕入先 ([Microsoft]) と識別子 ([ODBC Rdb Driver]) のプレフィックスが追加されます。
