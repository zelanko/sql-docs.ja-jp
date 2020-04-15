---
title: DBMS ベースのドライバ診断例 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DBMS-based driver diagnostic [ODBC]
- diagnostic information [ODBC], examples
- error messages [ODBC], diagnostic messages
ms.assetid: a80d54b0-43ff-4dfd-b6cb-f4694a5ed765
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 117f43548d2b57233dea6f7423e6bad67b6233b0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304353"
---
# <a name="dbms-based-driver-diagnostic-example"></a>DBMS ベースのドライバー診断の例
DBMS ベースのドライバーは、DBMS に要求を送信し、ドライバー マネージャーを使用してアプリケーションに情報を返します。 ドライバーはドライバー マネージャーとインターフェイスコンポーネントであるため **、SQLGetDiagRec**の引数を書式設定して返します。  
  
 たとえば、SQL/サービスを使用して、Oracle Rdb のマイクロソフト ドライバが無効なカーソル名を検出した場合 **、SQLGetDiagRec**から次の値を返す可能性があります。  
  
```  
SQLSTATE:         "34000"  
Native Error:      0  
Diagnostic Msg:   "[Microsoft][ODBC Rdb Driver]Invalid cursor name: EMPLOYEE_CURSOR."  
```  
  
 エラーがドライバで発生したため、ベンダー ([Microsoft]) とドライバ ([ODBC Rdb ドライバ]) の診断メッセージにプレフィックスが追加されました。  
  
 DBMS がテーブル EMPLOYEE を見つけることができなかった場合、ドライバーは **、SQLGetDiagRec**から次の値をフォーマットし、返す可能性があります。  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1  
Diagnostic Msg:   "[Microsoft][ODBC Rdb Driver][Rdb] %SQL-F-RELNOTDEF, Table EMPLOYEE "  
                  "is not defined in schema."  
```  
  
 エラーがデータ ソースで発生したため、ドライバーは、データ ソース識別子 ([Rdb]) のプレフィックスを診断メッセージに追加します。 ドライバはデータ ソースとインターフェイスされたコンポーネントであるため、ベンダ ([Microsoft]) と識別子 ([ODBC Rdb Driver]) のプレフィックスが診断メッセージに追加されました。
