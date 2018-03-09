---
title: "bcp_collen |Microsoft ドキュメント"
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
apiname: bcp_collen
apilocation: sqlncli11.dll
apitype: DLLExport
helpviewer_keywords: bcp_collen function
ms.assetid: faaf1f7a-81f2-4852-a178-56602c33673a
caps.latest.revision: "30"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1528b71e05a77034235606f43c9dc455521d79b1
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2018
---
# <a name="bcpcollen"></a>bcp_collen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に対する現在の一括コピー用のプログラム変数にデータ長を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
RETCODE bcp_collen (  
        HDBC hdbc,  
        DBINT cbData,  
        INT idxServerCol);  
```  
  
## <a name="arguments"></a>引数  
 *hdbc*  
 一括コピーが有効な ODBC 接続ハンドルです。  
  
 *cbData*  
 プログラム変数内のデータ長です。長さのインジケーターやターミネータの長さは含まれません。 設定*cbData* SQL_NULL_DATA するには、サーバーにコピーされるすべての行が列の NULL 値を含むを示します。 また、SQL_VARLEN_DATA に設定すると、文字列ターミネータや他の方法を使用してコピーするデータ長が決定されます。 長さのインジケーターとターミネータの両方を指定した場合、システムはコピーするデータ量が少なくなる方法を使用します。  
  
 *idxServerCol*  
 テーブル内にある、データのコピー先となる列の序数位置です。 最初の列は 1 です。 列の序数位置がによって報告された[SQLColumns](../../relational-databases/native-client-odbc-api/sqlcolumns.md)です。  
  
## <a name="returns"></a>返します。  
 SUCCEED または FAIL。  
  
## <a name="remarks"></a>解説  
 **Bcp_collen**関数では、データをコピーするときに、特定の列をプログラム変数内のデータ長を変更できます。[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で[bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)です。  
  
 最初に、データの長さを決定とき[bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)と呼びます。 呼び出しの間でデータの長さが変更された場合は**bcp_sendrow**プレフィックス長もターミネータが使用されていないと、呼び出すことができます**bcp_collen**長さをリセットします。 次に呼び出した**bcp_sendrow**への呼び出しで設定される長さを使用して**bcp_collen**です。  
  
 呼び出す必要があります**bcp_collen**のデータの長さを変更するテーブルの各列に対して 1 回です。  
  
## <a name="see-also"></a>参照  
 [一括コピー関数](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
