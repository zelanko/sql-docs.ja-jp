---
title: bcp_readfmt |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- bcp_readfmt
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_readfmt function
ms.assetid: 654001c8-ae9f-425c-b820-f0191bf89367
caps.latest.revision: 34
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3d700f752a3194821065dc21ddd6ab96fa6a8f26
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36175687"
---
# <a name="bcpreadfmt"></a>bcp_readfmt
  指定されたフォーマット ファイルからデータ ファイル形式の定義を読み取ります。  
  
## <a name="syntax"></a>構文  
  
```  
  
RETCODE bcp_readfmt (  
HDBC   
hdbc  
,  
LPCTSTR   
szFormatFile  
);  
  
```  
  
## <a name="arguments"></a>引数  
 *hdbc*  
 一括コピーが有効な ODBC 接続ハンドルです。  
  
 *szFormatFile*  
 データ ファイルの形式の値を含むファイルに関するパスとファイル名です。  
  
## <a name="returns"></a>戻り値  
 SUCCEED または FAIL。  
  
## <a name="remarks"></a>コメント  
 後に`bcp_readfmt`形式の値を読み取り、適切な呼び出しがなさ[bcp_columns](bcp-columns.md)と[bcp_colfmt](bcp-colfmt.md)です。 ユーザーがフォーマット ファイルを解析し、このような呼び出しを行う必要はありません。  
  
 フォーマット ファイルを保持するためには、呼び出す[bcp_writefmt](bcp-writefmt.md)です。 呼び出す`bcp_readfmt`保存形式を参照できます。 詳細については、次を参照してください。 [bcp_init](bcp-init.md)です。  
  
 代わりに、一括コピー ユーティリティ (**bcp**) によって参照されることができるファイルにユーザー定義のデータ形式を保存することができます`bcp_readfmt`です。 詳細については、 **bcp**ユーティリティおよびの構造**bcp**データ フォーマット ファイルを参照してください[データのエクスポートと一括インポート&#40;SQL Server&#41;](../import-export/bulk-import-and-export-of-data-sql-server.md)です。  
  
 `BCPDELAYREADFMT`の値、 *eOption*のパラメーター [bcp_control](bcp-control.md) bcp_readfmt の動作を変更します。  
  
> [!NOTE]  
>  4.2 以降のバージョンによって、フォーマット ファイルが生成される必要がありますが、 **bcp**ユーティリティです。  
  
## <a name="example"></a>例  
  
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
if (bcp_init(hdbc, _T("myTable"), _T("myData.csv"),  
   _T("myErrors"),    DB_IN) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_readfmt(hdbc, _T("myFmtFile.fmt")) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_exec(hdbc, &nRowsProcessed) == SUCCEED)  
   {  
   cout << nRowsProcessed << " rows copied to SQL Server\n";  
   }  
  
// Carry on.  
```  
  
## <a name="see-also"></a>参照  
 [一括コピー関数](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  