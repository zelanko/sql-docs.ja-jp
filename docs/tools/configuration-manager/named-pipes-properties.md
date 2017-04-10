---
title: "[名前付きパイプのプロパティ] ダイアログ ボックス | Microsoft Docs"
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
  - "パイプ [SQL Server]"
  - "リッスン [SQL Server], パイプ"
  - "パイプ [SQL Server], パイプのリッスン"
  - "名前付きパイプ [SQL Server], パイプのリッスン"
ms.assetid: a5fd5b8e-f889-485b-89e3-d4010ec4c6ec
caps.latest.revision: 32
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 32
---
# [名前付きパイプのプロパティ] ダイアログ ボックス
  **[名前付きパイプのプロパティ]** ダイアログ ボックスの **[プロトコル]**ページでは、名前付きパイプ プロトコルを使用している場合に [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がリッスンする名前付きパイプの表示や変更を行います。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を再起動する必要があるのは、プロトコルを有効または無効にする場合、または名前付きパイプを変更する場合です。  
  
## オプション  
 **有効**  
 可能な値は **Yes** と **No** です。  
  
 **[パイプ名]**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がリッスンする名前付きパイプを指定します。 既定では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が既定のインスタンスの場合は `\\.\pipe\sql\query` と、名前付きインスタンスの場合は `\\.\pipe\MSSQL$<instancename>\sql\query` でリッスンします。 このフィールドには最大 2,047 文字まで入力できます。  
  
## 代替名前付きパイプの作成  
 名前付きパイプを変更するには、新しいパイプ名を **[パイプ名]** ボックスに入力し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を再起動します。 **sql\query** は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が使用する名前付きパイプとしてよく知られているため、パイプを変更することによって、悪意のあるプログラムによる攻撃の危険性を減らすことができます。  
  
### 例  
 **unit\app** パイプでリッスンするには、**\\\\.\pipe\unit\app** と入力します。  
  
 **acct** パイプでリッスンするには、**\\\\.\pipe\acct** と入力します。  
  
## 参照  
 [サーバー ネットワーク プロトコルの有効化または無効化](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)   
 [ネットワーク プロトコルの選択](../Topic/Choosing%20a%20Network%20Protocol.md)   
 [名前付きパイプを使用した有効な接続文字列の作成](../Topic/Creating%20a%20Valid%20Connection%20String%20Using%20Named%20Pipes.md)  
  
  