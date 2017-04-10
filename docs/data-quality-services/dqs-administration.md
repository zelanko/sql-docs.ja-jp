---
title: "DQS 管理 | Microsoft Docs"
ms.custom: ""
ms.date: "10/01/2012"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DQS 管理"
  - "管理"
  - "dqs、管理"
ms.assetid: 9940ef5d-f6f6-4dec-9414-1077a4d7f12b
caps.latest.revision: 21
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 21
---
# DQS 管理
  [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) では、さまざまな DQS アクティビティが実行を管理することができる [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], 、DQS アクティビティに関連するサーバー レベルのプロパティを構成する、参照データ サービスの設定を構成および DQS ログ設定を構成します。 これらの操作が実行されます。、 **管理** 機能 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]です。 DQS でのセキュリティ アクセス (ロール) に基づいて、特定の管理機能へのアクセスが許可/禁止されます。  
  
 これらの管理機能とは別に、このトピックでは、[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] を使用して実行しない管理アクティビティである DQS データベースのバックアップと復元についても説明します。  
  
 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] での管理機能には次のような利点があります。  
  
-   データ スチュワードは、[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] から [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] でのさまざまな DQS アクティビティを監視できます。  
  
-   により、DQS 管理者は DQS アクティビティを監視する、 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] から、 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], 、および *終了* 実行中のアクティビティまたは *停止* ために必要な場合は、アクティビティ内で実行中のプロセスです。  
  
-   Windows Azure Marketplace との接続の設定や、ダイレクト サード パーティ参照データ サービス プロバイダーの管理など、参照データ サービスの設定を構成します。  
  
-   クレンジングおよび照合アクティビティのしきい値を構成します。  
  
-   [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] での通知を有効または無効にします。  
  
-   イベントの重大度レベルに基づくログを構成します。  
  
##  <a name="AdminUsingClent"></a> Data Quality Client を使用した管理アクティビティ  
 使用してこれらのアクティビティが実行される、 **管理** 機能 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]です。  
  
### [アクティビティ監視]  
  **アクティビティの監視** 画面で [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] に対して実行された各アクティビティに関する詳細な情報を表示、 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]です。 この画面は、[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] アプリケーションが接続されている [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 上で実行されているすべてのアクティビティに関する高レベルの監視を実行するために主にデータ スチュワードによって使用されます。 この画面では、システム レベルの監視は提供されません。 また、この画面を使用すると、DQS 管理者は、必要に応じて、実行中のアクティビティを終了したり、アクティビティ内で実行中のプロセスを停止したりして、アクティビティまたはアクティビティ内のプロセスを制御できます。 ナレッジの検出、ドメインの管理、照合ポリシー、クレンジング、照合、および SQL Server Integration Services (SSIS) ベースのクレンジングに関するデータが表示されます。  
  
### 構成  
  **構成** 画面で [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] により、DQS 管理者は、次の処理を実行します。  
  
-   **参照データ**: 参照データ サービス プロバイダーの構成: Windows Azure Marketplace またはダイレクト参照データ サービス プロバイダー。 参照データ サービス プロバイダーを設定した後は、ナレッジ ベースでのドメイン管理アクティビティの間にドメイン/複合ドメインと参照データをマップし、データ品質プロジェクトでのクレンジング アクティビティに同じナレッジ ベースを使用できます。 また、インターネットに接続して Windows Azure Marketplace を使用するためのプロキシ設定を指定できます。  
  
-   **[全般設定**: データ クレンジングおよびデータ照合、およびでのプロファイリングに対する通知を有効にするかどうかのしきい値の値を指定 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]します。 これらのしきい値は、データ品質プロジェクトでのコンピューター支援型のクレンジングおよび照合アクティビティの間に、DQS によって使用されます。  
  
-   **ログ設定**: DQS でのログ ファイル、DQS で実行されるアクティビティを記録およびメンテナンス時に運用上の問題を追跡およびトラブルシューティングに役立ちます。 さまざまな DQS 機能 (ドメイン管理、ナレッジ検出、クレンジング、照合、参照データ サービス) および DQS モジュールに関してログに記録するメッセージを、イベントの重大度レベルに基づいてフィルターできます。  
  
> [!NOTE]  
>   **構成** 画面は、DQS_MAIN データベースに対する dqs_administrator ロールを持つユーザーのみ使用できます。  
  
##  <a name="AdminOutsideClient"></a> Data Quality Client の外部での管理アクティビティ  
 アクティビティは Data Quality Client の外部で実行されます。  
  
-   **バックアップし、復元の DQS データベース**: バックアップと復元 DQS データベースのバックアップおよび DQS に固有のいくつかの考慮事項を持つ SQL Server データベースを復元すると同じです。  
  
-   **デタッチし、DQS データベースのアタッチ**: デタッチし、DQS データベースをアタッチする手順はのデタッチとアタッチは、DQS に固有のいくつかの考慮事項が任意の SQL Server データベースと同じです。  
  
 詳細については、次を参照してください。 [DQS データベースの管理](../data-quality-services/manage-dqs-databases.md)です。  
  
## 関連タスク  
  
|タスクの説明|トピック|  
|----------------------|-----------|  
|DQS のアクティビティを監視する方法について説明します。|[DQS アクティビティの監視](../data-quality-services/monitor-dqs-activities.md)|  
|DQS で参照データの設定を構成する方法について説明します。|[Configure DQS to Use Reference Data](../data-quality-services/configure-dqs-to-use-reference-data.md)|  
|クレンジングおよび照合アクティビティのしきい値を構成する方法について説明します。|[Configure Threshold Values for Cleansing and Matching](../data-quality-services/configure-threshold-values-for-cleansing-and-matching.md)|  
|DQS で通知を有効または無効にする方法について説明します。|[Enable or Disable Profiling Notifications in DQS](../data-quality-services/enable-or-disable-profiling-notifications-in-dqs.md)|  
|イベントの重大度レベルに基づいて DQS のログを構成する方法について説明します。|[Configure Severity Levels for DQS Log Files](../data-quality-services/configure-severity-levels-for-dqs-log-files.md)|  
|DQS ログの詳細設定を構成する方法について説明します。|[DQS ログ ファイルの詳細設定の構成](../data-quality-services/configure-advanced-settings-for-dqs-log-files.md)|  
|DQS データベースのバックアップと復元の方法について説明します。|[DQS データベースのバックアップと復元](../data-quality-services/backing-up-and-restoring-dqs-databases.md)|  
|DQS データベースをデタッチおよびアタッチする方法について説明します。|[Detaching and Attaching DQS Databases](../data-quality-services/detaching-and-attaching-dqs-databases.md)|  
  
## 参照  
 [Reference Data Services in DQS](../data-quality-services/reference-data-services-in-dqs.md)   
 [DQS ログ ファイルの管理](../data-quality-services/manage-dqs-log-files.md)   
 [DQS データベースの管理](../data-quality-services/manage-dqs-databases.md)  
  
  