---
title: bcp_batch |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
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
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ee208e08edd8c68e204f8ac531758850366e8687
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37407501"
---
# <a name="bcpbatch"></a>bcp_batch
  コミットの行すべて以前一括コピー プログラム変数からに送信される[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]によって[bcp_sendrow](bcp-sendrow.md)します。  
  
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
 最後の呼び出し後に保存されている行の数**bcp_batch**、またはエラーが発生した場合は-1。  
  
## <a name="remarks"></a>コメント  
 一括コピーのバッチではトランザクションを定義します。 アプリケーションが[bcp_bind](bcp-bind.md)と**bcp_sendrow**に行を一括コピー プログラム変数から SQL Server テーブルに、行がコミットされたプログラムを呼び出す場合にのみ**bcp_batch**または[bcp_done](bcp-done.md)します。  
  
 呼び出すことができます**bcp_batch**したらすべて*n*行 (製品利用統計情報のアプリケーション) のように、受信データ転送がある場合またはします。 アプリケーションが要求されていない場合**bcp_batch**一括コピーされた行がコミットされた場合にのみ**bcp_done**が呼び出されます。  
  
## <a name="see-also"></a>参照  
 [一括コピー関数](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
