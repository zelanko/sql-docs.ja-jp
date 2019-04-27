---
title: '[データベース構成] ページ (Master Data Services 構成マネージャー) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
f1_keywords:
- sql12.mds.configmanager.dbpg.f1
ms.assetid: dd72220e-a599-465d-8b84-9bb6a7433216
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: b28eb8d2455584bae77d8a7b62707b8888da27cf
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62765785"
---
# <a name="database-configuration-page-master-data-services-configuration-manager"></a>[データベース構成] ページ (Master Data Services 構成マネージャー)
  **[データベース構成]** ページを使用すると、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースのシステム設定を編集できます。 システム設定は、選択した [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースに関連付けられている Web アプリケーションおよび Web サービスすべてに影響します。 システム設定を有効にして構成できるようにするには、事前に [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースを選択または作成する必要があります。  
  
## <a name="current-database"></a>現在のデータベース  
 システム設定の編集を行う、既存の [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースを選択するか、新しいデータベースを作成します。 新しいデータベースは、作成後に選択されます。  
  
|コントロール名|説明|  
|------------------|-----------------|  
|**SQL Server インスタンス (SQL Server instance)**|選択した [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスの名前が表示されます。 これは、インスタンスに接続して、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースを選択または作成するまで、空白です。|  
|**[Master Data Services データベース]**|選択した [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースの名前が表示されます。 これは、インスタンスに接続して、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースを選択または作成するまで、空白です。|  
|**[Master Data Services データベース バージョン]**|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベース スキーマのバージョン。|  
|**[データベースの作成]**|**データベースの作成** ウィザードを開きます。このウィザードから、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスに接続し、そのインスタンス用の [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースを作成できます。|  
|**[データベースの選択]**|**[データベースへの接続]** ダイアログ ボックスを開きます。このダイアログ ボックスで、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスに接続して、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースを選択できます。|  
|**[データベースのアップグレード]**|ウィザードを開き、指定した [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースをアップグレードできます。 このボタンは指定したデータベースでアップグレードが必要な場合にのみ使用できます。|  
|**[修復]**|MDS データベースが正しくインストールされていることを確認するには、このボタンをクリックします。 これは、MDS データベースをホストしたことがない [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスに MDS データベースをバックアップおよび復元する場合に便利です。|  
  
## <a name="system-settings"></a>システム設定  
 選択した [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースに関連付けられている Web アプリケーションおよび Web サービスすべてのシステム設定を編集します。  
  
 これらの設定は、[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]で使用することができ、データベースの System Settings テーブル (mdm.tblSystemSetting) に格納されます。 すべての設定の一覧については、「[システム設定 (マスター データ サービス)](system-settings-master-data-services.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [マスター データ サービスのデータベースと web サイトの設定します。](../../2014/master-data-services/set-up-the-database-and-website-for-master-data-services.md)   
 [データベース要件 &#40;マスター データ サービス&#41;](install-windows/database-requirements-master-data-services.md)  
  
  
