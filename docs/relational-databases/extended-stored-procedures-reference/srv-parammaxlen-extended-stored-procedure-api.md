---
title: srv_parammaxlen (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_parammaxlen
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_parammaxlen
ms.assetid: 49bfc29d-f76a-4963-b0e6-b8532dfda850
author: rothja
ms.author: jroth
ms.openlocfilehash: 8dfa779a664d398a6fb619bf17bf67bb52ab1bb0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68005712"
---
# <a name="srv_parammaxlen-extended-stored-procedure-api"></a>srv_parammaxlen (拡張ストアド プロシージャ API)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]代わりに CLR Integration をご使用ください。  
  
 リモート ストアド プロシージャ呼び出しのパラメーターの最大データ長を返します。 この関数に代わって **srv_paraminfo** 関数が使用されるようになりました。  
  
## <a name="syntax"></a>構文  
  
```  
  
int srv_parammaxlen (  
SRV_PROC *  
srvproc  
,  
int  
n   
);  
```  
  
## <a name="arguments"></a>引数  
 *srvproc*  
 特定のクライアント接続のためのハンドル (この場合は、リモート ストアド プロシージャ呼び出しを受け取るハンドル) である SRV_PROC 構造体を指すポインターです。 この構造体には、アプリケーションとクライアントの間の通信やデータを管理するために、拡張ストアド プロシージャ API ライブラリで使用する情報が格納されます。  
  
 *n*  
 パラメーターの番号を示します。 最初のパラメーターは 1 です。  
  
## <a name="returns"></a>戻り値  
 パラメーター データの最大長をバイト数で返します。 *n* 番目のパラメーターがない場合、またはリモート ストアド プロシージャがない場合は、-1 を返します。  
  
 パラメーターが次[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のいずれかのデータ型である場合、この関数は次の値を返します。  
  
|新しいデータ型|入力データ長|  
|--------------------|-----------------------|  
|**BITN**|**NULL:** 1<br /><br /> **0:** 1<br /><br /> **>= 255:** 該当なし<br /><br /> **<255:** 該当なし|  
|**BIGVARCHAR**|**NULL:** 255<br /><br /> **ZERO:** 255<br /><br /> **>= 255:** 255<br /><br /> **<255:** 255|  
|**BIGCHAR**|**NULL:** 255<br /><br /> **ZERO:** 255<br /><br /> **>= 255:** 255<br /><br /> **<255:** 255|  
|**BIGBINARY**|**NULL:** 255<br /><br /> **ZERO:** 255<br /><br /> **>= 255:** 255<br /><br /> **<255:** 255|  
|**BIGVARBINARY**|**NULL:** 255<br /><br /> **ZERO:** 255<br /><br /> **>= 255:** 255<br /><br /> **<255:** 255|  
|**NCHAR**|**NULL:** 255<br /><br /> **ZERO:** 255<br /><br /> **>= 255:** 255<br /><br /> **<255:** 255|  
|**NVARCHAR**|**NULL:** 255<br /><br /> **ZERO:** 255<br /><br /> **>= 255:** 255<br /><br /> **<255:** 255|  
|**NTEXT**|**NULL:** -1<br /><br /> **ZERO:** -1<br /><br /> **>= 255:** -1<br /><br /> 255:-1 ** \<**|  
  
## <a name="remarks"></a>Remarks  
 リモート ストアド プロシージャ パラメーターのデータ長には、それぞれ実際値および最大値があります。 NULL 値を許容しない標準固定長データ型では、長さの実際値と最大値は等しくなります。 可変長データ型では、この 2 つの値が異なる場合があります。 たとえば、**varchar(30)** として宣言したパラメーターには、長さが 10 バイトしかないデータを格納することが可能です。 このパラメーターは実際の長さが 10 で、最大の長さが 30 です。 **srv_parammaxlen** 関数は、リモート ストアド プロシージャの最大データ長を取得します。 パラメーターの実際のデータ長を取得するには、**srv_paramlen** を使用します。  
  
 パラメーターを指定してリモート ストアド プロシージャを呼び出す場合、パラメーターは名前で指定することも、名前を使用せずにその位置を指定して渡すこともできます。 名前によるパラメーター指定と位置によるパラメーター指定を混合してリモート ストアド プロシージャを呼び出すと、エラーが発生します。 エラーが発生しても SRV_RPC ハンドラーは呼び出されますが、パラメーターが存在しないと見なされ、**srv_rpcparams** は 0 を返します。  
  
> [!IMPORTANT]  
>  拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。 セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。  
  
## <a name="see-also"></a>参照  
 [srv_paraminfo &#40;拡張ストアドプロシージャ API&#41;](../../relational-databases/extended-stored-procedures-reference/srv-paraminfo-extended-stored-procedure-api.md)   
 [srv_rpcparams &#40;拡張ストアド プロシージャ API&#41;](../../relational-databases/extended-stored-procedures-reference/srv-rpcparams-extended-stored-procedure-api.md)  
  
  
