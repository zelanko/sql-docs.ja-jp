---
title: bcp_readfmt |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 8ea8094778c8ccb204712536f01b13152c89c7a1
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82701904"
---
# <a name="bcp_readfmt"></a>bcp_readfmt
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
  
## <a name="remarks"></a>解説  
 は、 `bcp_readfmt` 書式設定値を読み取った後、 [bcp_columns](bcp-columns.md)と[bcp_colfmt](bcp-colfmt.md)に対する適切な呼び出しを行います。 ユーザーがフォーマット ファイルを解析し、このような呼び出しを行う必要はありません。  
  
 フォーマットファイルを永続化するには、 [bcp_writefmt](bcp-writefmt.md)を呼び出します。 の呼び出しで `bcp_readfmt` は、保存された形式を参照できます。 詳細については、「 [bcp_init](bcp-init.md)」を参照してください。  
  
 また、一括コピーユーティリティ (**bcp**) では、で参照できるファイルにユーザー定義データ形式を保存することもでき `bcp_readfmt` ます。 **Bcp**ユーティリティと**bcp**データフォーマットファイルの構造の詳細については、「[データ &#40;SQL Server&#41;の一括インポートと一括エクスポート](../import-export/bulk-import-and-export-of-data-sql-server.md)」を参照してください。  
  
 `BCPDELAYREADFMT` [Bcp_control](bcp-control.md)の*eOption*パラメーターの値によって、bcp_readfmt の動作が変更されます。  
  
> [!NOTE]  
>  フォーマットファイルは、 **bcp**ユーティリティのバージョン4.2 以降で作成されている必要があります。  
  
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
  
  
