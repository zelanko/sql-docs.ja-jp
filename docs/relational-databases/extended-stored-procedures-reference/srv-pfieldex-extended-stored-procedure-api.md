---
title: srv_pfieldex (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_pfieldex
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_pfieldex
ms.assetid: d4e9a34b-b3a3-434f-8556-768bd20d145a
author: rothja
ms.author: jroth
ms.openlocfilehash: d2294e12af7e22a70ab064a2c3d1163007631eef
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85755914"
---
# <a name="srv_pfieldex-extended-stored-procedure-api"></a>srv_pfieldex (拡張ストアド プロシージャ API)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
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
  
 *分野*  
 返す *srvproc* フィールドを指定します。  
  
|フィールド|説明|戻り値の型|  
|-----------|-----------------|------------------|  
|SRV_MSGLCID|現在のセッションのメッセージ LCID。|ULONG*|  
|SRV_INSTANCENAME|インスタンス名 (指定されている場合)。それ以外の場合は NULL を返します。|WCHAR*|  
  
 *len*  
 返される *field* 値の長さ (バイト単位) を格納した **int** 型変数を指すポインターです。 *len* が NULL の場合、長さは返されていません。 NULL が返されると、**len* は 0 に設定されます。  
  
## <a name="returns"></a>戻り値  
 *field* によってデータ型が決定されるデータを指すポインターです。 *len* または *srvproc* が NULL の場合は NULL が返されます。 *field* が不明の場合は NULL が返されます。 NULL が返されると、**len* は 0 に設定されます。  
  
> [!IMPORTANT]  
>  サーバーから返されるバッファーは読み取り専用にする必要があります。 そうでない場合、サーバーの状態が壊れることがあります。  
  
## <a name="remarks"></a>Remarks  
 **セキュリティに関する注意** 拡張ストアド プロシージャのソース コードを十分に確認し、コンパイルした DLL をテストしたうえで実稼働サーバーにインストールしてください。 セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。  
  
  
