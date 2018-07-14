---
title: srv_wsendmsg (拡張ストアド プロシージャ API) | Microsoft Docs
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
- srv_wsendmsg
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_wsendmsg
ms.assetid: f2153076-32c9-4a52-8e1b-fc9618153543
caps.latest.revision: 32
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 5ed9efee806d432019be9c8d606c84004f80e97d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37260818"
---
# <a name="srvwsendmsg-extended-stored-procedure-api"></a>srv_wsendmsg (拡張ストアド プロシージャ API)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]代わりに CLR Integration をご使用ください。  
  
 クライアントに Unicode メッセージを送信します。  
  
## <a name="syntax"></a>構文  
  
```  
  
int srv_wsendmsg(SRV_PROC *   
srvproc  
, int   
msgnum  
, int   
severity  
, WCHAR *   
message  
, int   
msglen  
);  
  
```  
  
## <a name="arguments"></a>引数  
 *srvproc*  
 特定のクライアント接続のためのハンドルである SRV_PROC 構造体を指すポインターです。 この構造体には、アプリケーションとクライアントの間の通信やデータを管理するために、拡張ストアド プロシージャ API ライブラリで使用する情報が格納されます。  
  
 *Msgnum*  
 4 バイトのメッセージ番号です。  
  
 *Severity*  
 エラーの重大度を指定します。 重大度が 10 以下の場合は情報メッセージと見なされ、10 より大きい場合はエラー メッセージと見なされます。  
  
 *message*  
 クライアントに送信される Unicode 文字列を指すポインターです。  
  
 *msglen*  
 *message* の長さを文字数で指定します。  
  
## <a name="returns"></a>戻り値  
 SUCCEED または FAIL。  
  
## <a name="remarks"></a>コメント  
 この関数は、Unicode でメッセージを送信するために使用します。 この関数は **srv_sendmsg** と似ていますが、送信されるメッセージは DBCHAR 型ではなく WCHAR 型の文字列です。 メッセージの長さはバイト数ではなく文字数で報告され、*msglen* が SRV_NULLTERM とは等しくならないことに注意してください。  
  
 次の場合、この関数は FAIL を返します。  
  
-   *msglen* が 0 から 32242 の範囲内にない場合。  
  
-   *msglen* が 0 で、メッセージ ポインターが NULL の場合。  
  
-   ネットワーク経由でエラー メッセージを送信するときにエラーが発生した場合。  
  
> [!IMPORTANT]  
>  拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。 セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/)をご覧ください。  
  
## <a name="see-also"></a>参照  
 [srv_sendmsg &#40;拡張ストアド プロシージャ API&#41;](srv-sendmsg-extended-stored-procedure-api.md)  
  
  
