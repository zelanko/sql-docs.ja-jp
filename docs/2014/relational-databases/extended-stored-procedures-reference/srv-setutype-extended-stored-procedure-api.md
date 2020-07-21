---
title: srv_setutype (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_setutype
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_setutype
ms.assetid: 6160f15d-1b68-411e-ab6d-491ec288f264
author: rothja
ms.author: jroth
ms.openlocfilehash: 1302f8bcd6a427d5225f6936b0adf158d0ed6ee0
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85050549"
---
# <a name="srv_setutype-extended-stored-procedure-api"></a>srv_setutype (拡張ストアド プロシージャ API)
    
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
  
## <a name="remarks"></a>Remarks  
 列には、実際のデータ型とユーザー定義データ型の 2 つのデータ型があります。 では、このユーザー定義データ型を使用して、列 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の実際のユーザー定義データ型 (存在する場合) と、列の null 値の許容と更新などの列の説明情報を格納します。  
  
 **srv_setutype** 関数は、**srv_describe** で *column* が定義されいれば、最後の行を送信する前のどの時点でも呼び出すことができます。  
  
> [!IMPORTANT]  
>  拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。 セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。  
  
## <a name="see-also"></a>参照  
 [srv_describe &#40;拡張ストアド プロシージャ API&#41;](srv-describe-extended-stored-procedure-api.md)  
  
  
