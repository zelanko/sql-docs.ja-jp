---
title: ゲートウェイ診断の例 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], examples
- gateway diagnostic [ODBC]
- error messages [ODBC], diagnostic messages
ms.assetid: e0695fac-4593-4b3d-8675-cb8f73dab966
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5f4e17074616111ee93ce87c04036d1fc3fd48dd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63062420"
---
# <a name="gateways-diagnostic-example"></a>ゲートウェイ診断の例
ゲートウェイのアーキテクチャでは、ドライバーは ODBC をサポートするゲートウェイに要求を送信します。 ゲートウェイは、DBMS に要求を送信します。 ドライバー マネージャーとのインターフェイスのコンポーネントであるため、ドライバーが書式設定し、の引数を返します**SQLGetDiagRec**します。  
  
 たとえば、Oracle Rdb へのゲートウェイ Microsoft Open Data Services とに基づいて Rdb が EMPLOYEE テーブルを検索しないかどうか、ゲートウェイはこの診断メッセージを生成可能性があります。  
  
```  
"[42S02][-1][DEC][ODS Gateway][Rdb]%SQL-F-RELNOTDEF, Table EMPLOYEE is not defined "  
   "in schema."  
```  
  
 データ ソースで、エラーが発生したため、ゲートウェイは、診断メッセージにデータ ソース識別子 ([Rdb]) のプレフィックスを追加します。 ゲートウェイがデータ ソースと接続するコンポーネントであるために、診断メッセージに、ベンダー ([10 進]) と (の [ODS ゲートウェイ]) の識別子のプレフィックスが追加されます。 また、SQLSTATE 値および Rdb エラー コードが診断メッセージの先頭に追加されます。 これは、独自のメッセージ構造のセマンティクスを保持し、まだドライバーの ODBC 診断情報を指定することを許可します。 ドライバーは、ゲートウェイによって、エラー ステートメントにアタッチされているエラー情報を解析します。  
  
 書式を設定してから次の値を返す前の診断メッセージが使用してゲートウェイ ドライバーは、ドライバー マネージャーとのインターフェイスのコンポーネントであるため**SQLGetDiagRec**:  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1  
Diagnostic Msg:   "[DEC][ODS Gateway][Rdb]%SQL-F-RELNOTDEF, Table EMPLOYEE is not "  
                  "defined in schema."  
```
