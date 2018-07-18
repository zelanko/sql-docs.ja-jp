---
title: 拡張ストアド プロシージャのプログラマーズ リファレンス | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
- apinav
helpviewer_keywords:
- extended stored procedures [SQL Server], listed
ms.assetid: 4e9d0374-0927-4f17-bab9-2215b1b8fea8
caps.latest.revision: 38
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 52fc30cedc3e45f970b9f1d9a28da4bede344a77
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37179885"
---
# <a name="extended-stored-procedures-programmer39s-reference"></a>拡張ストアド プロシージャのプログラマ&#39;リファレンス
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]代わりに CLR Integration をご使用ください。  
  
 以前 Open Data Services の一部であった [!INCLUDE[msCoName](../../includes/msconame-md.md)] 拡張ストアド プロシージャ API は、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の機能を拡張するためのサーバー ベースのアプリケーション プログラミング インターフェイスです。 この API は、アプリケーションの構築に使用する C および C++ の関数とマクロで構成されています。  
  
 拡張ストアド プロシージャへのニーズは、現在は CLR 統合などの強力な新しいテクノロジにほとんど移行しています。  
  
> [!IMPORTANT]  
>  拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。 セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/)をご覧ください。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|||  
|-|-|  
|[データ型](srv-pfield-extended-stored-procedure-api.md)|  
|[srv_alloc](srv-alloc-extended-stored-procedure-api.md)||  
|[srv_convert](srv-pfieldex-extended-stored-procedure-api.md)|  
|[srv_describe](srv-rpcdb-extended-stored-procedure-api.md)|  
|[srv_getbindtoken](srv-rpcname-extended-stored-procedure-api.md)|  
|[srv_got_attention](srv-rpcnumber-extended-stored-procedure-api.md)|  
||[srv_rpcoptions](srv-rpcoptions-extended-stored-procedure-api.md)|  
|[srv_message_handler](srv-rpcowner-extended-stored-procedure-api.md)|  
|[srv_paramdata](srv-rpcparams-extended-stored-procedure-api.md)|  
|[srv_paraminfo](srv-senddone-extended-stored-procedure-api.md)|  
|[srv_paramlen](srv-sendmsg-extended-stored-procedure-api.md)|  
|[srv_parammaxlen](srv-sendrow-extended-stored-procedure-api.md)|  
|[srv_paramname](srv-setcoldata-extended-stored-procedure-api.md)|  
|[srv_paramnumber](srv-setcollen-extended-stored-procedure-api.md)|  
|[srv_paramset](srv-setutype-extended-stored-procedure-api.md)|  
|[srv_paramsetoutput](srv-willconvert-extended-stored-procedure-api.md)|  
|[srv_paramstatus](srv-wsendmsg-extended-stored-procedure-api.md)|  
|[srv_paramtype](srv-paramtype-extended-stored-procedure-api.md)||  
  
  
