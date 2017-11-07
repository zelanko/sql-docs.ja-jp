---
title: "テーブル モデル パーティション (SSAS テーブル) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.asvs.ssms.partitions.partitionmgr.imbi.f1
ms.assetid: 041c269f-a229-4a41-8794-6ba4b014ef83
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 03122814773bd2e11b0ea1dc24b91b4c21a8f1a8
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="tabular-model-partitions-ssas-tabular"></a>テーブル モデル パーティション (SSAS テーブル)
  パーティションは、テーブルを論理的な部分に分割します。 各パーティションは、他のパーティションとは個別に処理 (更新) できます。 モデル作成時にあるモデルのために定義されたパーティションが、配置済みモデルで複製されます。 いったん配置されると、 **の** [パーティション] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ダイアログ ボックスまたはスクリプトを使用して、それらのパーティションを管理したり、新しいパーティションを作成したりできます。 このトピックでは、配置済みのテーブル モデル データベースにおけるパーティションについて説明します。 モデル作成時のパーティションの作成と管理の詳細については、「[パーティション (SSAS テーブル)](../../analysis-services/tabular-models/partitions-ssas-tabular.md)」を参照してください。  
  
 このトピックのセクション:  
  
-   [利点](#bkmk_benefits)  
  
-   [Permissions](#bkmk_permissions)  
  
-   [パーティションの処理](#bkmk_process_partitions)  
  
-   [並列処理](#bkmk_parallelProc)  
  
-   [関連タスク](#bkmk_related_tasks)  
  
##  <a name="bkmk_benefits"></a> 利点  
 効率的なモデル設計によるパーティションの活用によって、不必要な処理とその後の Analysis Services サーバーでのプロセッサ負荷が排除されます。同時に、データ ソースの大部分の最新のデータを反映できる頻度でデータが処理され更新されるようになります。  
  
 たとえば、あるテーブル モデルに現会計年度 (2011 年度) の売上データと過去の各会計年度の売上データを含む売上テーブルがあるとします。 モデルの売上テーブルは次の 3 つのパーティションで構成されます。  
  
|パーティション|データ ソース|  
|---------------|---------------|  
|Sales2011|現会計年度|  
|Sales2010-2001|会計年度 2001、2002、2003、2004、2005、2006。 2007、2008、2009、2010|  
|SalesOld|過去 10 年より前の全会計年度。|  
  
 現会計年度である 2011 年度の新しい売上データは追加されます。このデータを現会計年度の売上データ分析に正確に反映させるためには、データを毎日処理する必要があります。そのため、Sales2011 パーティションは毎晩処理されます。  
  
 Sales2010-2001 パーティションのデータは毎晩処理する必要がありません。ただし、製品の返品などの調整によって過去 10 年間の会計年度の売上データも変化する場合があるため、定期的に処理する必要があります。そのため、Sales2010-2001 パーティションのデータは毎月処理されます。 SalesOld パーティションのデータは変化しないため、1 年に 1 回処理されます。  
  
 2012 年度になると、新しい Sales2012 というパーティションがモードの売上テーブルに追加されます。 Sales2011 パーティションは、Sales2010-2001 パーティションとマージして、Sales2011-2002 という名前に変更することができます。 2001 年度のデータは、新しい Sales2011-2002 パーティションから削除され、SalesOld パーティションに移動されます。 次に、変更を反映させるためにすべてのパーティションが処理されます。  
  
 組織のテーブル モデルにパーティション分割の方法をどのように実装するかは、特定のモデル データ処理ニーズと使用可能なリソースによって大きく左右されます。  
  
##  <a name="bkmk_permissions"></a> Permissions  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でパーティションを作成、管理、および処理するには、適切な Analysis Services 権限がセキュリティ ロールで定義されている必要があります。 各セキュリティ ロールには次のいずれかの権限があります。  
  
|権限|アクション|  
|----------------|-------------|  
|管理者|読み取り、処理、作成、コピー、マージ、削除|  
|[処理]|読み取り、処理|  
|[読み取り専用]|読み取り|  
  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] を使用してモデル作成時にロールを作成する方法の詳細については、「[ロール (SSAS テーブル)](../../analysis-services/tabular-models/roles-ssas-tabular.md)」を参照してください。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して配置済みテーブル モデル ロールのロール メンバーを管理する方法の詳細については、「[テーブル モデル ロール (SSAS テーブル)](../../analysis-services/tabular-models/tabular-model-roles-ssas-tabular.md)」を参照してください。  
  
##  <a name="bkmk_parallelProc"></a> 並列処理  
Analysis Services には、処理パフォーマンスが向上する 2 つまたは複数のパーティションを持つテーブルへの並行処理が含まれています。 並行処理には構成設定はありません (メモを参照)。 テーブルを処理する場合、または同じテーブルに複数のパーティションを選択して処理する場合、既定で並列処理が行われます。 テーブルのパーティションを個別に処理することもできます。  
  
> [!NOTE]  
>  更新操作を順次実行するか並列して実行するかを指定するには、 **maxParallism** プロパティ オプションで [Sequence コマンド (TMSL)](../../analysis-services/tabular-models-scripting-language-commands/sequence-command-tmsl.md)を指定します。

> [!NOTE]  
>  再エンコードが検出されると、並列処理が原因で、システム リソースの使用量が増える場合があります。 これは、同時に行われる新しいエンコードにより、、複数のパーティションの操作を中断し、再開する必要があるためです。  
  
##  <a name="bkmk_process_partitions"></a> パーティションの処理  
 **の** [パーティション] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] ダイアログ ボックスを使用するか、スクリプトを使用すると、パーティションの処理 (更新) を他のパーティションに影響を与えずに行うことができます。 処理には次のオプションがあります。  
  
|モード|Description|  
|----------|-----------------|  
|既定の処理|パーティション オブジェクトの処理状態を検出して、未処理または部分的に処理されたパーティション オブジェクトを完全に処理された状態にするために必要な処理を実行します。 空のテーブルとパーティションのデータが読み込まれ、階層、計算列、およびリレーションシップが構築または再構築されます。|  
|完全処理|パーティション オブジェクトとそこに含まれているすべてのオブジェクトを処理します。 既に処理されたオブジェクトに対して完全処理を実行すると、そのオブジェクト内のすべてのデータが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によって削除されてから、オブジェクトが処理されます。 この種の処理は、構造上の変更をオブジェクトに加えた場合に必要となります。|  
|データの処理|階層またはリレーションシップを再構築したり、計算列とメジャーを再計算したりせずに、パーティションまたはテーブルにデータを読み込みます。|  
|消去の処理|パーティションからすべてのデータを削除します。|  
|追加の処理|パーティションを新しいデータで増分更新します。|  
  
##  <a name="bkmk_related_tasks"></a> 関連タスク  
  
|タスク|Description|  
|----------|-----------------|  
|[テーブル モデル パーティションの作成および管理 (SSAS テーブル)](../../analysis-services/tabular-models/create-and-manage-tabular-model-partitions-ssas-tabular.md)|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用して配置済みテーブル モデルでパーティションを作成および管理する方法について説明します。|  
|[テーブル モデル パーティションの処理 (SSAS テーブル)](../../analysis-services/tabular-models/process-tabular-model-partitions-ssas-tabular.md)|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用して配置済みテーブル モデルでパーティションを処理する方法について説明します。|  
  
  

