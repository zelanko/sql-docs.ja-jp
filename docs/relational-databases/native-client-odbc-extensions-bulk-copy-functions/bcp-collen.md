---
title: bcp_collen |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- bcp_collen
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_collen function
ms.assetid: faaf1f7a-81f2-4852-a178-56602c33673a
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 461b6826600200aa9e3c2d1a7b16b5960837f7bd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47648580"
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
 テーブル内にある、データのコピー先となる列の序数位置です。 最初の列は 1 です。 列の序数位置がによって報告された[SQLColumns](../../relational-databases/native-client-odbc-api/sqlcolumns.md)します。  
  
## <a name="returns"></a>戻り値  
 SUCCEED または FAIL。  
  
## <a name="remarks"></a>コメント  
 **Bcp_collen**関数では、データをコピーするときに、特定の列をプログラム変数内のデータ長を変更できます。[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で[bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)します。  
  
 最初に、データの長さを決定と[bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)が呼び出されます。 呼び出しの間でデータの長さが変更された場合**bcp_sendrow**プレフィックス長もターミネータが使用されていないを呼び出して、 **bcp_collen**長さをリセットします。 次回の呼び出し**bcp_sendrow**への呼び出しで設定される長さを使用して**bcp_collen**します。  
  
 呼び出す必要があります**bcp_collen**がデータの長さを変更するテーブルの各列に対して 1 回です。  
  
## <a name="see-also"></a>参照  
 [一括コピー関数](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
