---
title: クライアント プロトコル - TCP と IP のプロパティ (プロトコル タブ) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- configmgr-client
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- TCP/IP [SQL Server], client protocols
- client protocols [SQL Server]
ms.assetid: d04f1bce-069c-4a02-b561-c87c3282be36
caps.latest.revision: 24
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 2495b6c504083189313acf15e2bf8ecd0567aca2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36173837"
---
# <a name="client-protocols---tcp-and-ip-properties-protocol-tab"></a>クライアント プロトコル - TCP と IP のプロパティ (プロトコル タブ)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーでは、 **[TCP/IP のプロパティ]** ダイアログ ボックスの **[プロトコル]** タブを使用して、以下のオプションの表示や指定を行います。 別のポートに接続するには、 **[既定のポート]** ボックスにポート番号を入力します。 接続文字列の詳細については、「 [TCP/IP を使用した有効な接続文字列の作成](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)」を参照してください。  
  
## <a name="options"></a>および  
 **[既定のポート]**  
 TCP/IP Net-Library が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の対象インスタンスに接続するために使用するポートを指定します。 既定値のポートは 1433 です。  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]の既定のインスタンスに接続する場合、クライアントはこの値を使用します。 既定のインスタンスが別のポートでリッスンするように構成されている場合は、この値をそのポート番号に変更してください。  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]の名前付きインスタンスに接続する場合、クライアントはサーバー コンピューターで実行されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスからポート番号の取得を試みます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスが実行されていない場合、ポート番号がこの設定か、接続文字列の一部として指定されている必要があります。  
  
 **Enabled**  
 可能な値は、 **[はい]** と **[いいえ]** です。  
  
 **[Keep Alive]**  
 このパラメーターは、 **KEEPALIVE** パケットを送信することによって、アイドル状態の接続が壊れていないかどうかを TCP が確認する頻度をミリ秒単位で設定します。 既定値は 30,000 ミリ秒です。  
  
 **[Keep Alive 間隔]**  
 このパラメーターは、応答を受信するまで **KEEPALIVE** パケットを再送信する間隔をミリ秒単位で設定します。 既定値は 1,000 ミリ秒です。  
  
## <a name="see-also"></a>参照  
 [ネットワーク プロトコルを選択します。](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)   
 [[別名 - 新規] ダイアログ ボックス &#40;[別名] タブ&#41;](../../../2014/tools/configuration-manager/new-alias-alias-tab.md)   
 [&#60;エイリアス&#62;プロパティ&#40;[別名] タブ&#41;](../../../2014/tools/configuration-manager/alias-properties-alias-tab.md)  
  
  