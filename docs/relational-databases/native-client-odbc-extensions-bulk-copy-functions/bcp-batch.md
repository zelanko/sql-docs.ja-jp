---
title: bcp_batch |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- bcp_batch
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_batch function
ms.assetid: 0bda489e-86bc-4a7e-80f6-96047e03f281
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 4f0006229f0e6e0ef2fc5eacf87c1a93bb9be4a5
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37411001"
---
# <a name="bcpbatch"></a>bcp_batch
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  コミットの行すべて以前一括コピー プログラム変数からに送信される[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]によって[bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)します。  
  
## <a name="syntax"></a>構文  
  
```  
  
DBINT bcp_batch (HDBC  
        hdbc);  
```  
  
## <a name="arguments"></a>引数  
 *hdbc*  
 一括コピーが有効な ODBC 接続ハンドルです。  
  
## <a name="returns"></a>戻り値  
 最後の呼び出し後に保存されている行の数**bcp_batch**、またはエラーが発生した場合は-1。  
  
## <a name="remarks"></a>コメント  
 一括コピーのバッチではトランザクションを定義します。 アプリケーションが[bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)と**bcp_sendrow**に行を一括コピー プログラム変数から SQL Server テーブルに、行がコミットされたプログラムを呼び出す場合にのみ**bcp_batch**または[bcp_done](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-done.md)します。  
  
 呼び出すことができます**bcp_batch**したらすべて*n*行 (製品利用統計情報のアプリケーション) のように、受信データ転送がある場合またはします。 アプリケーションが要求されていない場合**bcp_batch**一括コピーされた行がコミットされた場合にのみ**bcp_done**が呼び出されます。  
  
## <a name="see-also"></a>参照  
 [一括コピー関数](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
