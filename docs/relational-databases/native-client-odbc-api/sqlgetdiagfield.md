---
title: クエリフィールド |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLGetDiagField function
ms.assetid: 395245ba-0372-43ec-b9a4-a29410d85a6d
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b0d704d76caa3f2a70744a3f2cb4358251f26e55
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299712"
---
# <a name="sqlgetdiagfield"></a>SQLGetDiagField
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  ネイティブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント ODBC ドライバーは **、SQLGetDiagField**の次の追加の診断フィールドを指定します。 これらのフィールドでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アプリケーションに関する各種エラー報告がサポートされます。また、これらのフィールドは、接続されている ODBC 接続ハンドルや ODBC ステートメント ハンドルで生成されるすべての診断レコードで使用できます。 これらのフィールドは、sqlncli.h で定義されています。  
  
|診断レコードのフィールド|説明|  
|------------------------------|-----------------|  
|SQL_DIAG_SS_LINE|ストアド プロシージャのエラーが発生した行番号を報告します。 SQL_DIAG_SS_LINE の値は、SQL_DIAG_SS_PROCNAME に値が返される場合にのみ意味があります。 この値は、16 ビットの符号なし整数で返されます。|  
|SQL_DIAG_SS_MSGSTATE|エラー メッセージの状態。 エラー メッセージの状態については、 [RAISERROR](../../t-sql/language-elements/raiserror-transact-sql.md)を参照してください。 この値は、32 ビットの符号付き整数で返されます。|  
|SQL_DIAG_SS_PROCNAME|エラーが発生したストアド プロシージャの名前 (該当する場合)。 この値は文字列で返されます。 この文字列の長さ (文字数) は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンによって異なります。 この値は、SQL_MAX_PROCEDURE_NAME_LENの値を要求する[SQLGetInfo](../../relational-databases/native-client-odbc-api/sqlgetinfo.md)を呼び出すことによって判別できます。|  
|SQL_DIAG_SS_SEVERITY|関連付けられたエラー メッセージの重大度レベル。 この値は、32 ビットの符号付き整数で返されます。|  
|SQL_DIAG_SS_SRVNAME|エラーが発生したサーバーの名前。 この値は文字列で返されます。 この文字列の長さ (文字列) は、sqlncli.h の SQL_MAX_SQLSERVERNAME マクロで定義されます。|  
  
 文字データを含む [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 固有の診断フィールドの SQL_DIAG_SS_PROCNAME と SQL_DIAG_SS_SRVNAME では、NULL で終わる ANSI 文字列または Unicode 文字列としてデータをクライアントに返します。 必要に応じて、文字数を文字幅で調整する必要があります。 また、TCHAR や SQLTCHAR などの移植可能な C データ型を使用して、プログラム変数の適切な長さを保証できます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、次の補足の動的機能コードが報告されます。この動的機能コードでは、最後に試行された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ステートメントが特定されます。 動的機能コードは、診断レコード セットのヘッダー (レコード 0) に返されるので、各実行が成功しても失敗しても参照できます。  
  
|動的機能コード|source|  
|---------------------------|------------|  
|SQL_DIAG_DFC_SS_ALTER_DATABASE|ALTER DATABASE ステートメント|  
|SQL_DIAG_DFC_SS_CHECKPOINT|CHECKPOINT ステートメント|  
|SQL_DIAG_DFC_SS_CONDITION|ステートメントの WHERE 句または HAVING 句でエラーが発生|  
|SQL_DIAG_DFC_SS_CREATE_DATABASE|CREATE DATABASE ステートメント|  
|SQL_DIAG_DFC_SS_CREATE_DEFAULT|既定のステートメントの作成|  
|SQL_DIAG_DFC_SS_CREATE_PROCEDURE|CREATE PROCEDURE ステートメント|  
|SQL_DIAG_DFC_SS_CREATE_RULE|ルールステートメントの作成|  
|SQL_DIAG_DFC_SS_CREATE_TRIGGER|CREATE TRIGGER ステートメント|  
|SQL_DIAG_DFC_SS_CURSOR_DECLARE|DECLARE CURSOR ステートメント|  
|SQL_DIAG_DFC_SS_CURSOR_OPEN|オープンステートメント|  
|SQL_DIAG_DFC_SS_CURSOR_FETCH|FETCH ステートメント|  
|SQL_DIAG_DFC_SS_CURSOR_CLOSE|CLOSE ステートメント|  
|SQL_DIAG_DFC_SS_DEALLOCATE_CURSOR|割り当て解除ステートメント|  
|SQL_DIAG_DFC_SS_DBCC|DBCC ステートメント|  
|SQL_DIAG_DFC_SS_DENY|DENY ステートメント|  
|SQL_DIAG_DFC_SS_DROP_DATABASE|DROP DATABASE ステートメント|  
|SQL_DIAG_DFC_SS_DROP_DEFAULT|既定のステートメントを削除します。|  
|SQL_DIAG_DFC_SS_DROP_PROCEDURE|プロシージャステートメントを削除します。|  
|SQL_DIAG_DFC_SS_DROP_RULE|ルールステートメントの削除|  
|SQL_DIAG_DFC_SS_DROP_TRIGGER|DROP TRIGGER ステートメント|  
|SQL_DIAG_DFC_SS_DUMP_DATABASE|BACKUP DATABASE ステートメントまたは DUMP DATABASE ステートメント|  
|SQL_DIAG_DFC_SS_DUMP_TABLE|DUMP TABLE ステートメント|  
|SQL_DIAG_DFC_SS_DUMP_TRANSACTION|BACKUP TRANSACTION ステートメントまたは DUMP TRANSACTION ステートメント。 **また、chkpt**にログオンする場合は、CHECKPOINT ステートメントに対しても返されます。 データベース オプションがオンです。|  
|SQL_DIAG_DFC_SS_GOTO|GOTO 流れ制御ステートメント|  
|SQL_DIAG_DFC_SS_INSERT_BULK|INSERT BULK ステートメント|  
|SQL_DIAG_DFC_SS_KILL|キルステートメント|  
|SQL_DIAG_DFC_SS_LOAD_DATABASE|LOAD DATABASE ステートメントまたは RESTORE DATABASE ステートメント|  
|SQL_DIAG_DFC_SS_LOAD_HEADERONLY|LOAD HEADERONLY ステートメントまたは RESTORE HEADERONLY ステートメント|  
|SQL_DIAG_DFC_SS_LOAD_TABLE|LOAD TABLE ステートメント|  
|SQL_DIAG_DFC_SS_LOAD_TRANSACTION|LOAD TRANSACTION ステートメントまたは RESTORE TRANSACTION ステートメント|  
|SQL_DIAG_DFC_SS_PRINT|印刷ステートメント|  
|SQL_DIAG_DFC_SS_RAISERROR|RAISERROR ステートメント|  
|SQL_DIAG_DFC_SS_READTEXT|ステートメントを読み取る|  
|SQL_DIAG_DFC_SS_RECONFIGURE|RECONFIGURE ステートメント|  
|SQL_DIAG_DFC_SS_RETURN|RETURN 流れ制御ステートメント|  
|SQL_DIAG_DFC_SS_SELECT_INTO|SELECT INTO ステートメント|  
|SQL_DIAG_DFC_SS_SET|SET ステートメント (すべての一般的なオプション)|  
|SQL_DIAG_DFC_SS_SET_IDENTITY_INSERT|ステートメントIDENTITY_INSERTセット|  
|SQL_DIAG_DFC_SS_SET_ROW_COUNT|SET ROWCOUNT ステートメント|  
|SQL_DIAG_DFC_SS_SET_STATISTICS|SET STATISTICS IO ステートメントまたは SET STATISTICS TIME ステートメント|  
|SQL_DIAG_DFC_SS_SET_TEXTSIZE|SET TEXTSIZE ステートメント|  
|SQL_DIAG_DFC_SS_SETUSER|SETUSER ステートメント|  
|SQL_DIAG_DFC_SS_SET_XCTLVL|トランザクション分離レベルのステートメントの設定|  
|SQL_DIAG_DFC_SS_SHUTDOWN|シャットダウンステートメント|  
|SQL_DIAG_DFC_SS_TRANS_BEGIN|BEGIN TRAN ステートメント|  
|SQL_DIAG_DFC_SS_TRANS_COMMIT|COMMIT TRAN ステートメント|  
|SQL_DIAG_DFC_SS_TRANS_PREPARE|分散トランザクションをコミットするための準備ステートメント|  
|SQL_DIAG_DFC_SS_TRANS_ROLLBACK|ROLLBACK TRAN ステートメント|  
|SQL_DIAG_DFC_SS_TRANS_SAVE|SAVE TRAN ステートメント|  
|SQL_DIAG_DFC_SS_TRUNCATE_TABLE|テーブル ステートメントの切り捨て|  
|SQL_DIAG_DFC_SS_UPDATE_STATISTICS|UPDATE STATISTICS ステートメント|  
|SQL_DIAG_DFC_SS_UPDATETEXT|ステートメント|  
|SQL_DIAG_DFC_SS_USE|USE ステートメント|  
|SQL_DIAG_DFC_SS_WAITFOR|WAITFOR 流れ制御ステートメント|  
|SQL_DIAG_DFC_SS_WRITETEXT|ステートメントを書き込みます。|  
  
## <a name="sqlgetdiagfield-and-table-valued-parameters"></a>SQLGetDiagField とテーブル値パラメーター  
 SQLGetDiagField は、SQL_DIAG_SS_TABLE_COLUMN_NUMBERとSQL_DIAG_SS_TABLE_ROW_NUMBERの 2 つの診断フィールドを取得するために使用できます。 これらのフィールドは、診断レコードに関連するエラーまたは警告の原因となった値を特定するのに役立ちます。  
  
 テーブル値パラメーターの詳細については、「 [ODBC&#41;&#40;テーブル値パラメーター ](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [関数](https://go.microsoft.com/fwlink/?LinkId=59352)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
