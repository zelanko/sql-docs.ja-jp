---
title: "bcp_columns |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-extensions-bulk-copy-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: bcp_columns
apilocation: sqlncli11.dll
apitype: DLLExport
helpviewer_keywords: bcp_columns function
ms.assetid: 5376f6fe-9508-439a-8c66-778d77f19ac3
caps.latest.revision: "31"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4b48c2c0953e3565a406bf2a22788a2e1c537110
ms.sourcegitcommit: 779f3398e4e3f4c626d81ae8cedad153bee69540
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2018
---
# <a name="bcpcolumns"></a>bcp_columns
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] との一括コピー入出力に使用する、ユーザー ファイル内の合計列数を設定します。 [bcp_setbulkmode](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-setbulkmode.md) bcp_columns の代わりに使用できると[bcp_colfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
RETCODE bcp_columns (  
        HDBC hdbc,  
        INT nColumns);  
```  
  
## <a name="arguments"></a>引数  
 *hdbc*  
 一括コピーが有効な ODBC 接続ハンドルです。  
  
 *nColumns*  
 ユーザー ファイル内の合計列数です。 データを一括コピーするユーザー ファイルから準備している場合でも、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブルで、ユーザー ファイル内のすべての列をコピーする予定がないと、設定する必要があります*nColumns*ユーザー ファイルの列の合計数。  
  
## <a name="returns"></a>返します。  
 SUCCEED または FAIL。  
  
## <a name="remarks"></a>解説  
 この関数は、後にのみ呼び出すことができる[bcp_init](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-init.md)有効なファイル名で呼び出されました。  
  
 この関数を呼び出す必要があるのは、既定とは異なる形式のユーザー ファイルを使用する場合のみです。 既定のユーザー ファイル形式の説明の詳細については、次を参照してください。 **bcp_init**です。  
  
 呼び出した後**bcp_columns**、呼び出す必要があります[bcp_colfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md)独自のファイル形式を完全に定義するユーザー ファイル内の各列にします。  
  
## <a name="see-also"></a>参照  
 [一括コピー関数](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
