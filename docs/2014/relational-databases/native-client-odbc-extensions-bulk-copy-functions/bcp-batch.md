---
title: bcp_batch |Microsoft ドキュメント
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
- bcp_batch
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_batch function
ms.assetid: 0bda489e-86bc-4a7e-80f6-96047e03f281
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e01952fbe3fcba497544b9defd94044bdf06bf09
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36083913"
---
# <a name="bcpbatch"></a>bcp_batch
  すべての行以前一括がプログラム変数からコピーされに送信されたがコミット[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]によって[bcp_sendrow](bcp-sendrow.md)です。  
  
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
 一括コピーのバッチではトランザクションを定義します。 アプリケーションを使用する場合[bcp_bind](bcp-bind.md)と**bcp_sendrow**行を一括コピー プログラム変数から SQL Server テーブルに、行はコミットされた場合にのみ、プログラムを呼び出す**bcp_batch**または[bcp_done](bcp-done.md)です。  
  
 呼び出すことができます**bcp_batch**したらすべて*n*行 (アプリケーションと同様、製品利用統計情報) の受信データの転送が中断がある場合またはします。 アプリケーションが要求されていない場合**bcp_batch**一括コピーされた行がコミットされる場合にのみ**bcp_done**と呼びます。  
  
## <a name="see-also"></a>参照  
 [一括コピー関数](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  