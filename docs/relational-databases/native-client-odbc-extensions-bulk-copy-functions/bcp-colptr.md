---
title: bcp_colptr | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-extensions-bulk-copy-functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- bcp_colptr
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_colptr function
ms.assetid: 02ece13e-1da3-4f9d-b860-3177e43d2471
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 48e3469b232033eb3da753e57dfb489f92f19f4d
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2018
---
# <a name="bcpcolptr"></a>bcp_colptr
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への現在のコピー操作に関するプログラム変数のデータ アドレスを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
RETCODE bcp_colptr (  
        HDBC hdbc,  
        LPCBYTE pData,  
        INT idxServerCol);  
```  
  
## <a name="arguments"></a>引数  
 *hdbc*  
 一括コピーが有効な ODBC 接続ハンドルです。  
  
 *pData*  
 コピーするデータを指すポインターです。 バインドされたデータ型は、大きな値型 (SQLTEXT や SQLIMAGE) 場合*pData* NULL にすることができます。 NULL *pData*を使用してチャンクで長い形式のデータ値は SQL Server に送信することを示します[bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md)です。  
  
 場合*pData*は NULL に設定され、列、バインドされるフィールドに対応するが、大きな値型ではない**bcp_colptr**は失敗します。  
  
 大きな値の型の詳細については、次を参照してください。 [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)**です。**  
  
 *idxServerCol*  
 データベース テーブル内にある、データのコピー先となる列の序数位置です。 テーブル内の最初の列は列 1 です。 列の序数位置がによって報告された[SQLColumns](../../relational-databases/native-client-odbc-api/sqlcolumns.md)です。  
  
## <a name="returns"></a>返します。  
 SUCCEED または FAIL。  
  
## <a name="remarks"></a>解説  
 **Bcp_colptr**関数では、データを使用した SQL Server にコピーするときに特定の列のソース データのアドレスを変更できます。 [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)です。  
  
 呼び出しによってユーザー データへのポインターを設定する最初に、 **bcp_bind**です。 呼び出しの間、プログラム変数のデータのアドレスが変更された場合は**bcp_sendrow**、呼び出すことができます**bcp_colptr**データへのポインターをリセットします。 次に呼び出した**bcp_sendrow**への呼び出しによってアドレス指定されるデータを送信**bcp_colptr**です。  
  
 個別である必要があります**bcp_colptr**データのアドレスをテーブルの各列に対して呼び出しが変更します。  
  
## <a name="see-also"></a>参照  
 [一括コピー関数](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
