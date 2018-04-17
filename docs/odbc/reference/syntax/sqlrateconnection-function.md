---
title: SQLRateConnection 関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQLRateConnection function [ODBC]
ms.assetid: e8da2ffb-d6ef-4ca7-824f-57afd29585d8
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 60a1cb0044b4368f0e985b5f258c01e07f21fd78
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sqlrateconnection-function"></a>SQLRateConnection 関数
**準拠**  
 のバージョンで導入されました ODBC 3.81 規格に準拠: ODBC。  
  
 **概要**  
 **SQLRateConnection**ドライバーが接続プール内で既存の接続を再利用できるかどうかを決定します。  
  
## <a name="syntax"></a>構文  
  
```  
SQLRETURN  SQLRateConnection(  
                SQLHDBC_INFO_TOKEN   hRequest,  
                SQLHDBC              hCandidateConnection,  
                BOOL                 fRequiredTransactionEnlistment,  
                TRANSID              transId,  
                DWORD *              pRating );  
```  
  
## <a name="arguments"></a>引数  
 *hRequest*  
 [入力]新しいアプリケーション接続要求を表すトークンのハンドル。  
  
 *hCandidateConnection*  
 [入力]接続プール内で既存の接続。 接続が開いた状態でなければなりません。  
  
 *fRequiredTransactionEnlistment*  
 [入力]TRUE の場合、既存の接続を再利用*hCandidateConnection*新しい接続要求の (*hRequest*) その他の参加が必要です。  
  
 *transId*  
 [入力]場合*fRequiredTransactionEnlistment* true *transId*要求は参加 DTC トランザクションを表します。 場合*fRequiredTransactionEnlistment* false で、 *transId*は無視されます。  
  
 *pRating*  
 [出力]*hCandidateConnection*のレーティングの再利用、 *hRequest*です。 この評価は、0 と 100 (包括) の間になります。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_ERROR、または SQL_INVALID_HANDLE します。  
  
## <a name="diagnostics"></a>診断  
 ドライバー マネージャーは、この関数から返される診断情報を処理しません。  
  
## <a name="remarks"></a>解説  
 **SQLRateConnection** 0 と 100 (包括) の既存の接続が要求に一致する度合いを示すスコアを生成します。  
  
|[スコア]|(ときに関係なく SQL_SUCCESS が返されます) の意味|  
|-----------|-----------------------------------------------|  
|0|*hCandidateConnection*の再利用する必要がありますされません、 *hRequest*です。|  
|1 ~ 98 (包括) の任意の値|スコアが高い、近くする*hCandidateConnection*と一致*hRequest*です。|  
|99|意味のない属性には、のみの不一致があります。  ドライバー マネージャーは、評価ループを停止する必要があります。|  
|100|完全に一致します。  ドライバー マネージャーは、評価ループを停止する必要があります。|  
|その他の値が 100 より大きい|*hCandidateConnection*は配信不能とそれが再利用できません以降の接続要求であってもとしてマークします。|  
  
 リターン コードは、(SQL_SUCCESS_WITH_INFO を含む) が SQL_SUCCESS 以外または規制レベルが 100 より大きい場合、ドライバー マネージャーは配信不能として接続をマークします。 配信不能の接続 (以降の接続要求) であっても再利用できませんが最終的にタイムアウトする CPTimeout 経過するとします。 ドライバー マネージャーは、レートをプールから別の接続を見つける続行されます。  
  
 ドライバー マネージャーは、点数が 100 (99 を含む) より厳密に小さい接続を再利用、ドライバー マネージャーは、アプリケーションによって要求された状態に戻す接続をリセットする SQLSetConnectAttr(SQL_ATTR_DBC_INFO_TOKEN) を呼び出します。 ドライバーでは、この関数の呼び出しで接続をリセットする必要がありますされません。  
  
 場合*fRequiredTransactionEnlistment*場合は TRUE、再利用が*hCandidateConnection*余分な参加リストを必要があります (*transId* ! = NULL) または参加解除 (*transId* NULL = =)。 これは、接続と、ドライバーの参加/接続を再利用する場合、接続の参加を解除する必要があるかどうかを再利用のコストを示します。 場合*fRequireTransactionEnlistment* false で、ドライバーの値は無視する必要があります*transId*です。  
  
 ドライバー マネージャーは、保証のハンドルを HENV 親*hRequest*と*hCandidateConnection*は同じです。 ドライバー マネージャーがプール ID に関連付けられていることを保証*hRequest*と*hCandidateConnection*は同じです。  
  
 アプリケーションでは、この関数を直接呼び出さないでください。 ドライバー対応接続プールをサポートする ODBC ドライバーでは、この関数を実装する必要があります。  
  
 ODBC ドライバーの開発の sqlspi.h が含まれます。  
  
## <a name="see-also"></a>参照  
 [ODBC ドライバーの開発](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [ドライバー対応接続プール](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [ODBC ドライバー対応接続プールの開発](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
