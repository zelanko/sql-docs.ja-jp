---
title: "ゲートウェイ診断例 |Microsoft ドキュメント"
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
- diagnostic information [ODBC], examples
- gateway diagnostic [ODBC]
- error messages [ODBC], diagnostic messages
ms.assetid: e0695fac-4593-4b3d-8675-cb8f73dab966
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b14ef1e84b36a0f371f503706fca805c156f2e9d
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="gateways-diagnostic-example"></a>ゲートウェイ診断例
ゲートウェイのアーキテクチャでは、ドライバーは ODBC をサポートするゲートウェイに要求を送信します。 ゲートウェイは、DBMS に要求を送信します。 インターフェイスと、ドライバー マネージャーをコンポーネントになっているため、ドライバーは書式化しての引数を返します**SQLGetDiagRec**です。  
  
 たとえば、Oracle ゲートウェイ Rdb を Microsoft のオープン データ サービスとに基づいて Rdb から従業員テーブルが見つかりませんだったかどうか、ゲートウェイはこの診断メッセージを生成可能性があります。  
  
```  
"[42S02][-1][DEC][ODS Gateway][Rdb]%SQL-F-RELNOTDEF, Table EMPLOYEE is not defined "  
   "in schema."  
```  
  
 データ ソースで、エラーが発生したため、ゲートウェイは、診断メッセージにデータ ソース識別子 ([Rdb]) のプレフィックスを追加します。 ゲートウェイがデータ ソースと接続するコンポーネントであるために、診断メッセージにその仕入先 ([10 進]) と識別子 (の [ODS ゲートウェイ]) のプレフィックスが追加されます。 また、SQLSTATE 値および Rdb エラー コードが診断メッセージの先頭に追加されます。 これは、独自のメッセージ構造のセマンティクスを保持してもドライバーの ODBC 診断情報を指定することを許可します。 ドライバーでは、ゲートウェイによって、エラー ステートメントにアタッチされたエラー情報を解析します。  
  
 書式を設定してから、次の値を返す前に診断メッセージを使用するゲートウェイ ドライバーはドライバー マネージャーとのインターフェイスと、コンポーネントであるため、 **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1  
Diagnostic Msg:   "[DEC][ODS Gateway][Rdb]%SQL-F-RELNOTDEF, Table EMPLOYEE is not "  
                  "defined in schema."  
```
