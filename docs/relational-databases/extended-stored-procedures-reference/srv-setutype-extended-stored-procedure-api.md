---
title: srv_setutype (拡張ストアド プロシージャ API) | Microsoft Docs
description: Srv_setutype について説明します。 srv_setutype、行内の列にユーザー定義データ型を設定します。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_setutype
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_setutype
ms.assetid: 6160f15d-1b68-411e-ab6d-491ec288f264
author: rothja
ms.author: jroth
ms.openlocfilehash: 9ecdbaef663059146f3ca6bd4a88305e12d4f495
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/28/2020
ms.locfileid: "87248194"
---
# <a name="srv_setutype-extended-stored-procedure-api"></a>srv_setutype (拡張ストアド プロシージャ API)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]代わりに CLR Integration をご使用ください。  
  
 行内の列について、ユーザー定義データ型を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
int srv_setutype (  
SRV_PROC *  
srvproc  
,  
int   
column  
,   
DBINT  
user_type   
);  
```  
  
## <a name="arguments"></a>引数  
 *srvproc*  
 特定のクライアント接続のためのハンドルである SRV_PROC 構造体を指すポインターです。 この構造体には、アプリケーションとクライアントの間の通信やデータを管理するために、拡張ストアド プロシージャ API ライブラリで使用する情報が格納されます。  
  
 *column*  
 設定する列を示します。 列には 1 から始まる番号が割り当てられます。  
  
 *user_type*  
 ユーザー定義データ型のコードを指定します。  
  
## <a name="returns"></a>戻り値  
 SUCCEED または FAIL。 列が存在しない場合は FAIL を返します。  
  
## <a name="remarks"></a>解説  
 列には、実際のデータ型とユーザー定義データ型の 2 つのデータ型があります。 では、このユーザー定義データ型を使用して、列 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の実際のユーザー定義データ型 (存在する場合) と、列の null 値の許容と更新などの列の説明情報を格納します。  
  
 **srv_setutype** 関数は、**srv_describe** で *column* が定義されいれば、最後の行を送信する前のどの時点でも呼び出すことができます。  
  
> [!IMPORTANT]  
>  拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。 セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://www.microsoft.com/msrc?rtc=1)をご覧ください。  
  
## <a name="see-also"></a>参照  
 [srv_describe &#40;拡張ストアド プロシージャ API&#41;](../../relational-databases/extended-stored-procedures-reference/srv-describe-extended-stored-procedure-api.md)  
  
  
