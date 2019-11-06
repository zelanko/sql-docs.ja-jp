---
title: bcp_exec |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- bcp_exec
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_exec function
ms.assetid: b23ea2cc-8545-4873-b0c1-57e76b0a3a7b
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 85fc18ed18f157b47d9fd7b654cda4bf25e608ec
ms.sourcegitcommit: 8732161f26a93de3aa1fb13495e8a6a71519c155
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2019
ms.locfileid: "71707687"
---
# <a name="bcp_exec"></a>bcp_exec
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
 DBINT へのポインターです。 **Bcp_exec**関数は、正常にコピーされた行の数をこの DBINT に入力します。 *PnRowsProcessed*が NULL の場合、 **bcp_exec**によって無視されます。  
  
## <a name="returns"></a>戻り値  
 SUCCEED、SUCCEED_ASYNC、または FAIL のいずれかを返します。 すべての行がコピーされると、 **bcp_exec**関数は成功を返します。 非同期の一括コピー操作がまだ未処理の場合、 **bcp_exec**は SUCCEED_ASYNC を返します。 完全なエラーが発生した場合、またはエラーを生成した行の数が[bcp_control](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)を使用して BCPMAXERRS に指定された値に達した場合、 **bcp_exec**は FAIL を返します。 BCPMAXERRS の既定値は 10 です。 BCPMAXERRS オプションの影響を受けるのは、データ ファイルの行 (サーバーに送信される行以外) を読み取る間にプロバイダーで検出される構文エラーのみです。 ある行でエラーが検出されると、サーバーはバッチを中止します。 *PnRowsProcessed*パラメーターで、正常にコピーされた行の数を確認します。  
  
## <a name="remarks"></a>コメント  
 この関数は、 [bcp_init](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-init.md)の*edirection*パラメーターの値に応じて、ユーザーファイルからデータベーステーブルへ、またはその逆のデータをコピーします。  
  
 **Bcp_exec**を呼び出す前に、有効なユーザーファイル名を指定して**bcp_init**を呼び出します。 この操作を行わないと、エラーが発生します。  
  
 **bcp_exec**は、任意の期間に未処理である可能性のある唯一の一括コピー関数です。 そのため、非同期モードをサポートする唯一の一括コピー関数でもあります。 非同期モードを設定するには、 [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)を使用して SQL_ATTR_ASYNC_ENABLE を SQL_ASYNC_ENABLE_ON に設定してから、 **bcp_exec**を呼び出します。 完了をテストするには、同じパラメーターを使用して**bcp_exec**を呼び出します。 一括コピーがまだ完了していない場合、 **bcp_exec**は SUCCEED_ASYNC を返します。 また、 *pnRowsProcessed*は、サーバーに送信された行数の状態カウントを返します。 サーバーに送信された行は、バッチの終わりに到達するまではコミットされません。  
  
 @No__t-0 以降の一括コピーの重大な変更については、「[一括コピー操作&#40;の実行&#41;ODBC](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例は、 **bcp_exec**の使用方法を示しています。  
  
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
  
## <a name="see-also"></a>関連項目  
 [一括コピー関数](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
