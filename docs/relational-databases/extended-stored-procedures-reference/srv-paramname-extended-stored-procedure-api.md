---
title: srv_paramname (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: extended-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- srv_paramname
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_paramname
ms.assetid: 1a53d707-7b06-49cc-a0df-ac727cfe953f
caps.latest.revision: 30
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 50af5fe7e6c40a1133ee585b416189e61ed461e2
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="srvparamname-extended-stored-procedure-api"></a>srv_paramname (拡張ストアド プロシージャ API)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]代わりに CLR Integration をご使用ください。  
  
 リモート ストアド プロシージャ呼び出しのパラメーターの名前を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
DBCHAR * srv_paramname (  
SRV_PROC * srvproc,intn, int *len );  
```  
  
## <a name="arguments"></a>引数  
 *srvproc*  
 特定のクライアント接続のためのハンドル (この場合は、リモート ストアド プロシージャ呼び出しを受け取るハンドル) である SRV_PROC 構造体を指すポインターです。 この構造体には、アプリケーションとクライアントの間の通信やデータを管理するために、拡張ストアド プロシージャ API ライブラリで使用する情報が格納されます。  
  
 *n*  
 パラメーターの番号を示します。 最初のパラメーターは 1 です。  
  
 *len*  
 パラメーター名の長さ (バイト数) を格納した **int** 変数へのポインターです。 *len* が NULL である場合、リモート ストアド プロシージャのパラメーター名の長さは返されていません。  
  
## <a name="returns"></a>返します。  
 パラメーター名を格納した NULL 終端文字列を指すポインターを返します。 パラメーター名の長さは、*len* に格納されます。 ある場合ありません*n*番目のパラメーターまたはリモート ストアド プロシージャなしは、NULL を返します*len*を-1 に設定されている、情報エラー メッセージを送信します。 パラメーター名が NULL である場合、*len* は 0 に設定され、NULL 終端の空文字列が返されます。  
  
## <a name="remarks"></a>解説  
 この関数は、リモート ストアド プロシージャ呼び出しのパラメーターの名前を取得します。 パラメーターを指定してリモート ストアド プロシージャを呼び出す場合、パラメーターは名前で指定することも、名前を使用せずにその位置を指定して渡すこともできます。 名前によるパラメーター指定と位置によるパラメーター指定を混合してリモート ストアド プロシージャを呼び出すと、エラーが発生します。 エラーが発生しても SRV_RPC ハンドラーは呼び出されますが、パラメーターが存在しないと見なされ、**srv_rpcparams** は 0 を返します。  
  
> [!IMPORTANT]  
>  拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。 セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/)をご覧ください。  
  
## <a name="see-also"></a>参照  
 [srv_rpcparams &#40;拡張ストアド プロシージャ API&#41;](../../relational-databases/extended-stored-procedures-reference/srv-rpcparams-extended-stored-procedure-api.md)  
  
  
