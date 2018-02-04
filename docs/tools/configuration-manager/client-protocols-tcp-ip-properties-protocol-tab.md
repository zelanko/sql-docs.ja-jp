---
title: "クライアント プロトコル - TCP/IP のプロパティ (プロトコル タブ) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: configuration-manager
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TCP/IP [SQL Server], client protocols
- client protocols [SQL Server]
ms.assetid: d04f1bce-069c-4a02-b561-c87c3282be36
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1fa2175534441ab464452a1f549833742daaa185
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="client-protocols---tcp-ip-properties-protocol-tab"></a>クライアント プロトコル - [TCP/IP のプロパティ] ダイアログ ボックス ([プロトコル] タブ)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーでは、 **[TCP/IP のプロパティ]** ダイアログ ボックスの **[プロトコル]** タブを使用して、以下のオプションの表示や指定を行います。 別のポートに接続するには、 **[既定のポート]** ボックスにポート番号を入力します。 接続文字列の詳細については、「 [TCP/IP を使用した有効な接続文字列の作成](../../tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **[既定のポート]**  
 TCP/IP Net-Library が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の対象インスタンスに接続するために使用するポートを指定します。 既定値のポートは 1433 です。  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]の既定のインスタンスに接続する場合、クライアントはこの値を使用します。 既定のインスタンスが別のポートでリッスンするように構成されている場合は、この値をそのポート番号に変更してください。  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]の名前付きインスタンスに接続する場合、クライアントはサーバー コンピューターで実行されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスからポート番号の取得を試みます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスが実行されていない場合、ポート番号がこの設定か、接続文字列の一部として指定されている必要があります。  
  
 **有効**  
 可能な値は、 **[はい]** と **[いいえ]**です。  
  
 **[Keep Alive]**  
 このパラメーターは、 **KEEPALIVE** パケットを送信することによって、アイドル状態の接続が壊れていないかどうかを TCP が確認する頻度をミリ秒単位で設定します。 既定値は 30,000 ミリ秒です。  
  
 **[Keep Alive 間隔]**  
 このパラメーターは、応答を受信するまで **KEEPALIVE** パケットを再送信する間隔をミリ秒単位で設定します。 既定値は 1,000 ミリ秒です。  
  
## <a name="see-also"></a>参照  
 [ネットワーク プロトコルの選択](http://msdn.microsoft.com/library/6565fb7d-b076-4447-be90-e10d0dec359a)   
 [新しいエイリアス &#40;です。[別名] タブ &#41;](../../tools/configuration-manager/new-alias-alias-tab.md)   
 [[&#60;Alias&#62; のプロパティ] ダイアログ ボックス &#40;[別名] タブ&#41;](../../tools/configuration-manager/alias-properties-alias-tab.md)  
  
  
