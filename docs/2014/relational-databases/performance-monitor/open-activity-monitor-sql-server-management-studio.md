---
title: 利用状況モニターを開く方法 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Activity Monitor [SQL Server], setting the refresh interval
- refresh interval for Activity Monitor
- Activity Monitor [SQL Server], opening
- opening Activity Monitor
ms.assetid: 0a6eeb16-f02b-479d-9a60-543e40ebf46b
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 0d1c0312acfcd2e5dbb17d740fe2659cb8c91bbe
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63032006"
---
# <a name="open-activity-monitor-sql-server-management-studio"></a>利用状況モニターを開く方法 (SQL Server Management Studio)
  このトピックでは、利用状況モニターを開いて、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセスおよびこれらのプロセスが現在の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスに与える影響に関する情報を取得する方法について説明します。 また、利用状況モニターの更新間隔の設定方法についても説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [セキュリティ](#Security)  
  
-   **利用状況モニターを開くための方法:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
-   **更新間隔を設定する方法:**  [SQL Server Management Studio](#Refresh)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
 利用状況モニターでは、監視対象となるインスタンスでクエリを実行し、[利用状況モニター] 表示ペインに表示する情報を取得します。 更新間隔を 10 秒未満に設定すると、これらのクエリを実行する時間がサーバーのパフォーマンスに影響を与える可能性があります。  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 利用状況モニターを表示するには、VIEW SERVER STATE 権限が必要です。 利用状況モニターの [データ ファイル I/O] セクションを表示するには、VIEW SERVER STATE に加えて、CREATE DATABASE、ALTER ANY DATABASE、VIEW ANY DEFINITION のいずれかの権限が必要です。  
  
 プロセスを強制終了するには、sysadmin 固定サーバー ロールまたは processadmin 固定サーバー ロールのメンバーである必要があります。  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-open-activity-monitor-in-sql-server-management-studio"></a>SQL Server Management Studio で利用状況モニターを開くには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の [標準] ツール バーの **[利用状況モニター]** をクリックします。  
  
2.  **[サーバーへの接続]** ダイアログ ボックスで、サーバー名と認証モードを選択して **[接続]** をクリックします。  
  
 また、Ctrl キーと Alt キーを押しながら A キーを押すと、いつでも利用状況モニターを表示できます。  
  
#### <a name="to-open-activity-monitor-in-object-explorer"></a>オブジェクト エクスプローラーで利用状況モニターを開くには  
  
-   オブジェクトエクスプローラーで、インスタンス名を右クリックし、[**利用状況モニター**] を選択します。  
  
#### <a name="to-open-activity-monitor-when-opening-sql-server-management-studio"></a>SQL Server Management Studio を開くときに利用状況モニターを開くには  
  
1.  **[ツール]** メニューの **[オプション]** をクリックします。  
  
2.  **[オプション]** ダイアログ ボックスで **[環境]** を展開し、 **[全般]** をクリックします。  
  
3.  **[スタートアップ時]** ボックスで **[オブジェクト エクスプローラーと利用状況モニターを開く]** をクリックします。  
  
4.  変更を有効にするには、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を閉じて再度開きます。  
  
###  <a name="to-set-the-activity-monitor-refresh-interval"></a><a name="Refresh"></a>利用状況モニターの更新間隔を設定するには  
  
-   利用状況モニターを開きます。  
  
-   **[概要]** を右クリックして **[更新間隔]** をクリックし、利用状況モニターで新しいインスタンス情報を取得する間隔を選択します。  
  
  
