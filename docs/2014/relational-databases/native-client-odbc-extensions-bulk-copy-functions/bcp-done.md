---
title: bcp_done |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 630762fc74a9c1c71d24d40a1ba22bf6627a0d0c
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37414721"
---
# <a name="bcpdone"></a>bcp_done
  プログラム変数から一括コピーを終了[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メンテナンスに伴う[bcp_sendrow](bcp-sendrow.md)します。  
  
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
 呼び出す**bcp_done**を最後に呼び出した後[bcp_sendrow](bcp-sendrow.md)または[bcp_moretext](bcp-moretext.md)します。 呼び出しに失敗する**bcp_done**エラーですべてのデータの結果をコピーした後。  
  
## <a name="see-also"></a>参照  
 [一括コピー関数](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
