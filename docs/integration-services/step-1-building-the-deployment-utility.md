---
title: "手順 1: 配置ユーティリティの構築 | Microsoft Docs"
ms.custom: ""
ms.date: "02/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 1ff4dcff-89b3-4b99-a725-5f7963e98abf
caps.latest.revision: 21
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
---
# 手順 1: 配置ユーティリティの構築
ここでは、Deployment Tutorial プロジェクト用の配置ユーティリティを構成し、構築します。  
  
配置ユーティリティを構築する前に、Deployment Tutorial プロジェクトのプロパティを変更する必要があります。 これらのプロパティを構成するには、**[Deployment Tutorial プロパティ ページ]** ダイアログ ボックスを使用します。 このダイアログ ボックスでは、配置中に構成を更新する機能を有効にし、構築プロセスによる配置ユーティリティの生成を指定する必要があります。 プロパティを設定したら、プロジェクトを構成します。  
  
[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]  には、パッケージのデバッグに使用できる一連のウィンドウが用意されています。 これらのウィンドウでは、エラー、警告、および情報メッセージの表示、実行時のパッケージ状態の追跡、または構築プロセスの進行状況と結果の表示ができます。 このレッスンでは、配置ユーティリティの構築の進行状況と結果を出力ウィンドウに表示します。  
  
### 配置ユーティリティのプロパティを設定するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] がまだ開いていない場合は、**[スタート]** ボタンをクリックし、**[すべてのプログラム]**、**[Microsoft SQL Server]** の順にポイントして、**[Business Intelligence Development Studio]** をクリックします。  
  
2.  **[ファイル]** メニューの **[開く]** をクリックし、**[プロジェクト/ソリューション]** をクリックします。次に、**[Deployment Tutorial]** フォルダーをクリックして **[開く]** をクリックし、**Deployment Tutorial.sln** をダブルクリックします。  
  
3.  ソリューション エクスプローラーで [Deployment Tutorial] を右クリックし、**[プロパティ]** をクリックします。  
  
4.  **[Deployment Tutorial プロパティ ページ]** ダイアログ ボックスで、[構成プロパティ] を展開し、[配置ユーティリティ] をクリックします。  
  
5.  **[Deployment Tutorial プロパティ ページ]** ダイアログ ボックスの右側のペインで、**AllowConfigurationChanges** が **true** に設定されていることを確認し、**CreateDeploymentUtility** を **true** に設定し、**DeploymentOutputPath** の既定値を必要に応じて更新します。  
  
6.  **[OK]**をクリックします。  
  
### 配置ユーティリティを構築するには  
  
1.  ソリューション エクスプローラーで、**[Deployment Tutorial]** をクリックします。  
  
2.  **[表示]** メニューの **[出力]** をクリックします。 既定では、出力ウィンドウは [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] の左下隅に配置されます。  
  
3.  **[ビルド]** メニューの **[Deployment Tutorial のビルド]** をクリックします。  
  
4.  出力ウィンドウに、次のような情報が表示されます。  
  
    ビルド開始:  SQL Integration Services プロジェクト: インクリメンタル...  
  
    配置ユーティリティを作成しています  
  
    配置ユーティリティが作成されました。  
  
    ビルドの完了 -- エラー 0 個、警告 0 個  
  
    ========== ビルド: 0 正常終了、0 失敗、1 更新、0 スキップ ==========  
  
5.  **[ファイル]** メニューの **[終了]**をクリックします。 Deployment Tutorial アイテムへの変更の保存を指示するメッセージが表示されたら、**[はい]** をクリックします。  
  
## このレッスンの次の作業  
[手順 2: 配置バンドルの確認](../integration-services/step-2-verifying-the-deployment-bundle.md)  
  
## 参照  
[配置ユーティリティを作成する](../integration-services/packages/create-a-deployment-utility.md)  
  
  
  
