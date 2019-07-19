---
title: Analysis Services 表形式モデルでパーティション |Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5d26b1b1558ca546fb47660488b15dc777c5ad87
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68162718"
---
# <a name="partitions"></a>[メジャー グループ]
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  パーティションは、テーブルを論理的な部分に分割します。 各パーティションは、他のパーティションとは個別に処理 (更新) できます。 モデル作成時に SSDT でのパーティション ダイアログ ボックスを使用して作成されたパーティションは、モデル ワークスペース データベースに適用されます。 モデルが配置されたときに、モデル ワークスペース データベースに定義されたパーティションが配置済み model データベースで複製されます。 さらに作成し、SSMS でのパーティション ダイアログ ボックスを使用して配置済みモデル データベースのパーティションを管理できます。  このトピックで提供される情報には、SSDT でのパーティション マネージャー ダイアログ ボックスを使用してモデルの作成時に作成されたパーティションがについて説明します。 配置済みモデルのパーティション作成と管理については、次を参照してください。[の作成とテーブル モデル パーティションの管理](../../analysis-services/tabular-models/create-and-manage-tabular-model-partitions-ssas-tabular.md)します。  
  
##  <a name="bkmk_benefits"></a> 利点  
 テーブル モデルでは、パーティションがテーブルを論理パーティション オブジェクトに分割します。 各パーティションは、他のパーティションとは個別に処理できます。 たとえば、あるテーブルにはめったに変更されないデータを含む所定の行セットが含まれている場合がありますが、他の行セットには頻繁に変更されるデータがあるとします。 このような場合は、データの一部を処理するときにデータ全体を処理する必要はありません。 パーティションを使用すると、めったに処理されないデータから頻繁に処理する必要のあるデータ部分を分割できます。  
  
 効率的なモデル設計によるパーティションの活用によって、不必要な処理とその後の Analysis Services サーバーでのプロセッサ負荷が排除されます。同時に、データ ソースの大部分の最新のデータを反映できる頻度でデータが処理され更新されるようになります。 モデル作成時にパーティションをどのように実装し利用するかは、配置済みモデルでパーティションがどのように実装され利用されているかによって大幅に異なる場合があります。 モデル作成段階では、最終的に配置済みモデルに入るデータのサブセットのみを操作している可能性があるということに注意してください。  
  
### <a name="processing-partitions"></a>パーティションの処理  
 SSMS を使用して、またはプロセス コマンドが含まれ、処理オプションと設定を指定するスクリプトを実行して配置済みのモデルの処理に発生します。 SSDT を使用してモデルを作成するときは、プロセス モデル メニューまたはツールバーからコマンドを使用してプロセス操作を実行することができます。 処理操作は、パーティション、テーブル、またはすべてに対して指定できます。  
  
 処理操作を実行するときは、データ接続を使用してデータ ソースへの接続が行われます。 モデル テーブルに新しいデータがインポートされると、各テーブルに対してリレーションシップと階層が再構築され、計算済みの列およびメジャーでの計算が再計算されます。  
  
 テーブルを論理パーティションにさらに分割することで、各パーティション内のどのデータを、どのタイミングで、どのように処理するかを、選択的に決めることができます。 モデルを配置するパーティションの処理は、SSMS でのパーティション ダイアログ ボックスを使用して手動で行うことができますか、プロセス コマンドを実行するスクリプトを使用しています。  
  
### <a name="partitions-in-the-model-workspace-database"></a>モデル ワークスペース データベースのパーティション  
 新しいパーティションを作成して編集、マージするか、または SSDT で Partition Manager を使用してパーティションを削除できます。 作成中のモデルの互換性レベルによっては、パーティション マネージャーは、テーブル、行、およびパーティションの列を選択するための 2 つのモードを提供します。表形式 1400 モデルでは、パーティションは、M クエリを使用して定義またはデザイン モードを使用してクエリ エディターを開くことができます。 表形式の 1100、1103、1200 モデルでは、テーブル プレビュー モードと使用 SQL クエリ モード。 
  
### <a name="partitions-in-a-deployed-model-database"></a>配置済みモデル データベースのパーティション  
 モデルを配置するときに、配置済みモデル データベース用のパーティションは、SSMS でデータベース オブジェクトとして表示されます。 作成して編集、マージするか、および SSMS の [パーティション] ダイアログ ボックスを使用して配置済みモデルのパーティションを削除できます。 SSMS での配置モデルのパーティションを管理するが、このトピックの範囲外です。 SSMS でのパーティション管理については、次を参照してください。[の作成とテーブル モデル パーティションの管理](../../analysis-services/tabular-models/create-and-manage-tabular-model-partitions-ssas-tabular.md)します。  
  
##  <a name="bkmk_related_tasks"></a> 関連タスク  
  
|トピック|説明|  
|-----------|-----------------|  
|[ワークスペース データベースのパーティションの作成と管理](../../analysis-services/tabular-models/create-and-manage-partitions-in-the-workspace-database-ssas-tabular.md)|作成して、SSDT で Partition Manager を使用して、モデル ワークスペース データベースでパーティションを管理する方法について説明します。|  
|[ワークスペース データベースのパーティションの処理](../../analysis-services/tabular-models/process-partitions-in-the-workspace-database-ssas-tabular.md)|モデル ワークスペース データベースでのパーティションの処理 (更新) 方法について説明します。|  
  
## <a name="see-also"></a>関連項目  
 [DirectQuery モード](../../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)   
 [データの処理](../../analysis-services/tabular-models/process-data-ssas-tabular.md)  
  
  
