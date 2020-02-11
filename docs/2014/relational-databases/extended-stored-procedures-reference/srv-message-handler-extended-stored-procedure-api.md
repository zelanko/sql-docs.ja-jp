---
title: srv_message_handler (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_message_handler
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_message_handler
ms.assetid: 41bcd057-436f-4fa8-8293-fc8057a30877
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: f597aa6c9ba9759b606501b0bd72a2166b1805e5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63127406"
---
# <a name="srv_message_handler-extended-stored-procedure-api"></a>srv_message_handler (拡張ストアド プロシージャ API)
    
> [!IMPORTANT]  
>  
  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]代わりに CLR Integration をご使用ください。  
  
 インストールされている拡張ストアド プロシージャ API メッセージ ハンドラーを呼び出します。 この関数は、通常、拡張[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ストアドプロシージャからを呼び出して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エラーログファイルまたは[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アプリケーションログにエラー (拡張ストアドプロシージャで定義) を記録するために使用されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
int srv_message_handler (  
SRV_PROC *  
srvproc  
,  
int  
errornum  
,  
BYTE   
severity  
,  
BYTE  
state  
,  
int  
oserrnum  
,  
char *  
errtext  
,  
int  
errtextlen  
,  
char *  
oserrtext  
,  
int  
oserrtextlen  
);  
  
```  
  
## <a name="arguments"></a>引数  
 *srvproc*  
 特定のクライアント接続のためのハンドルである SRV_PROC 構造体を指すポインターです。 
  *srvproc* パラメーターには、アプリケーションとクライアント間の通信やデータを管理するために使用する情報が格納されます。  
  
 *errornum*  
 拡張ストアド プロシージャが定義するエラー番号です。 この値の有効値は 50,001 から 2,147,483,647 です。  
  
 *順*  
 エラーに関する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の重大度を示す標準の値です。 この値の有効値は 0 ～ 24 です。  
  
 *状態*  
 エラーに関する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の状態値です。  
  
 *oserrnum*  
 オペレーティング システムのエラー番号です。 この引数は無視されます。  
  
 *errtext*  
 拡張ストアド プロシージャのエラー *errornum* の説明です。  
  
 *errtextlen*  
 拡張ストアド プロシージャのエラー文字列 *errtext* の長さです。  
  
 *oserrtext*  
 オペレーティング システムのエラー *oserrnum* の説明です。 この引数は無視されます。  
  
 *oserrtextlen*  
 オペレーティング システムのエラー文字列 *oserrtext* の長さです。  
  
## <a name="returns"></a>戻り値  
 SUCCEED または FAIL。  
  
## <a name="remarks"></a>解説  
 
  **srv_message_handler** 関数を使用すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の集中型エラー ログ機能とレポート機能に拡張ストアド プロシージャを統合できるようになります。 拡張ストアド プロシージャからのイベントに対して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の警告を設定し、警告条件を SQL Server エージェントで監視できます。  
  
 エラー メッセージが長い場合は、412 バイトに切り捨てられます。  
  
> [!IMPORTANT]  
>  拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。 セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。  
  
  
