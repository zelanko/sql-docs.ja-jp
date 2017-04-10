---
title: "[データベース構成] ページ (Master Data Services 構成マネージャー) | Microsoft Docs"
ms.custom: ""
ms.date: "03/20/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.mds.configmanager.dbpg.f1"
ms.assetid: dd72220e-a599-465d-8b84-9bb6a7433216
caps.latest.revision: 8
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 7
---
# [データベース構成] ページ (Master Data Services 構成マネージャー)
  **[データベース構成]** ページを使用すると、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースのシステム設定を編集できます。 システム設定は、選択した [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースに関連付けられている Web アプリケーションおよび Web サービスすべてに影響します。 システム設定を有効にして構成できるようにするには、事前に [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースを選択または作成する必要があります。  
  
## 現在のデータベース  
 システム設定の編集を行う、既存の [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースを選択するか、新しいデータベースを作成します。 新しいデータベースは、作成後に選択されます。  
  
|コントロール名|Description|  
|------------------|-----------------|  
|**SQL Server インスタンス (SQL Server instance)**|選択した [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスの名前が表示されます。 これは、インスタンスに接続して、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースを選択または作成するまで、空白です。|  
|**[Master Data Services データベース]**|選択した [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースの名前が表示されます。 これは、インスタンスに接続して、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースを選択または作成するまで、空白です。|  
|**[Master Data Services データベース バージョン]**|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベース スキーマのバージョン。|  
|**[データベースの作成]**|**データベースの作成** ウィザードを開きます。このウィザードから、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスに接続し、そのインスタンス用の [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースを作成できます。|  
|**[データベースの選択]**|**[データベースへの接続]** ダイアログ ボックスを開きます。このダイアログ ボックスで、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスに接続して、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースを選択できます。|  
|**[データベースのアップグレード]**|ウィザードを開き、指定した [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースをアップグレードできます。 このボタンは指定したデータベースでアップグレードが必要な場合にのみ使用できます。|  
|**[修復]**|MDS データベースが正しくインストールされていることを確認するには、このボタンをクリックします。 これは、MDS データベースをホストしたことがない [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスに MDS データベースをバックアップおよび復元する場合に便利です。|  
  
## システム設定  
 選択した [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースに関連付けられている Web アプリケーションおよび Web サービスすべてのシステム設定を編集します。  
  
 これらの設定は、[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]で使用することができ、データベースの System Settings テーブル (mdm.tblSystemSetting) に格納されます。 すべての設定の一覧については、「[システム設定 (マスター データ サービス)](../master-data-services/system-settings-master-data-services.md)」を参照してください。  
  
## 参照  
 [マスター データ サービスの概要 (SQL Server 2016)](../Topic/Get%20Started%20with%20Master%20Data%20Services%20\(SQL%20Server%202016\).md)   
 [データベース要件 &#40;マスター データ サービス&#41;](../master-data-services/install-windows/database-requirements-master-data-services.md)  
  
  