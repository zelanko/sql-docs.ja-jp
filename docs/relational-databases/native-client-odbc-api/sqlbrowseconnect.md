---
title: SQLBrowseConnect |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLBrowseConnect function
ms.assetid: 57faf388-c7ca-4696-9845-34e0a10cc5f7
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b3980ee8eb0f5f2085f47a1e2ef7f7967e998549
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68115257"
---
# <a name="sqlbrowseconnect"></a>SQLBrowseConnect
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  **SQLBrowseConnect**の接続情報の 3 つのレベルに分類できるキーワードを使用します。 次の表では、キーワードごとに、有効な値の一覧が返されるかどうか、およびそのキーワードが省略可能であるかどうかを示します。  
  
## <a name="level-1"></a>[レベル 1]  
  
|Keyword|一覧が返されるかどうか|省略できるかどうか|説明|  
|-------------|--------------------|---------------|-----------------|  
|DSN|なし|いいえ|によって返されるデータ ソースの名前**SQLDataSources**。 DSN キーワードは、DRIVER キーワードと同時に使用できません。|  
|DRIVER|なし|いいえ|Microsoft®[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアントの ODBC ドライバーの名前は、{[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント 11}。 DRIVER キーワードは、DSN キーワードと同時に使用できません。|  
  
## <a name="level-2"></a>[レベル 2]  
  
|Keyword|一覧が返されるかどうか|省略できるかどうか|説明|  
|-------------|--------------------|---------------|-----------------|  
|SERVER|はい|いいえ|データ ソースがあるネットワーク上のサーバー名。 サーバー名には「(local)」と入力することもできます。これは、ネットワークに接続されていない [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカル コピーも使用できることを意味します。|  
|UID|いいえ|はい|ユーザー ログイン ID。|  
|PWD|いいえ|はい (ユーザーによって異なります)|ユーザーが指定したパスワード。|  
|APP|いいえ|はい|アプリケーションの呼び出し元の名前**SQLBrowseConnect**。|  
|WSID|いいえ|はい|ワークステーション id。 通常は、アプリケーションが実行されているコンピューターのネットワーク名です。|  
  
## <a name="level-3"></a>[レベル 3]  
  
|Keyword|一覧が返されるかどうか|省略できるかどうか|説明|  
|-------------|--------------------|---------------|-----------------|  
|DATABASE|はい|はい|名前、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースです。|  
|LANGUAGE|はい|はい|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で使用される言語。|  
  
 **SQLBrowseConnect** ODBC データ ・ ソースの定義に格納されているデータベースと言語のキーワードの値を無視します。 渡されたデータベースまたは接続文字列で指定された言語場合**SQLBrowseConnect**が有効でない**SQLBrowseConnect** SQL_NEED_DATA とレベル 3 の接続属性を返します。  
  
 呼び出すことによって設定されている次の属性は、 [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)、によって返される結果セットを決定する**SQLBrowseConnect**。  
  
|属性|説明|  
|---------------|-----------------|  
|SQL_COPT_SS_BROWSE_CONNECT|場合は、この属性を SQL_MORE_INFO_YES に設定されている**SQLBrowseConnect**サーバーのプロパティの拡張文字列を返します。<br /><br /> 次の拡張によって返される文字列の例では**SQLBrowseConnect**。<br /><br /> <br /><br /> `ServerName\InstanceName;Clustered:No;Version:8.00.131`<br /><br /> <br /><br /> この文字列では、サーバーに関するさまざまな情報がセミコロンで区切られます。 コンマは、異なるサーバー インスタンスを区切るために使用します。|  
|SQL_COPT_SS_BROWSE_SERVER|サーバー名を指定すると場合、 **SQLBrowseConnect**は指定されたサーバーの情報を返します。 SQL_COPT_SS_BROWSE_SERVER に NULL が設定されている場合**SQLBrowseConnect**ドメイン内のすべてのサーバー情報を返します。<br /><br /> <br /><br /> ネットワークの問題があるため注意してください**SQLBrowseConnect**のすべてのサーバーからタイムリーな応答を受信しない場合があります。 したがって、要求ごとに返されるサーバーの一覧が異なる可能性があります。|  
|SQL_COPT_SS_BROWSE_CACHE_DATA|SQL_COPT_SS_BROWSE_CACHE_DATA 属性が SQL_CACHE_DATA_YES に設定されている場合は、バッファー長の不足が原因で結果を保持できないときにデータをチャンクでフェッチできます。 この長さは、SQLBrowseConnect BufferLength 引数で指定されます。<br /><br /> バッファー長を超えるデータがあるときは SQL_NEED_DATA が返されます。 取得対象のデータがそれ以上ないときは SQL_SUCCESS が返されます。<br /><br /> 既定値は SQL_CACHE_DATA_NO です。|  
  
## <a name="sqlbrowseconnect-support-for-high-availability-disaster-recovery"></a>SQLBrowseConnect の HADR サポート  
 使用の詳細については**SQLBrowseConnect**に接続するのには、[!INCLUDE[ssHADR](../../includes/sshadr-md.md)]クラスターは、「 [SQL Server ネイティブ クライアントのサポート、高可用性、災害復旧の](../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)です。  
  
## <a name="sqlbrowseconnect-support-for-service-principal-names-spns"></a>SQLBrowseConnect によるサービス プリンシパル名 (SPN) のサポート  
 接続が開いている場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client では、SQL_COPT_SS_MUTUALLY_AUTHENTICATED および SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD が、接続を開くときに使用された認証方式に設定されます。  
  
 Spn の詳細については、次を参照してください。[サービス プリンシパル名&#40;Spn&#41;クライアント接続で&#40;ODBC&#41;](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md)します。  
  
## <a name="change-history"></a>変更履歴  
  
|変更内容|  
|---------------------|  
|SQL_COPT_SS_BROWSE_CACHE_DATA に関する記述を追加しました。|  
  
## <a name="see-also"></a>参照  
 [SQLBrowseConnect 関数](https://go.microsoft.com/fwlink/?LinkId=59329)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
