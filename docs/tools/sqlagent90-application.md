---
title: "sqlagent90 アプリケーション | Microsoft Docs"
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
  - "SQL Server エージェントの起動"
  - "sqlagent90 アプリケーション"
  - "SQL Server エージェント, 開始"
  - "コマンド プロンプト ユーティリティ [SQL Server], sqlagent90"
ms.assetid: e8b80e8d-d0c9-4500-a868-0ce08233da08
caps.latest.revision: 34
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 34
---
# sqlagent90 アプリケーション
  **sqlagent90** アプリケーションは、コマンド プロンプトから [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェントを起動します。 通常、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェントは [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] から実行するか、またはアプリケーションで SQL-SMO メソッドを使って実行します。 ただし、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェントを診断する場合や、プライマリ サポート プロバイダーから指示された場合は、コマンド プロンプトから **sqlagent90** を実行してください。  
  
## 構文  
  
```  
  
sqlagent90  
-c [-v] [-i instance_name]  
```  
  
## 引数  
 **-c**  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェントをコマンド プロンプトから実行し、Microsoft Windows サービス コントロール マネージャーの制御下にないことを指定します。 **-c** を使用する場合、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェントを、管理ツールのサービス アプリケーションまたは [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 構成マネージャーから制御することはできません。 この引数は必須です。  
  
 **-v**  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェントを冗長モードで実行し、診断情報をコマンド プロンプト ウィンドウに書き込みます。 診断情報は、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェントのエラー ログに書き込まれる情報と同じです。  
  
 **-i** *instance_name*  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェントを *instance_name* によって指定された名前付き [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスに接続します。  
  
## 解説  
 **sqlagent90** は、**-v** スイッチが指定された場合にのみ、著作権に関するメッセージを表示した後にコマンド プロンプト ウィンドウに出力を表示します。 **sqlagent90** を停止するには、コマンド プロンプトで Ctrl キーを押しながら C キーを押します。 **sqlagent90** を停止する前に、コマンド プロンプト ウィンドウを閉じないでください。  
  
## 参照  
 [管理タスクの自動化 &#40;SQL Server エージェント&#41;](../ssms/agent/automated-administration-tasks-sql-server-agent.md)  
  
  