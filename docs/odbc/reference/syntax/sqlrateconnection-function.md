---
title: 接続機能 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLRateConnection function [ODBC]
ms.assetid: e8da2ffb-d6ef-4ca7-824f-57afd29585d8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d29033460a7f89fc4a8b1c371a4d32bdf94a2a05
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288882"
---
# <a name="sqlrateconnection-function"></a>SQLRateConnection 関数
**適合 性**  
 バージョン導入: ODBC 3.81 標準準拠: ODBC  
  
 **まとめ**  
 **SQLRateConnection**は、ドライバーが接続プール内の既存の接続を再利用できるかどうかを決定します。  
  
## <a name="syntax"></a>構文  
  
```cpp
  
SQLRETURN  SQLRateConnection(  
                SQLHDBC_INFO_TOKEN   hRequest,  
                SQLHDBC              hCandidateConnection,  
                BOOL                 fRequiredTransactionEnlistment,  
                TRANSID              transId,  
                DWORD *              pRating );  
```  
  
## <a name="arguments"></a>引数  
 *hリクエスト*  
 [入力]新しいアプリケーション接続要求を表すトークン ハンドル。  
  
 *ホレ候補コネクション*  
 [入力]接続プール内の既存の接続。 接続は開かれた状態である必要があります。  
  
 *を要求するトランザクションの参加*  
 [入力]TRUE の場合は、新しい接続要求 (*hRequest*) に既存の接続の*hCandidateConnection*を再利用するには、追加の参加が必要です。  
  
 *トランスID*  
 [入力]*fRequiredTransactionEnlist が*TRUE の場合 *、transId*は要求が参加する DTC トランザクションを表します。 *fRequired トランザクションエンリストが*FALSE の場合、*トランス ID*は無視されます。  
  
 *プレティング*  
 [出力]*hCandidateConnection*の*hRequest*の再使用評価 。 この評価は 0 から 100 (含む) の間になります。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 ドライバー マネージャーは、この関数から返される診断情報を処理しません。  
  
## <a name="remarks"></a>解説  
 **SQLRateConnection は**、既存の接続が要求にどの程度一致しているかを示す 0 から 100 までのスコアを生成します。  
  
|Score|意味 (SQL_SUCCESSが返された場合)|  
|-----------|-----------------------------------------------|  
|0|*hCandidateConnection*を*hRequest*に再利用することはできません。|  
|1 ~ 98 の値 (両端を含む)|スコアが高いほど *、hCandidateConnection*が*hRequest*と一致する近い値になります。|  
|99|重要でない属性には不一致しかありません。  ドライバー マネージャーは、評価ループを停止する必要があります。|  
|100|完璧なマッチ。  ドライバー マネージャーは、評価ループを停止する必要があります。|  
|100 より大きい値|*hCandidateConnection*はデッドとしてマークされ、今後の接続要求でも再利用されません。|  
  
 ドライバー マネージャーは、リターン コードが (SQL_SUCCESS_WITH_INFOを含む) SQL_SUCCESS以外の場合、または評価が 100 を超える場合は、接続をデッドとしてマークします。 その接続が停止しても(将来の接続要求でも)再利用されず、最終的には CPTimeout が通過した後にタイムアウトします。 ドライバー マネージャーは、レートにプールから別の接続を検索し続けます。  
  
 ドライバー マネージャーは、スコアが厳密に 100 未満 (99 を含む) の接続を再利用する場合、ドライバー マネージャーは SQLSetConnectAttr(SQL_ATTR_DBC_INFO_TOKEN) を呼び出して、アプリケーションが要求した状態に接続をリセットします。 ドライバーは、この関数呼び出しで接続をリセットしないでください。  
  
 *fRequiredTransactionEnlist を*TRUE に設定する場合は、*追加*の参加 (transId != NULL) または参加解除 *(transId* == NULL) が必要です。*transId* これは、接続を再利用するコストと、接続を再利用する場合に、ドライバーが接続を参加させるか参加解除するかを示します。 *fRequireTransactionEnlist が*FALSE の場合、ドライバーは*transId*の値を無視する必要があります。  
  
 ドライバー マネージャーは *、hRequest*と*hCandidate 接続*の親 HENV ハンドルが同じであることを保証します。 ドライバー マネージャーは *、hRequest*と*hCandidate 接続*に関連付けられているプール ID が同じであることを保証します。  
  
 アプリケーションはこの関数を直接呼び出さないでください。 ドライバー対応接続プールをサポートする ODBC ドライバーは、この関数を実装する必要があります。  
  
 ODBC ドライバ開発用に sqlspi.h を含めます。  
  
## <a name="see-also"></a>参照  
 [ODBC ドライバーの開発](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [ドライバー対応接続プール](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [ODBC ドライバー対応接続プールの開発](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
