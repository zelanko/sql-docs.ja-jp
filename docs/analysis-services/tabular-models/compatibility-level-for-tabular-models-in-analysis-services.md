---
title: "Analysis services 表形式モデルの互換性レベル |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/16/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.asvs.bidtoolset.versioncompat.f1
ms.assetid: 8943d78d-4a73-4be8-ad14-3d428f5abd06
caps.latest.revision: "27"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: d194cdfa2771b96f2ae1880f474b8a0107e0b67c
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="compatibility-level-for-analysis-services-tabular-models"></a>Analysis Services 表形式モデルの互換性レベル
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]

  *互換性レベル*Analysis Services エンジンでのリリースに固有の動作を指します。 たとえば、DirectQuery と表形式オブジェクトのメタデータは、互換性レベルによって異なる実装を持ちます。 一般に、サーバーでサポートされている最新の互換性レベルを選択してください。

  **最新の互換性レベルが 1400** 
  
主な機能を 1400 互換性レベルは次のとおりです。

*  データ接続、表形式モデルにインポート新しいインフラストラクチャ TOM Api および TMSL スクリプトをサポートします。 これにより、Azure Blob ストレージなどの他のデータ ソースがサポートされます。 今後の更新プログラムにはで追加のデータ ソースがあることが含まれています。
*  データ変換をデータの取得と M の式を使用してデータのマッシュ アップ機能します。
*  メジャーでは、集約されたレポートから詳細なデータを Microsoft Excel ドリル ダウンなどの BI ツールを有効にする、DAX 式で、詳細行プロパティできるようになりました。 たとえば、エンドユーザーは、地域と月の売上合計を表示するときに、関連付けられている注文の詳細表示できます。 
*  オブジェクト レベルのセキュリティをそこに含まれるデータに加え、テーブルと列の名前。
*  不規則階層のサポートを強化します。
*  パフォーマンスと機能強化を監視します。

  
## <a name="supported-compatibility-levels-by-version"></a>バージョンでサポートされる互換性レベル
  
|||  
|-|-|- 
|**互換性レベル**|**サーバーのバージョン**| 
|1400|Azure Analysis Services、SQL Server 2017 |  
|1200|Azure Analysis Services、SQL Server 2017、SQL Server 2016| 
|1103|SQL Server 2017 *、SQL Server 2016、SQL Server 2014、SQL Server 2012 SP1|  
|1100|SQL Server 2017 *、SQL Server 2016、SQL Server 2014、SQL Server 2012 SP1、SQL Server 2012| 

\*SQL Server 2017 では、1100 と 1103 互換性レベルが廃止されました。
  
## <a name="set-compatibility-level"></a>互換性レベルの設定 
 新しいテーブル モデル プロジェクトで SQL Server Data Tools (SSDT) を作成するときに互換性レベルを指定できます、**表形式モデル デザイナー**ダイアログ。 
  
 ![ssas_tabularproject_compat1200](../../analysis-services/tabular-models/media/ssas-tabularproject-compat1200.png)  
  
 選択した場合、**今後このメッセージを表示しない**オプション、それ以降のすべてのプロジェクトには、既定値として指定した互換性レベルが使用されます。 SSDT の既定の互換性レベルは、 **[ツール]** > **[オプション]**の順に選択すると変更できます。  
  
 SSDT で表形式モデル プロジェクトをアップグレードするには、設定、**互換性レベル**モデル内のプロパティ**プロパティ**ウィンドウです。 注意して、互換性レベルのアップグレードは元に戻すことはありません。
  
## <a name="check-compatibility-level-for-a-database-in-ssms"></a>SSMS でデータベースの互換性レベルを確認する  
 SSMS では、データベース名を右クリックして >**プロパティ** > **互換性レベル**です。  
  
## <a name="check-supported-compatibility-level-for-a-server-in-ssms"></a>SSMS でサーバーのサポートされる互換性レベルを確認する  
 SSMS では、サーバー名を右クリックして >**プロパティ** > **サポートされる互換性レベル**です。  
  
 このプロパティは、サーバーで実行されるデータベースの最も高い互換性レベルを指定します。 サポートされる互換性レベルは読み取り専用であり、変更できません。  
  
## <a name="see-also"></a>参照  
 [多次元データベースの互換性レベル](../../analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services.md)   
 [Analysis Services の新機能](../../analysis-services/what-s-new-in-analysis-services.md)   
 [新しいテーブル モデル プロジェクトを作成します。](../../analysis-services/tabular-models/create-a-new-tabular-model-project-analysis-services.md)  
  
  
