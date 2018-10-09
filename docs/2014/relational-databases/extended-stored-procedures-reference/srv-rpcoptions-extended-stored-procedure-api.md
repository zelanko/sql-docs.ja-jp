---
title: srv_rpcoptions (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- srv_rpcoptions
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcoptions
ms.assetid: dbcce5d1-d5a1-4379-9597-04e43af5923d
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 5087c29feb94f22395573614ea10beb09ba344b0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48073842"
---
# <a name="srvrpcoptions-extended-stored-procedure-api"></a>srv_rpcoptions (拡張ストアド プロシージャ API)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]代わりに CLR Integration をご使用ください。  
  
 現在のリモート ストアド プロシージャの実行時オプションを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
DBUSMALLINT srv_rpcoptions ( SRV_PROC *  
srvproc   
);  
  
```  
  
## <a name="arguments"></a>引数  
 *srvproc*  
 特定のクライアント接続のためのハンドル (この場合は、リモート ストアド プロシージャを受け取るハンドル) である SRV_PROC 構造体を指すポインターです。 この構造体には、アプリケーションとクライアントの間の通信やデータを管理するために、拡張ストアド プロシージャ API ライブラリで使用する情報が格納されます。  
  
## <a name="returns"></a>戻り値  
 現在のリモート ストアド プロシージャの実行時フラグを論理 OR で結合して格納したビットマップを返します。 リモート ストアド プロシージャがない場合は、0 を返し、メッセージを生成します。  
  
## <a name="remarks"></a>コメント  
 次の表では、各実行時フラグについて説明します。  
  
|実行時フラグ|説明|  
|--------------------|-----------------|  
|SRV_NOMETADATA|クライアントがメタデータ情報なしの結果を要求したことを示します。 このフラグが使用されるのは、クライアントと [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが通信中である場合だけです。 拡張ストアド プロシージャ API アプリケーションではメタデータ情報を省略できません。|  
|SRV_RECOMPILE|クライアントがリモート ストアド プロシージャの実行前に再コンパイルを要求していることを示します。 このフラグは、拡張ストアド プロシージャ API アプリケーションには適用できません。|  
  
> [!IMPORTANT]  
>  拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。 セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/)をご覧ください。  
  
  
