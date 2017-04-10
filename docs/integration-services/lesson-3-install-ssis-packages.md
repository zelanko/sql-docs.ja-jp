---
title: "レッスン 3: SSIS パッケージのインストール | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 87bc4d82-39d8-424f-886f-98cf1e4bb07a
caps.latest.revision: 16
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 16
---
# レッスン 3: SSIS パッケージのインストール
「[レッスン 2: SSIS で配置バンドルを作成する](../integration-services/lesson-2-create-the-deployment-bundle-in-ssis.md)」では、配置ユーティリティを構築し、配置バンドルを作成しました。配置バンドルには、別のコンピューターにパッケージをインストールする際に必要となるアイテムが含まれています。 また、配置バンドルのファイル リストを確認し、配置ユーティリティの構築時に作成されたマニフェスト ファイルの内容も調べました。  
  
このレッスンでは、配置バンドルを目的のコンピューターにコピーし、パッケージ インストール ウィザードを実行して、そのコンピューターにパッケージ、パッケージの依存関係、および補助ファイルをインストールします。 パッケージは **msdb** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データベースにインストールされ、その他の項目はファイル システムにインストールされます。 パッケージのインストールが完了すると、パッケージ実行ユーティリティを使用して [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] からパッケージを実行し、配置をテストします。  
  
**このレッスンの推定所要時間:** 30 分  
  
## このレッスンの作業  
このレッスンの内容は次のとおりです。  
  
-   [手順 1: 配置バンドルのコピー](../integration-services/step-1-copying-the-deployment-bundle.md)  
  
-   [手順 2: パッケージ インストール ウィザードの実行](../integration-services/step-2-running-the-package-installation-wizard.md)  
  
-   [手順 3 : 配置したパッケージのテスト](../integration-services/step-3-testing-the-deployed-packages.md)  
  
## レッスンの開始  
[手順 1: 配置バンドルのコピー](../integration-services/step-1-copying-the-deployment-bundle.md)  
  
  
  
