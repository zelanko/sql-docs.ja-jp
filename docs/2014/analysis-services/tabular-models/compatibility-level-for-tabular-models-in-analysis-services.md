---
title: 互換性レベル (SSAS 表形式 SP1) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.versioncompat.f1
ms.assetid: 8943d78d-4a73-4be8-ad14-3d428f5abd06
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 57a1e67db8bcbf17dc964f7341df25a396c36ad0
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/25/2020
ms.locfileid: "66067599"
---
# <a name="compatibility-level-ssas-tabular-sp1"></a>互換性レベル (SSAS テーブル SP1)
  新しいテーブルモデルプロジェクトを作成するとき、既存のテーブルモデルプロジェクトをアップグレードするとき、既存の配置済みテーブルモデルデータベースをアップグレードするとき、または PowerPivot ブックをインポートするときに、*互換性レベル*を指定できます。  
  
## <a name="compatibility-level"></a>互換性レベル  
 通常は、実稼働コンピューターにインストールする前に、開発用コンピューターとテスト用コンピューターに新しいバージョンとサービス パックをインストールします。 このような場合は、新しいテーブル モデル プロジェクトと実稼働環境に既に配置されているテーブル モデル プロジェクトの両方に対する互換性レベルの設定について理解することが重要です。  
  
 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] の Analysis Services インスタンスは、次の互換性レベル (データベース バージョン) をサポートします。  
  
-   SQL Server 2012 (1100)  
  
-   SQL Server 2012 SP1 (1103)  
  
-   SQL Server 2014 (1103)  
  
### <a name="set-compatibility-level-when-creating-a-new-tabular-model-project"></a>新しいテーブル モデル プロジェクトを作成するときに互換性レベルを設定する  
 SQL Server Data Tools (SSDT) で新しいテーブルモデルプロジェクトを作成するときに、[**新しい表形式プロジェクトのオプション**] ダイアログで互換性レベルを指定できます。 作成した新しいプロジェクトの配置先として、[!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] 以降の Analysis Services インスタンス、または SQL Server 2012 Analysis Services インスタンス (Service Pack 1 なし) を選択できます。  
  
 **[今後、このメッセージを表示しない]** オプションを選択することで、既定の互換性レベルを指定することもできます。 以降、すべてのプロジェクトで、指定した互換性レベルが使用されます。 既定の互換性レベルは、SSDT の [オプション] で変更できます。  
  
### <a name="upgrade-an-existing-tabular-model-project-to-1103-compatibility-level"></a>既存のテーブル モデル プロジェクトを 1103 互換性レベルにアップグレードする  
 [モデルの**プロパティ**] ウィンドウの [**互換性レベル**] プロパティを[!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]使用して、1103以降をインストールする前に、SSDT で作成したテーブルモデルプロジェクトをアップグレードすることができます。 テーブル モデル プロジェクトをアップグレードするには、SSDT をインストールするコンピューターに [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] 以降がインストールされ、ワークスペース データベースが存在する Analysis Services インスタンス上にも [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] 以降がインストールされている必要があります。 以前のバージョンにダウングレードすることはできません。  
  
### <a name="upgrade-a-deployed-tabular-model-database-to-1103-compatibility-level"></a>配置済みテーブル モデル データベースを 1103 互換性レベルにアップグレードする  
 **データベースプロパティ**の [**互換性レベル**] プロパティを使用すると、既存の配置済みテーブルモデルデータベースを SQL Server Management Studio (SSMS) で互換性のあるデータベースバージョン1103にアップグレードできます。 アップグレードするには、SQL Server Analysis Services インスタンスがインストールされるコンピューターに [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] 以降がインストールされている必要があります。 配置済みのテーブル モデル データベースを以前のバージョンのインスタンスにダウングレードすることはできません。  
  
### <a name="import-from-powerpivot"></a>PowerPivot からのインポート  
 新しいテーブル モデル プロジェクトを PowerPivot からインポートすることで作成する場合は、互換性レベルを既定の互換性レベルにアップグレードする (SSDT で構成済みの場合) か、PowerPivot ワークブックに既に指定されている互換性のままにするかを指定できます。  
  
### <a name="check-compatibility-level-for-a-tabular-model-database-in-ssms"></a>SSMS のテーブル モデル データベースの互換性レベルを確認する  
 SSMS のテーブルモデルデータベースの互換性レベルを確認するには、[**データベースのプロパティ**] の [**互換性レベル**] プロパティを表示します (の[!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]新機能)。  
  
### <a name="check-supported-compatibility-level-for-an-analysis-services-instance-in-ssms"></a>Analysis Services インスタンスでサポートされる互換性レベルを SSMS で確認する  
 SSMS でサポートされている互換性レベルを確認するには、 **Analysis Services のプロパティ**の**情報**ページ (の[!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]新機能) で [サポートされて**いる互換性レベル**] プロパティを表示します。 サポートされる互換性レベル 1103 は、SQL Server SP1 以降がインストールされていることを示します。 サポートされる互換性レベルは変更できません。  
  
  
