---
title: SQL Server をインストールする | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: quickstart
helpviewer_keywords:
- AdventureWorks sample database
- installing SQL Server, preparing to install
- installation [SQL Server]
ms.assetid: 0300e777-d56b-4d10-9c33-c9ebd2489ee5
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: d790ef532a66bf7f8e34f69b9f982bef3416d0a1
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68893986"
---
# <a name="install-sql-server"></a>SQL Server をインストールする
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
 
 [!INCLUDE[sssql15](../../includes/sssql15-md.md)] 以降、[!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] は 64 ビット アプリケーションでのみ使用できるようになりました。 SQL Server の入手およびインストールの方法に関する重要な詳細情報を次に示します。

## <a name="installation-details"></a>インストールの詳細
  
*  **オプション**: インストール ウィザード、コマンド プロンプト、または sysprep でインストールします。
 
*  **要件**: インストールする前に、「[SQL Server のインストール計画](../../sql-server/install/planning-a-sql-server-installation.md)」に記載されているインストール要件、システム構成チェック、セキュリティ上の考慮事項を確認してください。 

* **プロセス**: インストール プロセスの完全な手順については、「[SQL Server のインストール](../../database-engine/install-windows/installation-for-sql-server-2016.md)」を参照してください。

* **サンプル データベースとサンプル コード**: 
    * これらは、既定では SQL Server セットアップの一環としてインストールされません。 
    * SQL Server の Express 以外のエディションをインストールするには、[GitHub](https://github.com/Microsoft/sql-server-samples) を参照してください。
    

## <a name="get-the-installation-media"></a>インストール メディアを入手する

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

## <a name="how-to-install-includessnoversionincludesssnoversion-mdmd"></a>[!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] のインストール方法
 
|[タイトル]|[説明]|  
|-----------|-----------------|  
|[Server Core に [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] をインストールする](../../database-engine/install-windows/install-sql-server-on-server-core.md)|Windows Server Core への [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] のインストールについては、この記事をご覧ください。|  
|[システム構成チェッカーの検査パラメーター](../../database-engine/install-windows/check-parameters-for-the-system-configuration-checker.md)|システム構成チェッカー (SCC) の機能について説明します。|  
|[インストール ウィザードから [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] をインストールする &#40;セットアップ&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)|インストール ウィザードを使った [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の一般的なインストール手順に関する記事です。|  
|[コマンド プロンプトからの [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] のインストール](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)|自動セットアップを実行するためのサンプルの構文とインストール パラメーターを提供する手順に関する記事です。|  
|[構成ファイルを使用した [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] のインストール](../../database-engine/install-windows/install-sql-server-2016-using-a-configuration-file.md)|構成ファイルからセットアップを実行するためのサンプルの構文とインストール パラメーターを提供する手順に関する記事です。|  
|[SysPrep を使用して [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] をインストールする](../../database-engine/install-windows/install-sql-server-using-sysprep.md)|SysPrep からセットアップを実行するためのサンプルの構文とインストール パラメーターを提供する手順に関する記事です。|  
|[[!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] のインスタンスへの機能の追加 &#40;セットアップ&#41;](../../database-engine/install-windows/add-features-to-an-instance-of-sql-server-2016-setup.md)|[!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] の既存のインスタンスのコンポーネントを更新する手順に関する記事です。|  
|[失敗した [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] のインストールを修復する](../../database-engine/install-windows/repair-a-failed-sql-server-installation.md)|壊れた [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] を修復する手順に関する記事です。|  
|[SQL Server のスタンドアロン インスタンスをホストするコンピューターの名前変更](../../database-engine/install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md)|sys.servers に格納されているシステム メタデータを更新する手順に関する記事です。|  
|[[!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] サービス更新プログラムをインストールする](../../database-engine/install-windows/install-sql-server-servicing-updates.md)|[!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] の更新プログラムのインストール手順に関する記事です。|  
|[SQL Server セットアップ ログ ファイルの表示と読み取り](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)|セットアップ ログ ファイルでエラーをチェックする手順に関する記事です。|  
|[SQL Server のインストールの検証](../../database-engine/install-windows/validate-a-sql-server-installation.md)|コンピューターにインストールされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンおよび [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の機能を確認するための SQL の検出レポートの使用方法を確認します。|  
  
  
## <a name="how-to-install-individual-components"></a>個々のコンポーネントをインストールする方法  
  
|トピック|[説明]|  
|-----------|-----------------|  
|[SQL Server データベース エンジンのインストール](../../database-engine/install-windows/install-sql-server-database-engine.md)|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]をインストールして構成する方法について説明します。|  
|[SQL Server レプリケーションのインストール](../../database-engine/install-windows/install-sql-server-replication.md)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レプリケーションをインストールして構成する方法について説明します。|  
|[分散再生のインストール - 概要](../../tools/distributed-replay/install-distributed-replay-overview.md)|分散再生の機能のインストールに関する記事の一覧を示します。|  
|[SSMS を使用した SQL Server 管理ツールのインストール](https://msdn.microsoft.com/library/af68d59a-a04d-4f23-9967-ad4ee2e63381)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理ツールをインストールして構成する方法について説明します。|  
|[SQL Server PowerShell のインストール](../../database-engine/install-windows/install-sql-server-powershell.md)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell コンポーネントのインストールに関する考慮事項について説明します。|  
  

## <a name="how-to-configure-sql-server"></a>SQL Server を構成する方法  
  
|トピック|[説明]|  
|-----------|-----------------|  
|[SQL Server のアクセスを許可するための Windows ファイアウォールの構成](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)|この記事では、ファイアウォール構成の概要を示し、Windows ファイアウォールを構成する方法について説明します。|  
|[SQL Server アクセス用のマルチホーム コンピューターの構成](../../sql-server/install/configure-a-multi-homed-computer-for-sql-server-access.md)|この記事では、マルチホーム環境内の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスへのネットワーク接続用に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] とセキュリティが強化された Windows ファイアウォールを構成する方法について説明します。|  
|[Analysis Services のアクセスを許可するための Windows ファイアウォールの構成](https://docs.microsoft.com/analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access)|この記事で示す手順に従って、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] または [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint へのアクセスを許可するためにポートとファイアウォールの両方の設定を構成できます。|  
  
## <a name="related-sections"></a>関連項目  
[[!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] の各エディションとサポートされる機能](../../sql-server/editions-and-supported-features-for-sql-server-2016.md)  
[[!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] のビジネス インテリジェンス機能のインストール](../../sql-server/install/install-sql-server-business-intelligence-features.md)  
  [SQL Server フェールオーバー クラスターのインストール](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md)  
 
  
## <a name="see-also"></a>参照  

[SQL Server のインストール計画](../../sql-server/install/planning-a-sql-server-installation.md)   
 [[!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] へのアップグレード](../../database-engine/install-windows/upgrade-sql-server.md)   
 [[!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] のアンインストール](../../sql-server/install/uninstall-sql-server.md)   
 [高可用性ソリューション &#40;SQL Server&#41;](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md)  
  
  
