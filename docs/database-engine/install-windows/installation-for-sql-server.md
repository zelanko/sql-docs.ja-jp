---
title: SQL Server のインストール | Microsoft Docs
ms.custom: ''
ms.date: 09/06/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
f1_keywords:
- sql13.portal.Installation.f1
helpviewer_keywords:
- installing SQL Server, initial installation
- installation [SQL Server]
- initial installation [SQL Server]
ms.assetid: edd75f68-dc62-4479-a596-57ce8ad632e5
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: a05419d31d7b3c8579afc824b9bb27f15aa9481d
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68892701"
---
# <a name="sql-server-installation"></a>SQL Server のインストール

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール ウィザードの 1 つの機能ツリーから、次のすべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントをインストールできます。  
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
-   [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]  
-   [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)]  
-   接続コンポーネント  
  
[!INCLUDE[ss2016](../../includes/sssql15-md.md)] 以降では、SQL Server 管理ツールがメイン機能ツリーからインストールされなくなりました。詳細については、「[SQL Server Management Studio (SSMS) のダウンロード](../../ssms/download-sql-server-management-studio-ssms.md)」を参照してください。  
  
各コンポーネントを個別にインストールするか、上記のコンポーネントを組み合わせて選択できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の最適なエディションおよびコンポーネントを選択するには、お使いのバージョンの SQL Server でサポートされている機能を参照してください。

- [[!INCLUDE[ss2017](../../includes/sssqlv14-md.md)] の各エディションとサポートされる機能](~/sql-server/editions-and-components-of-sql-server-2017.md)。  
- [[!INCLUDE[ss2016](../../includes/sssql15-md.md)] の各エディションとサポートされる機能](~/sql-server/editions-and-components-of-sql-server-2016.md)。  
- [[!INCLUDE[ss2014](../../includes/sssql14-md.md)] でサポートされる機能](https://technet.microsoft.com/library/cc645993(v=sql.120).aspx)
  
## <a name="in-this-section"></a>このセクションの内容  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール ウィザードを使用する場合でも、コマンド プロンプトから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をインストールする場合でも、セットアップ時には以下の手順を実行する必要があります。  
  
[SQL Server のインストール計画](../../sql-server/install/planning-a-sql-server-installation.md)  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]用にコンピューターを準備する方法について説明します。  
  
-   ハードウェアとソフトウェアの要件  
-   システム構成チェッカーの要件とブロックの問題  
-   セキュリティに関する注意点  
  
[SQL Server のインストール](../../database-engine/install-windows/install-sql-server.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインストール オプションについて説明します。  
  
[SQL Server セットアップのユーザー インターフェイス リファレンス](https://msdn.microsoft.com/library/183b5cdd-962e-41ca-8064-ea44f622c77d)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール ウィザードのインストール オプションについて説明します。  
  
[SQL Server のアップグレード](../../database-engine/install-windows/upgrade-sql-server.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]にアップグレードするためのオプションについて説明します。  
  
[SQL Server のアンインストール](../../sql-server/install/uninstall-sql-server.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] および [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]のアンインストール手順について説明します。  
  
[SQL Server フェールオーバー クラスターのインストール](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップ ドキュメントのこのセクションでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスターをインストールして構成する方法について説明します。  
  
[SQL Server のビジネス インテリジェンス機能のインストール](../../sql-server/install/install-sql-server-business-intelligence-features.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で Microsoft BI プラットフォームに含まれる機能には、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]、および分析データの作成または操作に使用されるいくつかのクライアント アプリケーションがあります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップ ドキュメントのこのセクションでは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] および [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]のインストール方法について説明します。  
  
## <a name="more-information"></a>詳細情報
[SharePoint を使用した SQL Server の BI 機能のインストール &#40;Power Pivot と Reporting Services&#41;](https://msdn.microsoft.com/library/3166107c-30c2-468e-bb1b-bb42b79b37c3)  
 このセクションでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能を SharePoint 環境でインストールする方法について説明します。 ここでは、特定のバージョンとエディションの SharePoint で使用できる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能を示します。 また、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint と Reporting Services を SharePoint モードでインストールする手順についても説明します。  
  
![ssrs_fyi_note](https://docs.microsoft.com/analysis-services/analysis-services/instances/install-windows/media/ssrs-fyi-note.png) 新しいサンプル データベース [Wide World importers](../../sample/world-wide-importers/wide-world-importers-documentation.md)をインストールします。 
  
[その他の SQL Server サンプルとサンプル データベース](https://sqlserversamples.codeplex.com/)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のサンプルおよびサンプル データベースをインストールして構成する方法について説明します。  
  
サポートされている [のバージョンのリンクと情報については、](https://msdn.microsoft.com/library/ff803383.aspx) SQL Server の Update Center [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]を参照してください。  
  
## <a name="see-also"></a>参照  
[SQL Server インストールの新機能](../../sql-server/install/what-s-new-in-sql-server-installation.md)   
[SQL Server のインストールに必要なハードウェアおよびソフトウェア](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  
