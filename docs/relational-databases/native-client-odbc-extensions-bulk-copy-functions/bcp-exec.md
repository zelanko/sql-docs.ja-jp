---
title: "bcp_exec |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-extensions-bulk-copy-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: bcp_exec
apilocation: sqlncli11.dll
apitype: DLLExport
helpviewer_keywords: bcp_exec function
ms.assetid: b23ea2cc-8545-4873-b0c1-57e76b0a3a7b
caps.latest.revision: "36"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5255e22b10db37c7cb731f486d6c9f4d5a0b5b79
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="bcpexec"></a>bcp_exec
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  データベース テーブルとユーザー ファイル間でデータの完全な一括コピーを実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
RETCODE bcp_exec (  
        HDBC hdbc,  
        LPDBINT pnRowsProcessed);  
```  
  
## <a name="arguments"></a>引数  
 *hdbc*  
 一括コピーが有効な ODBC 接続ハンドルです。  
  
 *pnRowsProcessed*  
 DBINT へのポインターです。 **Bcp_exec**関数が正常にコピーされた行の数でこの DBINT を塗りつぶします。 場合*pnRowsProcessed* null では無視されます**bcp_exec**です。  
  
## <a name="returns"></a>返します。  
 SUCCEED、SUCCEED_ASYNC、または FAIL のいずれかを返します。 **Bcp_exec**すべての行がコピーされた場合、関数は SUCCEED を返します。 **bcp_exec**非同期の一括コピー操作がまだ保留中の場合は SUCCEED_ASYNC を返します。 **bcp_exec**全体の障害が発生した場合、またはエラーを生成する行の数が使用して BCPMAXERRS に指定された値に達した場合は FAIL を返します[bcp_control](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)です。 BCPMAXERRS の既定値は 10 です。 BCPMAXERRS オプションの影響を受けるのは、データ ファイルの行 (サーバーに送信される行以外) を読み取る間にプロバイダーで検出される構文エラーのみです。 ある行でエラーが検出されると、サーバーはバッチを中止します。 チェック、 *pnRowsProcessed*行の数のパラメーターが正常にコピーします。  
  
## <a name="remarks"></a>解説  
 この関数では、データベース テーブルまたはその逆の場合、ユーザー ファイルからデータをコピーの値に応じて、 *eDirection*パラメーター [bcp_init](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-init.md)です。  
  
 呼び出しの前に**bcp_exec**、呼び出す**bcp_init**有効なユーザー ファイル名を持つ。 この操作を行わないと、エラーが発生します。  
  
 **bcp_exec**されている唯一の一括コピー関数を任意の長さの時間の未処理する可能性があります。 そのため、非同期モードをサポートする唯一の一括コピー関数でもあります。 非同期モードを設定するには、使用[SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)を呼び出す前に SQL_ATTR_ASYNC_ENABLE を SQL_ASYNC_ENABLE_ON に設定する**bcp_exec**です。 完了をテストするには、呼び出す**bcp_exec**同じパラメーターを使用します。 一括コピーがまだ完了していない場合、 **bcp_exec** SUCCEED_ASYNC を返します。 も返します*pnRowsProcessed*がサーバーに送信された行の数の状態カウントします。 サーバーに送信された行は、バッチの終わりに到達するまではコミットされません。  
  
 以降では、一括コピーでの変更については、互換性に影響する[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]を参照してください[一括コピー操作の実行 &#40;ODBC&#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)です。  
  
## <a name="example"></a>例  
 次の例は、使用する方法を示しています**bcp_exec**:。  
  
```  
// Variables like henv not specified.  
HDBC      hdbc;  
DBINT      nRowsProcessed;  
  
// Application initiation, get an ODBC environment handle, allocate the  
// hdbc, and so on.  
...   
  
// Enable bulk copy prior to connecting on allocated hdbc.  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP, (SQLPOINTER) SQL_BCP_ON,  
   SQL_IS_INTEGER);  
  
// Connect to the data source, return on error.  
if (!SQL_SUCCEEDED(SQLConnect(hdbc, _T("myDSN"), SQL_NTS,  
   _T("myUser"), SQL_NTS, _T("myPwd"), SQL_NTS)))  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Initialize bulk copy.   
if (bcp_init(hdbc, _T("pubs..authors"), _T("authors.sav"), NULL, DB_OUT)  
   == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Now, execute the bulk copy.   
if (bcp_exec(hdbc, &nRowsProcessed) == FAIL)  
   {  
   if (nRowsProcessed == -1)  
      {  
      printf_s("No rows processed on bulk copy execution.\n");  
      }  
   else  
      {  
      printf_s("Incomplete bulk copy.   Only %ld row%s copied.\n",  
         nRowsProcessed, (nRowsProcessed == 1) ? "": "s");  
      }  
   return;  
   }  
  
printf_s("%ld rows processed.\n", nRowsProcessed);  
  
// Carry on.  
```  
  
## <a name="see-also"></a>参照  
 [一括コピー関数](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
