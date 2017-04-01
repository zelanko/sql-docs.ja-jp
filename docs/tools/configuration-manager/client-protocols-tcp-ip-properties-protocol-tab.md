---
title: "クライアント プロトコル - [TCP/IP のプロパティ] ダイアログ ボックス ([プロトコル] タブ) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "TCP/IP [SQL Server], クライアント プロトコル"
  - "クライアント プロトコル [SQL Server]"
ms.assetid: d04f1bce-069c-4a02-b561-c87c3282be36
caps.latest.revision: 25
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 25
---
# クライアント プロトコル - [TCP/IP のプロパティ] ダイアログ ボックス ([プロトコル] タブ)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーでは、**[TCP/IP のプロパティ]** ダイアログ ボックスの **[プロトコル]** タブを使用して、以下のオプションの表示や指定を行います。 別のポートに接続するには、**[既定のポート]** ボックスにポート番号を入力します。 接続文字列の詳細については、「[TCP/IP を使用した有効な接続文字列の作成](../../tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)」を参照してください。  
  
## オプション  
 **[既定のポート]**  
 TCP/IP Net-Library が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の対象インスタンスに接続するために使用するポートを指定します。 既定値のポートは 1433 です。  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]の既定のインスタンスに接続する場合、クライアントはこの値を使用します。 既定のインスタンスが別のポートでリッスンするように構成されている場合は、この値をそのポート番号に変更してください。  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]の名前付きインスタンスに接続する場合、クライアントはサーバー コンピューターで実行されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスからポート番号の取得を試みます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスが実行されていない場合、ポート番号がこの設定か、接続文字列の一部として指定されている必要があります。  
  
 **有効**  
 可能な値は、**[はい]** と **[いいえ]** です。  
  
 **[Keep Alive]**  
 このパラメーターは、**KEEPALIVE** パケットを送信することによって、アイドル状態の接続が壊れていないかどうかを TCP が確認する頻度をミリ秒単位で設定します。 既定値は 30,000 ミリ秒です。  
  
 **[Keep Alive 間隔]**  
 このパラメーターは、応答を受信するまで **KEEPALIVE** パケットを再送信する間隔をミリ秒単位で設定します。 既定値は 1,000 ミリ秒です。  
  
## 参照  
 [ネットワーク プロトコルの選択](../Topic/Choosing%20a%20Network%20Protocol.md)   
 [[別名 - 新規] ダイアログ ボックス &#40;[別名] タブ&#41;](../Topic/New%20Alias%20\(Alias%20Tab\).md)   
 [[&#60;Alias&#62; のプロパティ] ダイアログ ボックス &#40;[別名] タブ&#41;](../Topic/%3CAlias%3E%20Properties%20\(Alias%20Tab\).md)  
  
  