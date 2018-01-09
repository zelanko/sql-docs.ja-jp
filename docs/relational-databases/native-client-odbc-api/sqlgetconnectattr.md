---
title: "SQLGetConnectAttr |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-api
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apitype: DLLExport
helpviewer_keywords: SQLGetConnectAttr function
ms.assetid: 26e4e69a-44fd-45e3-b47a-ae39184f041b
caps.latest.revision: "60"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2ec92c6f38bec112705e29cda021ab6e5a7b49d0
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="sqlgetconnectattr"></a>SQLGetConnectAttr
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、ドライバー固有の接続属性が定義されます。 属性の一部が使用する**SQLGetConnectAttr**関数がその現在の設定をレポートするために使用されます。 報告される値はこれらの属性の保証がないまでの接続が行われたかを使用して、属性が設定されて後[SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)です。  
  
 ここでは、読み取り専用の属性を示します。 については、他の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client ODBC ドライバー固有の接続属性を参照してください[SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)です。  
  
## <a name="sqlcoptssconnectiondead"></a>SQL_COPT_SS_CONNECTION_DEAD  
 SQL_COPT_SS_CONNECTION_DEAD 属性では、サーバーへの接続状態が報告されます。 ドライバーは、接続の現在の状態をネットワークにクエリします。  
  
> [!NOTE]  
>  標準の ODBC 接続属性 SQL_ATTR_CONNECTION_DEAD は、接続の最新の状態を返します。 これは現在の接続状態と異なる場合があります。  
  
|値|Description|  
|-----------|-----------------|  
|SQL_CD_TRUE|サーバーへの接続が失われました。|  
|SQL_CD_FALSE|接続が開かれており、ステートメントの処理に使用できます。|  
  
## <a name="sqlcoptssclientconnectionid"></a>SQL_COPT_SS_CLIENT_CONNECTION_ID  
 SQL_COPT_SS_CLIENT_CONNECTION_ID 属性は、クライアント接続 ID を取得します。この ID を使用すると、次の情報を検索できます。  
  
-   XEvent ログの診断情報 (有効な場合)。  
  
-   接続リング バッファーの接続エラー情報。  
  
-   データ アクセスのトレース ログの診断情報 (有効な場合)。  
  
 詳細については、次を参照してください。[へのアクセス ログの診断情報、拡張イベント](../../relational-databases/native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md)です。  
  
|値|Description|  
|-----------|-----------------|  
|SQL_ERROR|接続に失敗しました。|  
|SQL_SUCCESS|接続に成功しました。 クライアント接続 ID は出力バッファーで見つかります。|  
  
## <a name="sqlcoptssperfdata"></a>SQL_COPT_SS_PERF_DATA  
 SQL_COPT_SS_PERF_DATA 属性は、現在のドライバーのパフォーマンス統計情報を保持する SQLPERF 構造体へのポインターを返します。 **SQLGetConnectAttr**パフォーマンスのログ記録が有効でない場合は NULL を返します。 SQLPERF 構造体内の統計情報がドライバーで動的に更新されることはありません。 呼び出す**SQLGetConnectAttr**たびにパフォーマンス統計を更新する必要があります。  
  
|値|Description|  
|-----------|-----------------|  
|NULL|パフォーマンスのログ記録が無効です。|  
|その他の値|SQLPERF 構造体へのポインター。|  
  
## <a name="sqlcoptssperfquery"></a>SQL_COPT_SS_PERF_QUERY  
 SQL_COPT_SS_PERF_QUERY 属性は、実行時間の長いクエリのログ記録が有効の場合に TRUE を返します。 クエリのログ記録が無効の場合は FALSE を返します。  
  
## <a name="sqlcoptssuserdata"></a>SQL_COPT_SS_USER_DATA  
 SQL_COPT_SS_USER_DATA 属性は、ユーザー データ ポインターを取得します。 ユーザー データはクライアントのメモリに格納され、接続ごとに記録されます。 ユーザー データ ポインターが設定されていない場合、SQL_UD_NOTSET という NULL ポインターが返されます。  
  
|値|Description|  
|-----------|-----------------|  
|SQL_UD_NOTSET|ユーザー データ ポインターが設定されていません。|  
|その他の値|ユーザー データへのポインターです。|  
  
## <a name="sqlgetconnectattr-support-for-service-principal-names-spns"></a>SQLGetConnectAttr によるサービス プリンシパル名 (SPN) のサポート  
 SQLGetConnectAttr は、新しい接続属性 SQL_COPT_SS_SERVER_SPN、SQL_COPT_SS_FAILOVER_PARTNER_SPN、SQL_COPT_SS_MUTUALLY_AUTHENTICATED、および SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD の値をクエリに使用できます。 (SQLGetConnectOption こともできますをこれらの値を照会します。)  
  
 SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD は、Windows 認証を使用する、開いている接続でのみ使用できます。  
  
 SQL_COPT_SS_SERVER_SPN または SQL_COPT_SS_FAILOVER_PARTNER が設定されていない場合は、既定値 (空の文字列) が返されます。  
  
 Spn の詳細については、次を参照してください。[サービス プリンシパル名 &#40;です。Spn &#41;でクライアント接続 &#40;ODBC&#41;](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md).  
  
## <a name="see-also"></a>参照  
 [SQLGetConnectAttr 関数](http://go.microsoft.com/fwlink/?LinkId=59347)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)   
 [SET QUOTED_IDENTIFIER と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-quoted-identifier-transact-sql.md)   
 [SET ANSI_NULLS &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-nulls-transact-sql.md)   
 [SET ANSI_PADDING &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-padding-transact-sql.md)   
 [SET ANSI_WARNINGS &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-ansi-warnings-transact-sql.md)  
  
  
