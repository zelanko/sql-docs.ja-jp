---
title: "srv_rpcname (拡張ストアド プロシージャ API) | Microsoft Docs"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: extended-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: srv_rpcname
apilocation: opends60.dll
apitype: DLLExport
dev_langs: C++
helpviewer_keywords: srv_rpcname
ms.assetid: 0a1424e4-3319-4836-b8d8-5e0344cc683f
caps.latest.revision: "29"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fb0640702667d73882f70dfe95f6dddb1658fdc9
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="srvrpcname-extended-stored-procedure-api"></a>srv_rpcname (拡張ストアド プロシージャ API)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]代わりに CLR Integration をご使用ください。  
  
 現在のリモート ストアド プロシージャのプロシージャ名部分を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
DBCHAR * srv_rpcname (  
SRV_PROC *  
srvproc  
,  
int *  
len   
);  
```  
  
## <a name="arguments"></a>引数  
 *srvproc*  
 特定のクライアント接続のためのハンドル (この場合は、リモート ストアド プロシージャを受け取るハンドル) である SRV_PROC 構造体を指すポインターです。 この構造体には、アプリケーションとクライアントの間の通信やデータを管理するために、拡張ストアド プロシージャ API ライブラリで使用する情報が格納されます。  
  
 *len*  
 データベース名の長さを受け取る整数変数を指すポインターです。 *len* が NULL である場合、リモート ストアド プロシージャ名の長さは返されていません。  
  
## <a name="returns"></a>戻り値  
 現在のリモート ストアド プロシージャのリモート ストアド プロシージャ名部分に対応した NULL 終端文字列を指す DBCHAR ポインターを返します。 現在のリモート ストアド プロシージャがない場合は、NULL が返され、*len* が -1 に設定されます。  
  
## <a name="remarks"></a>解説  
 この関数は、リモート ストアド プロシージャの名前のみを返します。 所有者、データベース名、およびリモート ストアド プロシージャ番号に対応する省略可能な指定子は含まれません。  
  
 リモート ストアド プロシージャがなくても **srv_rpcname** を呼び出すことは有効であるため (情報エラーは発生しない)、この関数にはリモート ストアド プロシージャが存在するかどうかを判断する手段が用意されています。  
  
> [!IMPORTANT]  
>  拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。 セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/)をご覧ください。  
  
  
