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
ms.openlocfilehash: 8bbec3cd552434070d76913f72812b302440bcdb
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62775033"
---
# <a name="upgrade-analysis-services"></a>Analysis Services のアップグレード
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をアップグレードします。 アップグレードに関する詳細情報の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]SharePoint モードを参照してください。 [PowerPivot for SharePoint のアップグレード](upgrade-power-pivot-for-sharepoint.md)します。 既存の SQL Server のアップグレードの詳細については、インスタンスは、「[インストール ウィザードを SQL Server 2014 を使用するアップグレード&#40;セットアップ&#41;](upgrade-sql-server-using-the-installation-wizard-setup.md)します。  
  
## <a name="known-upgrade-issues"></a>アップグレードに関する既知の問題  
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]にアップグレードする前に、次のトピックを確認してください。  
  
-   [SQL Server 2014 リリース ノート](https://go.microsoft.com/fwlink/?LinkID=296445).  
  
-   これについては、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]の特徴および機能廃止、非推奨、または変更を参照してください[Analysis Services の旧バージョンとの互換性](../../analysis-services/analysis-services-backward-compatibility.md)します。  
  
## <a name="pre-upgrade-checklist"></a>アップグレード前のチェック リスト  
 アップグレードの前に、次の情報を確認してください。  
  
-   [サポートされているバージョンとエディションのアップグレード](supported-version-and-edition-upgrades.md)  
  
-   [SQL Server 2014 のインストールに必要なハードウェアおよびソフトウェア](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  
  
-   [システム構成チェッカーの検査パラメーター](check-parameters-for-the-system-configuration-checker.md)  
  
-   [SQL Server インストールにおけるセキュリティの考慮事項](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
-   [Analysis Services データベースのバックアップと復元](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
-   [アップグレード アドバイザーを使用したアップグレードの準備](../../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)  
  
## <a name="upgrading-analysis-services"></a>Analysis Services のアップグレード  
 サーバーおよびデータをアップグレードするには、複数の方法から選択できます。  
  
-   **、インプレース アップグレード**、既存のプログラム ファイルが置換[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]プログラム ファイル。 データベースは、同じ場所に残ります。 プログラム フォルダーは、新しい名前を反映して更新されます。  
  
-   A**サイド バイ サイド アップグレード**の新しいインストールである[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]既存の Analysis Services インスタンスがある同じコンピューターにします。 以前のバージョンを今後使用しない場合は、データベースを同じコンピューター上の新しいインスタンスへ移動し、以前のバージョンをアンインストールできます。  
  
-   Analysis Services を新しいハードウェア上にインストールし、既存のデータベースをそのサーバーへ移行することもできます。  
  
## <a name="in-place-upgrade"></a>インプレース アップグレード  
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の既存のインスタンスを [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] and, as part of the upgrade process, auの既存のインスタンスをmatically migrate existing databases from the old instance の既存のインスタンスを the new instance. メタデータおよびバイナリ データは 2 つのバージョン間で互換性があるため、アップグレード後もそのまま使用できます。手動でデータを移行する必要はありません。  
  
 既存のインスタンスをアップグレードするには、セットアップを実行し、新しいインスタンスの名前として既存のインスタンス名を指定します。  
  
## <a name="upgrading-databases"></a>データベースのアップグレード  
 以前のバージョンの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で作成されたデータベースは、アップグレード後のサーバー上で、古いデータベース互換性レベル設定で実行されます。 次のバージョンで作成されたデータベースのデータベース互換性レベルは 105 になります。 新しいデータベースの互換性レベルを必要とする機能を使用する場合は、互換性レベルを変更できます。 それ以外の場合は、元の設定を使用して、アップグレード後のサーバー上でデータベースを実行できます。 詳細については、次を参照してください。[多次元データベースの互換性レベル設定&#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services.md)します。  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]  
  
## <a name="see-also"></a>参照  
 [SQL Server 2014 のエディションでサポートされる機能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [SQL Server のインストール計画](../../sql-server/install/planning-a-sql-server-installation.md)   
 [Microsoft OLAP アーキテクチャをについてください。](../../analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-architecture.md)   
 [PowerPivot for SharePoint をアップグレードします。](upgrade-power-pivot-for-sharepoint.md)   
 [多次元モードおよびデータ マイニング モードでの Analysis Services のインストール](../../sql-server/install/install-analysis-services-in-multidimensional-and-data-mining-mode.md)   
 [PowerPivot for SharePoint 2010 のインストール](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
