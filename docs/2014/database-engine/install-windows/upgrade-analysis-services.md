---
title: Analysis Services のアップグレード | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- upgrading databases
- databases [Analysis Services], upgrading
- installing Analysis Services, side-by-side installations
- Analysis Services upgrades
- Analysis Services upgrades, about upgrading Analysis Services
- SSAS, database migration
- upgrading Analysis Services
- installing Analysis Services, upgrading
- SSAS, upgrading
ms.assetid: a131d329-386e-4470-aaa9-ffcde4e5ec0c
author: Minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cdd9e34e57694efc1234a2f0245833596644cb73
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68889184"
---
# <a name="upgrade-analysis-services"></a>Analysis Services のアップグレード
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をアップグレードします。 SharePoint モードでのアップグレード[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の詳細については、「 [Upgrade PowerPivot for SharePoint](upgrade-power-pivot-for-sharepoint.md)」を参照してください。 既存の SQL Server インスタンスのアップグレードの詳細については、[インストールウィザードを使用した SQL Server 2014 へのアップグレード &#40;のセットアップ&#41;を](upgrade-sql-server-using-the-installation-wizard-setup.md)参照してください。  
  
## <a name="known-upgrade-issues"></a>アップグレードに関する既知の問題  
 に[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]アップグレードする前に、次の内容を確認してください。  
  
-   [SQL Server 2014 リリース ノート](https://go.microsoft.com/fwlink/?LinkID=296445).  
  
-   廃止、非[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]推奨、または変更された機能の詳細については、「 [Analysis Services 旧バージョン](https://docs.microsoft.com/analysis-services/analysis-services-backward-compatibility)との互換性」を参照してください。  
  
## <a name="pre-upgrade-checklist"></a>アップグレード前のチェック リスト  
 アップグレードの前に、次の情報を確認してください。  
  
-   [サポートされているバージョンとエディションのアップグレード](supported-version-and-edition-upgrades.md)  
  
-   [SQL Server 2014 のインストールに必要なハードウェアおよびソフトウェア](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  
  
-   [システム構成チェッカーの検査パラメーター](check-parameters-for-the-system-configuration-checker.md)  
  
-   [SQL Server インストールにおけるセキュリティの考慮事項](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
-   [Analysis Services データベースのバックアップと復元](https://docs.microsoft.com/analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases)  
  
-   [アップグレード アドバイザーを使用したアップグレードの準備](../../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)  
  
## <a name="upgrading-analysis-services"></a>Analysis Services のアップグレード  
 サーバーおよびデータをアップグレードするには、複数の方法から選択できます。  
  
-   **インプレースアップグレードで**は、既存のプログラムファイルがプログラム[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]ファイルに置き換えられます。 データベースは、同じ場所に残ります。 プログラム フォルダーは、新しい名前を反映して更新されます。  
  
-   **サイドバイサイドアップグレード**は、既存の Analysis Services インスタンスがある[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]同じコンピューター上のの新規インストールです。 以前のバージョンを今後使用しない場合は、データベースを同じコンピューター上の新しいインスタンスへ移動し、以前のバージョンをアンインストールできます。  
  
-   Analysis Services を新しいハードウェア上にインストールし、既存のデータベースをそのサーバーへ移行することもできます。  
  
## <a name="in-place-upgrade"></a>インプレース アップグレード  
 の既存の[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]インスタンスをに[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]アップグレードすることができます。また、アップグレードプロセスの一環として、既存のデータベースが古いインスタンスから新しいインスタンスに自動的に移行されます。 メタデータおよびバイナリ データは 2 つのバージョン間で互換性があるため、アップグレード後もそのまま使用できます。手動でデータを移行する必要はありません。  
  
 既存のインスタンスをアップグレードするには、セットアップを実行し、新しいインスタンスの名前として既存のインスタンス名を指定します。  
  
## <a name="upgrading-databases"></a>データベースのアップグレード  
 以前のバージョンの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で作成されたデータベースは、アップグレード後のサーバー上で、古いデータベース互換性レベル設定で実行されます。 次のバージョンで作成されたデータベースのデータベース互換性レベルは 105 になります。 新しいデータベースの互換性レベルを必要とする機能を使用する場合は、互換性レベルを変更できます。 それ以外の場合は、元の設定を使用して、アップグレード後のサーバー上でデータベースを実行できます。 詳細については、「[多次元データベースの互換性レベルを設定する &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services)」を参照してください。  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]  
  
## <a name="see-also"></a>参照  
 [SQL Server 2014 の各エディションがサポートする機能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [SQL Server インストールの計画](../../sql-server/install/planning-a-sql-server-installation.md)   
 [Microsoft OLAP アーキテクチャについて](https://docs.microsoft.com/analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-architecture)   
 [PowerPivot for SharePoint のアップグレード](upgrade-power-pivot-for-sharepoint.md)   
 [多次元およびデータマイニングモードでの Analysis Services のインストール](../../sql-server/install/install-analysis-services-in-multidimensional-and-data-mining-mode.md)   
 [PowerPivot for SharePoint 2010 のインストール](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
