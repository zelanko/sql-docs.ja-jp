---
title: ゲートウェイ診断の例 |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b18fd78be7be2eb79316339cbdf3d315deb194fb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305573"
---
# <a name="gateways-diagnostic-example"></a>ゲートウェイ診断の例
ゲートウェイ アーキテクチャでは、ドライバーは ODBC をサポートするゲートウェイに要求を送信します。 ゲートウェイは、要求を DBMS に送信します。 ドライバー マネージャーとインターフェイスコンポーネントであるため、ドライバーは **、SQLGetDiagRec**の引数を書式設定し、返します。  
  
 たとえば、Oracle が Microsoft オープン データ サービスの Rdb へのゲートウェイに基づいていて、Rdb がテーブル EMPLOYEE を見つけることができなかった場合、ゲートウェイは次の診断メッセージを生成します。  
  
```  
"[42S02][-1][DEC][ODS Gateway][Rdb]%SQL-F-RELNOTDEF, Table EMPLOYEE is not defined "  
   "in schema."  
```  
  
 データ ソースでエラーが発生したため、ゲートウェイはデータ ソース識別子 ([Rdb]) のプレフィックスを診断メッセージに追加しました。 ゲートウェイはデータ ソースとインターフェイスするコンポーネントであるため、ベンダー ([DEC]) と識別子 ([ODS ゲートウェイ]) のプレフィックスを診断メッセージに追加しました。 また、SQLSTATE 値と Rdb エラー・コードも診断メッセージの先頭に追加されました。 これにより、独自のメッセージ構造体のセマンティクスを保持し、ドライバーに ODBC 診断情報を提供することが可能になります。 ドライバーは、ゲートウェイによってエラー ステートメントに添付されたエラー情報を解析します。  
  
 ゲートウェイ ドライバーは、ドライバー マネージャーとインターフェイスコンポーネントであるため、上記の診断メッセージを使用して **、SQLGetDiagRec**から次の値を書式設定して返します。  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1  
Diagnostic Msg:   "[DEC][ODS Gateway][Rdb]%SQL-F-RELNOTDEF, Table EMPLOYEE is not "  
                  "defined in schema."  
```
