---
title: bcp_batch |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_batch
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_batch function
ms.assetid: 0bda489e-86bc-4a7e-80f6-96047e03f281
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c41e8d90adc8ff6eb2058feebe3f33c10edbfa92
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62631386"
---
# <a name="bcp_batch"></a>bcp_batch
  プログラム変数から一括コピーされ、 [bcp_sendrow](bcp-sendrow.md)によって[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に送信されたすべての行をコミットします。  
  
## <a name="syntax"></a>構文  
  
```  
  
DBINT bcp_batch (HDBC  
hdbc  
);  
  
```  
  
## <a name="arguments"></a>引数  
 *hdbc*  
 一括コピーが有効な ODBC 接続ハンドルです。  
  
## <a name="returns"></a>戻り値  
 **Bcp_batch**を最後に呼び出した後に保存された行の数。エラーが発生した場合は-1。  
  
## <a name="remarks"></a>解説  
 一括コピーのバッチではトランザクションを定義します。 アプリケーションで[bcp_bind](bcp-bind.md)を使用し、プログラム変数から SQL Server テーブルに行を一括コピーする**bcp_sendrow** 、プログラムが**bcp_batch**または[bcp_done](bcp-done.md)を呼び出した場合にのみ、行がコミットされます。  
  
 **Bcp_batch**は、 *n*行ごとに、または (テレメトリアプリケーションと同様に) 受信データになどがあるときに1回呼び出すことができます。 アプリケーションがを呼び出さない場合**bcp_batch** **bcp_done**が呼び出されたときにのみ、一括コピーされた行がコミットされます。  
  
## <a name="see-also"></a>参照  
 [一括コピー関数](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
