---
title: "Windows アプリケーション ログの表示 (Windows) | Microsoft Docs"
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
  - "ログの表示"
  - "アプリケーション ログ [SQL Server]"
  - "ログ [SQL Server], アプリケーション"
  - "Windows NT アプリケーション ログの監視 [SQL Server]"
  - "Windows NT アプリケーション ログ [SQL Server]"
  - "ログの確認"
  - "監視 [SQL Server], イベント"
  - "ログ [SQL Server], 表示"
ms.assetid: 168a6c6e-12df-46a9-9904-55d63ca8fe14
caps.latest.revision: 25
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
---
# Windows アプリケーション ログの表示 (Windows)
  Windows アプリケーション ログを使用するように [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が構成されている場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各セッションで新しいイベントがそのログに書き込まれます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログとは異なり、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを開始するたびに新しいアプリケーション ログが作成されることはありません。  
  
### Windows アプリケーション ログを表示するには  
  
1.  **[スタート]** ボタンをクリックし、**[すべてのプログラム]**、**[管理ツール]** の順にポイントして、**[イベント ビューアー]** をクリックします。  
  
2.  イベント ビューアーで **[アプリケーション]** をクリックします。  
  
3.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [ソース] 列に **MSSQLSERVER** と表示されている項目が  のイベントです。名前付きインスタンスの場合は、**[ソース]** 列に **MSSQL$***<instance_name>* と表示されます。 また、SQL Server エージェントのイベントは SQLSERVERAGENT と表示されます ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の名前付きインスタンスの場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのイベントは **SQLAgent$**\<*instance_name*> と表示されます)。 Microsoft Search サービスのイベントは "**Microsoft Search**" と表示されます。  
  
4.  別のコンピューターのログを表示するには、**[イベント ビューアー]** を右クリックし、**[別のコンピューターへ接続]** をクリックします。次に、**[コンピューターの選択]** ダイアログ ボックスで必要な項目を設定します。  
  
5.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のイベントのみを表示する場合は、**[表示]** メニューの **[フィルター]** をクリックし、**[イベント ソース]** ボックスの一覧で **[MSSQLSERVER]** を選択します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのイベントのみを表示するには、**[イベント ソース]** ボックスの一覧で **[SQLSERVERAGENT]** を選択します。  
  
6.  イベントについての詳細情報を表示するには、イベントをダブルクリックします。  
  
## 参照  
 [SQL Server エラー ログの表示 &#40;SQL Server Management Studio&#41;](../../relational-databases/performance/view-the-sql-server-error-log-sql-server-management-studio.md)  
  
  