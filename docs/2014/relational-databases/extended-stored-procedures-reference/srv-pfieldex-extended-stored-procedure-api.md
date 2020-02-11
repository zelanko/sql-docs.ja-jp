---
title: srv_pfieldex (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_pfieldex
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_pfieldex
ms.assetid: d4e9a34b-b3a3-434f-8556-768bd20d145a
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 8bacfd4f955f60b17b439c8066a3b1cba2c52392
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63126950"
---
# <a name="srv_pfieldex-extended-stored-procedure-api"></a>srv_pfieldex (拡張ストアド プロシージャ API)
    
> [!IMPORTANT]  
>  
  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]代わりに CLR Integration をご使用ください。  
  
 要求された SRV_PROC フィールドを格納したデータへのポインターを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
void *srv_pfieldex(SRV_PROC *   
srvproc  
, int   
field  
, int *   
len  
);  
  
```  
  
## <a name="arguments"></a>引数  
 *srvproc*  
 特定のクライアント接続のためのハンドルである SRV_PROC 構造体を指すポインターです。 この構造体には、アプリケーションとクライアントの間の通信やデータを管理するために、拡張ストアド プロシージャ API ライブラリで使用する情報が格納されます。  
  
 *分野*  
 返す *srvproc* フィールドを指定します。  
  
|フィールド|[説明]|戻り値の型|  
|-----------|-----------------|------------------|  
|SRV_MSGLCID|現在のセッションのメッセージ LCID。|ULONG*|  
|SRV_INSTANCENAME|インスタンス名 (指定されている場合)。それ以外の場合は NULL を返します。|WCHAR*|  
  
 *len*  
 返される **field** 値の長さ (バイト単位) を格納した *int* 型変数を指すポインターです。 
  *len* が NULL の場合、長さは返されていません。 NULL が返されると、**len* は 0 に設定されます。  
  
## <a name="returns"></a>戻り値  
 
  *field* によってデータ型が決定されるデータを指すポインターです。 
  *len* または *srvproc* が NULL の場合は NULL が返されます。 
  *field* が不明の場合は NULL が返されます。 NULL が返されると、**len* は 0 に設定されます。  
  
> [!IMPORTANT]  
>  サーバーから返されるバッファーは読み取り専用にする必要があります。 そうでない場合、サーバーの状態が壊れることがあります。  
  
## <a name="remarks"></a>解説  
 **セキュリティ**に関する注意拡張ストアドプロシージャのソースコードを十分に確認し、コンパイル済みの Dll を実稼働サーバーにインストールする前にテストする必要があります。 セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。  
  
  
