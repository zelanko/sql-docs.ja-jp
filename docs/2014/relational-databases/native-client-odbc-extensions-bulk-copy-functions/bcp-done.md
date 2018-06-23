---
title: bcp_done |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- bcp_done
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_done function
ms.assetid: e59b3f16-5b59-40da-880f-f3edf657d1ee
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 56c1d20d56d95263e93e33a45f712447b749b1be
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36179106"
---
# <a name="bcpdone"></a>bcp_done
  プログラム変数から一括コピーを終了[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で実行される[bcp_sendrow](bcp-sendrow.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
DBINT bcp_done (  
    HDBC   
hdbc  
);  
  
```  
  
## <a name="arguments"></a>引数  
 *hdbc*  
 一括コピーが有効な ODBC 接続ハンドルです。  
  
## <a name="returns"></a>戻り値  
 最後の呼び出し後に完全に保存されている行の数[bcp_batch](bcp-batch.md)またはエラーが発生した場合は-1。  
  
## <a name="remarks"></a>コメント  
 呼び出す**bcp_done**を最後に呼び出した後[bcp_sendrow](bcp-sendrow.md)または[bcp_moretext](bcp-moretext.md)です。 呼び出しに失敗する**bcp_done**エラーのすべての結果のデータをコピーした後です。  
  
## <a name="see-also"></a>参照  
 [一括コピー関数](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  