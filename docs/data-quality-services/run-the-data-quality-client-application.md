---
title: "Data Quality Client アプリケーションの実行 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dqs.browseforservers.f1"
  - "sql13.dqs.connecttoserver.f1"
ms.assetid: 0b2aa202-7ab2-4c9d-b0f1-802588053a1e
caps.latest.revision: 13
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 13
---
# Data Quality Client アプリケーションの実行
  実行 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], 、ログオンして、 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]です。  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Prerequisites"></a> 前提条件  
 DQSInstaller.exe ファイルを実行して [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] のインストールを完了しておく必要があります。 詳細については、次を参照してください。 [データ品質サーバー インストールの完了に DQSInstaller.exe を実行](../data-quality-services/install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md)します。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> アクセス許可  
 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] にログオンするには、DQS_MAIN データベースに対して、3 つの DQS ロール (dqs_administrator、dqs_kb_editor、dqs_kb_operator) のいずれかが必要です。  
  
##  <a name="Run"></a> Data Quality Client の実行  
 実行する [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] インストールしたコンピューターで。  
  
1.  クリックして **開始**, 、] をポイント **すべてのプログラム**, 、] をクリックして **[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]**, 、] をクリックして **Data Quality Services**, 、順にクリック **Data Quality Client**です。  
  
2.   **サーバーへの接続** ] ダイアログ ボックス。  
  
    1.  [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] アプリケーションを接続するサーバーを指定します。 選択 **(LOCAL)** への接続に [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 、ローカル コンピューターです。 下矢印をクリックして選択もできます **\< [参照のサーバーをネットワーク詳細>** 別のサーバーに接続する (または名前でローカル サーバーに接続する)。  **サーバーの参照** ] ダイアログ ボックスが表示されます。 サーバーを選択することができます、 **ローカル サーバー** ] タブまたは [、 **ネットワーク サーバー** ] タブをクリックします。  
  
    2.  間で転送するデータを暗号化する [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] と [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], 、] をクリックして **オプション**, 、クリックして、 **暗号化接続** ] チェック ボックスです。  
  
3.  **[接続]**をクリックします。  
  
 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のホーム画面が表示されます。 詳細については、次を参照してください。 [データ品質クライアント ホームの画面](../data-quality-services/data-quality-client-home-screen.md)します。  
  
  