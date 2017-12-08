---
title: "srv_pfieldex (拡張ストアド プロシージャ API) | Microsoft Docs"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: extended-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: srv_pfieldex
apilocation: opends60.dll
apitype: DLLExport
dev_langs: C++
helpviewer_keywords: srv_pfieldex
ms.assetid: d4e9a34b-b3a3-434f-8556-768bd20d145a
caps.latest.revision: "30"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 11e0eeb19711c6070eeca4fdae23607d420289b3
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="srvpfieldex-extended-stored-procedure-api"></a>srv_pfieldex (拡張ストアド プロシージャ API)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]代わりに CLR Integration をご使用ください。  
  
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
  
 *field*  
 返す *srvproc* フィールドを指定します。  
  
|フィールド|Description|戻り値の型|  
|-----------|-----------------|------------------|  
|SRV_MSGLCID|現在のセッションのメッセージ LCID。|ULONG*|  
|SRV_INSTANCENAME|インスタンス名 (指定されている場合)。それ以外の場合は NULL を返します。|WCHAR*|  
  
 *len*  
 返される *field* 値の長さ (バイト単位) を格納した **int** 型変数を指すポインターです。 *len* が NULL の場合、長さは返されていません。 NULL が返されると、**len* は 0 に設定されます。  
  
## <a name="returns"></a>戻り値  
 *field* によってデータ型が決定されるデータを指すポインターです。 *len* または *srvproc* が NULL の場合は NULL が返されます。 *field* が不明の場合は NULL が返されます。 NULL が返されると、**len* は 0 に設定されます。  
  
> [!IMPORTANT]  
>  サーバーから返されるバッファーは読み取り専用にする必要があります。 そうでない場合、サーバーの状態が壊れることがあります。  
  
## <a name="remarks"></a>解説  
 **セキュリティに関する注意** 拡張ストアド プロシージャのソース コードを十分に確認し、コンパイルした DLL をテストしたうえで実稼働サーバーにインストールしてください。 セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/)をご覧ください。  
  
  
