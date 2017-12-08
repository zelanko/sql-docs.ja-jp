---
title: "パーティション (SSAS テーブル) |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/10/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 708b9bdf-8c0b-4476-809a-8f616be23a58
caps.latest.revision: "20"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: ceaff43e4f0f5d2b1901c98b026d37af9ba89383
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="partitions"></a>パーティション
  パーティションは、テーブルを論理的な部分に分割します。 各パーティションは、他のパーティションとは個別に処理 (更新) できます。 モデル作成時に SSDT の [パーティション] ダイアログ ボックスを使用して作成されたパーティションは、モデル ワークスペース データベースに適用されます。 モデルが配置されたときに、モデル ワークスペース データベースに定義されたパーティションが配置済み model データベースで複製されます。 さらに、作成し、SSMS の [パーティション] ダイアログ ボックスを使用して、配置済みモデル データベースのパーティションを管理することができます。  このトピックで提供される情報には、SSDT のパーティション マネージャー ダイアログ ボックスを使用してモデルを作成中に作成されたパーティションがについて説明します。 作成して、配置済みモデルのパーティションの管理については、次を参照してください。[作成および表形式モデル パーティションの管理](../../analysis-services/tabular-models/create-and-manage-tabular-model-partitions-ssas-tabular.md)です。  
  
##  <a name="bkmk_benefits"></a> 利点  
 テーブル モデルでは、パーティションがテーブルを論理パーティション オブジェクトに分割します。 各パーティションは、他のパーティションとは個別に処理できます。 たとえば、あるテーブルにはめったに変更されないデータを含む所定の行セットが含まれている場合がありますが、他の行セットには頻繁に変更されるデータがあるとします。 このような場合は、データの一部を処理するときにデータ全体を処理する必要はありません。 パーティションを使用すると、めったに処理されないデータから頻繁に処理する必要のあるデータ部分を分割できます。  
  
 効率的なモデル設計によるパーティションの活用によって、不必要な処理とその後の Analysis Services サーバーでのプロセッサ負荷が排除されます。同時に、データ ソースの大部分の最新のデータを反映できる頻度でデータが処理され更新されるようになります。 モデル作成時にパーティションをどのように実装し利用するかは、配置済みモデルでパーティションがどのように実装され利用されているかによって大幅に異なる場合があります。 モデル作成段階では、最終的に配置済みモデルに入るデータのサブセットのみを操作している可能性があるということに注意してください。  
  
### <a name="processing-partitions"></a>パーティションの処理  
 配置済みモデルは、処理には、SSMS を使用するか、process コマンドを含め、処理オプションと設定を指定するスクリプトを実行して行われます。 SSDT を使用してモデルを作成するときに、[モデル] メニューまたはツールバーからプロセス コマンドを使用して処理操作を実行できます。 処理操作は、パーティション、テーブル、またはすべてに対して指定できます。  
  
 処理操作を実行するときは、データ接続を使用してデータ ソースへの接続が行われます。 モデル テーブルに新しいデータがインポートされると、各テーブルに対してリレーションシップと階層が再構築され、計算済みの列およびメジャーでの計算が再計算されます。  
  
 テーブルを論理パーティションにさらに分割することで、各パーティション内のどのデータを、どのタイミングで、どのように処理するかを、選択的に決めることができます。 モデルを配置する場合は、パーティションの処理は、ssms で、[パーティション] ダイアログ ボックスを使用して手動で完了できるまたはプロセス コマンドを実行するスクリプトを使用しています。  
  
### <a name="partitions-in-the-model-workspace-database"></a>モデル ワークスペース データベースのパーティション  
 新しいパーティションを作成、編集、マージ、か SSDT で Partition Manager を使用してパーティションを削除します。 作成中のモデルの互換性レベルによってパーティション マネージャーでは、2 つのモード テーブル、行、およびパーティションの列を選択します M クエリを使用して表形式の 1400 モデルのパーティションが定義されているかを開くにはデザイン モードを使用することができます。クエリ エディターです。 表形式の 1100、1103、1200 モデルでは、使用テーブル プレビュー モードと SQL クエリ モードです。 
  
### <a name="partitions-in-a-deployed-model-database"></a>配置済みモデル データベースのパーティション  
 モデルを配置するときに、配置済みモデル データベース用のパーティションは、SSMS でデータベース オブジェクトとして表示されます。 ことができますを作成、編集、マージ、および SSMS の [パーティション] ダイアログ ボックスを使用して配置済みモデル用のパーティションを削除します。 SSMS で、配置済みモデルのパーティションを管理するには、このトピックの範囲外です。 詳細については、SSMS でのパーティションを管理する、次を参照してください。[作成および表形式モデル パーティションの管理](../../analysis-services/tabular-models/create-and-manage-tabular-model-partitions-ssas-tabular.md)です。  
  
##  <a name="bkmk_related_tasks"></a> Related tasks  
  
|トピック|Description|  
|-----------|-----------------|  
|[ワークスペース データベースのパーティションの作成と管理](../../analysis-services/tabular-models/create-and-manage-partitions-in-the-workspace-database-ssas-tabular.md)|作成し、SSDT で Partition Manager を使用して、モデル ワークスペース データベースでパーティションを管理する方法について説明します。|  
|[ワークスペース データベースでパーティションの処理](../../analysis-services/tabular-models/process-partitions-in-the-workspace-databse-ssas-tabular.md)|モデル ワークスペース データベースでのパーティションの処理 (更新) 方法について説明します。|  
  
## <a name="see-also"></a>参照  
 [DirectQuery モード](../../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)   
 [データの処理](../../analysis-services/tabular-models/process-data-ssas-tabular.md)  
  
  
