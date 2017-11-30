---
title: "Reporting Services のバックアップおよび復元操作 | Microsoft Docs"
ms.custom: 
ms.date: 05/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- databases [Reporting Services], backing up
- databases [Reporting Services], restoring
- databases [Reporting Services], moving
- backing up databases [Reporting Services]
- moving databases
- restoring databases [Reporting Services]
- files [Reporting Services], restoring
- files [Reporting Services], backing up
ms.assetid: 157bc376-ab72-4c99-8bde-7b12db70843a
caps.latest.revision: "43"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: b16289b6455ac596fcc05b58db3793e3c8d5c541
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="backup-and-restore-operations-for-reporting-services"></a>Reporting Services のバックアップおよび復元操作

  このトピックでは、インストールした [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] で使用するデータ ファイルの概要と、これらのファイルをバックアップするタイミングおよび方法について説明します。 レポート サーバー データベース ファイルのバックアップ/復元プランの作成は、復旧計画の最も重要な部分です。 ただし、さらに包括的な復旧計画には、暗号化キー、カスタム アセンブリや拡張機能、構成ファイル、レポートおよびモデルのソース ファイルのバックアップなども必要になります。  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブ モード | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モード  
  
 バックアップ操作および復元操作は、インストールした [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の全体または一部を移動する際によく使用します。  
  
-   レポート サーバー データベースだけを移動する場合は、バックアップと復元またはアタッチとデタッチを使用して、別の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスにデータベースを再配置できます。 詳細については、「 [別のコンピューターへのレポート サーバー データベースの移動 (SSRS ネイティブ モード)](../../reporting-services/report-server/moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md)」を参照してください。  
  
-   インストールされている [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を別のコンピューターへ移動することを "移行" といいます。 インストールを移行する場合、セットアップを実行して新しいレポート サーバー インスタンスをインストールし、次にインスタンス データを移行先のコンピューターにコピーします。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インストールの移行の詳細については、次のトピックを参照してください。  
  
    -   [Reporting Services のアップグレードと移行](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)  
  
    -   [Reporting Services の移行 &#40;SharePoint モード&#41;](../../reporting-services/install-windows/migrate-a-reporting-services-installation-sharepoint-mode.md)  
  
    -   [Reporting Services のインストールの移行 &#40;ネイティブ モード&#41;](../../reporting-services/install-windows/migrate-a-reporting-services-installation-native-mode.md)  
  
## <a name="backing-up-the-report-server-databases"></a>レポート サーバー データベースのバックアップ  
 レポート サーバーはステートレス サーバーであるため、アプリケーション データはすべて、 **インスタンスで稼働している** reportserver **および** reportservertempdb [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] データベースに格納されます。 **reportserver** データベースと **reportservertempdb** データベースは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースでサポートされているバックアップ方式のいずれかを使用してバックアップできます。 レポート サーバー データベースについては、次のような推奨事項があります。  
  
-   **reportserver** データベースをバックアップするには、完全復旧モデルを使用します。  
  
-   **reportservertempdb** データベースをバックアップするには、単純復旧モデルを使用します。  
  
-   各データベースに対して異なるバックアップ スケジュールを設定できます。 **reportservertempdb** をバックアップする唯一の理由は、ハードウェア障害が発生した場合にこのデータベースの再作成を回避することです。 ハードウェア障害が発生した場合、 **reportservertempdb**のデータを復旧する必要はありませんが、テーブル構造については復旧が必要になります。 **reportservertempdb**が失われた場合、レポート サーバー データベースの再作成以外にこのデータベースを復元する方法はありません。 **reportservertempdb**を再作成する場合、プライマリ レポート サーバー データベースと同じ名前を使用することが重要です。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] リレーショナル データベースのバックアップおよび復旧の詳細については、「 [SQL Server データベースのバックアップと復元](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)」を参照してください。  
  
> [!IMPORTANT]  
>  レポート サーバーが SharePoint モードの場合は、SharePoint 構成データベースや [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 警告データベースなど、考慮する必要があるデータベースがあります。 SharePoint モードでは、それぞれの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションに対して 3 つのデータベースが作成されます。 その 3 つのデータベースとは、 **reportserver**、 **reportservertempdb**、および **dataalerting** です。 詳細については、「 [Reporting Services SharePoint サービス アプリケーションのバックアップと復元](../../reporting-services/report-server-sharepoint/backup-and-restore-reporting-services-sharepoint-service-applications.md)」を参照してください。  
  
## <a name="backing-up-the-encryption-keys"></a>暗号化キーのバックアップ  
 インストールした [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を初めて構成するときは、暗号化キーをバックアップする必要があります。 サービス アカウントの ID やコンピューターの名前を変更する際にも、そのつど暗号化キーをバックアップする必要があります。 詳細については、「 [Back Up and Restore Reporting Services Encryption Keys](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)」を参照してください。 SharePoint モードのレポート サーバーについては、「 [Reporting Services SharePoint サービス アプリケーションの管理](../../reporting-services/report-server-sharepoint/manage-a-reporting-services-sharepoint-service-application.md)」の「キー管理」のセクションを参照してください。  
  
## <a name="backing-up-the-configuration-files"></a>構成ファイルのバックアップ  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] では、構成ファイルを使用してアプリケーション設定を格納します。 初めてサーバーを構成するときおよびカスタム拡張機能を配置した後は常に、ファイルをバックアップする必要があります。 バックアップするのは次のファイルです。  
  
-   Rsreportserver.config  
  
-   Rssvrpolicy.config  
  
-   Rsmgrpolicy.config  
  
-   Reportingservicesservice.exe.config  
  
-   レポート サーバーおよびレポート マネージャーの [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] アプリケーション用の Web.config  
  
-   用の Machine.config [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]  
  
## <a name="backing-up-data-files"></a>データ ファイルのバックアップ  
 レポート デザイナーおよびモデル デザイナーで作成およびメンテナンスしているファイルをバックアップします。 これらのファイルには、レポート定義 (.rdl) ファイル、レポート モデル (.smdl) ファイル、共有データ ソース (.rds) ファイル、データ ビュー (.dv) ファイル、データ ソース (.ds) ファイル、レポート サーバー プロジェクト (.rptproj) ファイル、およびレポート ソリューション (.sln) ファイルが含まれます。  
  
 管理タスクまたは配置タスクのために作成したスクリプト ファイル (.rss) のバックアップを忘れないように注意してください。  
  
 使用しているカスタム拡張機能およびカスタム アセンブリのバックアップ コピーが存在していることを確認します。  

## <a name="next-steps"></a>次の手順

[レポート サーバー データベース](../../reporting-services/report-server/report-server-database-ssrs-native-mode.md)   
[Reporting Services 構成ファイル](../../reporting-services/report-server/reporting-services-configuration-files.md)   
[Rskeymgmt ユーティリティ](../../reporting-services/tools/rskeymgmt-utility-ssrs.md)   
[バックアップと復元によるデータベースのコピー](../../relational-databases/databases/copy-databases-with-backup-and-restore.md)   
[レポート サーバー データベースを管理する](../../reporting-services/report-server/administer-a-report-server-database-ssrs-native-mode.md)   
[暗号化キーの構成と管理](../../reporting-services/install-windows/ssrs-encryption-keys-manage-encryption-keys.md)  

その他の質問 [Reporting Services のフォーラムに質問してみてください](http://go.microsoft.com/fwlink/?LinkId=620231)
