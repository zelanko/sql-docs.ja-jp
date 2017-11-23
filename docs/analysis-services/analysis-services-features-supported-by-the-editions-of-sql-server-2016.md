---
title: "Analysis Services の SQL Server 2016 の各エディションでサポートされている機能 |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/29/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: misc
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/data-mining
- analysis-services/multidimensional-tabular
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f09d7be1-bd63-43f8-b91c-bf19166b4457
caps.latest.revision: "4"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 05804908eb3d5b4d519516519eb091e92aeaee34
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="analysis-services-features-supported-by-the-editions-of-sql-server-2016"></a>SQL Server 2016 の各エディションがサポートする Analysis Services の機能
[!INCLUDE[ssas-appliesto-sql2016-later](../includes/ssas-appliesto-sql2016-later.md)]

このトピックでは、SQL Server 2016 Analysis Services のさまざまなエディションでサポートされる機能の詳細を説明します。 Evaluation および Developer エディションでサポートされる機能、Enterprise edition を参照してください。

## <a name="analysis-services-servers"></a>Analysis Services (サーバー)
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|開発者|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|スケーラブルな共有データベース|はい||||||はい|  
|データベースのバックアップ/復元、アタッチ/デタッチ|はい|可|||||はい|  
|データベースの同期|はい||||||はい|  
|Always On フェールオーバー クラスター インスタンス|はい<br /><br /> ノードの数はオペレーティング システムの最大容量|はい<br /><br /> 2 つのノードのサポート|||||はい<br /><br /> ノードの数はオペレーティング システムの最大容量|  
|プログラミング (AMO、ADOMD.Net、OLEDB、XML/A、ASSL、TMSL)|はい|可|||||可|  
  
## <a name="tabular-models"></a>テーブル モデル 
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|開発者|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|階層|はい|可|||||はい|  
|KPI|はい|可|||||はい|  
|パースペクティブ|はい||||||はい|  
|翻訳|はい|可|||||はい|  
|DAX 計算、DAX クエリ、MDX クエリ|はい|可|||||はい|  
|行レベルのセキュリティ|はい|可|||||はい|  
|複数パーティション|はい||||||はい|  
|インメモリ ストレージ モード|はい|可|||||はい|  
|DirectQuery ストレージ モード|はい||||||可|  

## <a name="multidimensional-models"></a>多次元モデル 
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|開発者|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|準加法メジャー|はい|不可 <sup>1</sup>|||||はい|  
|階層|はい|可|||||はい|  
|KPI|はい|可|||||はい|  
|パースペクティブ|はい||||||はい|  
|アクション|はい|可|||||はい|  
|勘定科目インテリジェンス|はい|可|||||はい|  
|タイム インテリジェンス|はい|可|||||はい|  
|カスタム ロールアップ|はい|可|||||はい|  
|キューブの書き戻し|はい|可|||||はい|  
|ディメンションの書き戻し|はい||||||はい|  
|セルの書き戻し|はい|可|||||はい|  
|ドリルスルー|はい|可|||||はい|  
|高度な階層の種類 (親子、不規則階層)|はい|可|||||はい|  
|高度なディメンション (参照ディメンション、多対多ディメンション)|はい|可|||||はい|  
|リンク メジャーとディメンション|はい|可  <sup>2</sup> |||||はい|  
|翻訳|はい|可|||||はい|  
|集計|はい|可|||||はい|  
|複数パーティション|はい|可 (3 つまで)|||||はい|  
|プロアクティブ キャッシュ|はい||||||はい|  
|カスタム アセンブリ (ストアド プロシージャ)|はい|可|||||はい|  
|MDX クエリおよびスクリプト|はい|可|||||はい|  
|DAX クエリ|はい|可|||||はい|  
|ロールベースのセキュリティ モデル|はい|可|||||はい|  
|ディメンションおよびセル レベルのセキュリティ|はい|可|||||はい|  
|スケーラブルな文字列ストレージ|はい|可|||||はい|  
|MOLAP、ROLAP、および HOLAP ストレージ モード|はい|可|||||はい|  
|バイナリおよび圧縮 XML の転送|はい|可|||||はい|  
|プッシュモード処理|はい||||||はい|  
|直接書き戻し|はい||||||はい|  
|メジャー式|はい||||||はい|  
  
 <sup>1</sup> LastChild 準加法メジャーは Standard Edition でサポートされますが、他の準加法メジャー (None、FirstChild、FirstNonEmpty、LastNonEmpty、AverageOfChildren、ByAccount など) はサポートされません。 加法メジャー (Sum、Count、Min、Max など) や非加法メジャー (DistinctCount) はすべてのエディションでサポートされます。  
  <sup>2</sup>リンクのメジャーとディメンションが、同じデータベース内の他のデータベースまたはインスタンスからではなく standard edition をサポートしています。
  
## <a name="power-pivot-for-sharepoint"></a>Power Pivot for SharePoint  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|開発者|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|共有サービス アーキテクチャに基づく SharePoint ファーム統合|はい||||||はい|  
|使用状況レポート|はい||||||はい|  
|状態の監視のルール|はい||||||はい|  
|Power Pivot ギャラリー|はい||||||はい|  
|Power Pivot データ更新|はい||||||はい|  
|Power Pivot データ フィード|はい||||||はい|  
  
## <a name="data-mining"></a>データ マイニング  
  
|機能名|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|開発者|  
|------------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|標準アルゴリズム|はい|可|||||はい|  
|データ マイニング ツール (ウィザード、エディター、クエリ ビルダー)|はい|可|||||はい|  
|相互検証|はい||||||はい|  
|マイニング構造データのフィルター選択したサブセットのモデル|はい||||||はい|  
|時系列: ARTXP 法と ARIMA 法のカスタムな組み合わせ|はい||||||はい|  
|時系列: 新しいデータでの予測|はい||||||はい|  
|無制限の同時 DM クエリ|はい||||||はい|  
|データ マイニング アルゴリズムの構成とチューニングの拡張オプション|はい||||||はい|  
|プラグイン アルゴリズムのサポート|はい||||||はい|  
|並列モデル処理|はい||||||はい|  
|時系列: 系列のクロス予測|はい||||||はい|  
|アソシエーション ルールの無制限の属性|はい||||||はい|  
|シーケンス予測|はい||||||はい|  
|複数の Naïve Bayes の予測ターゲット、ニューラル ネットワーク、およびロジスティック回帰|はい||||||はい|  
  
 ## <a name="see-also"></a>参照  
 [SQL Server 2016 の製品仕様](http://msdn.microsoft.com/library/6445fd53-6844-4170-a86b-7fe76a9f64cb)   
 [SQL Server 2016 のインストール](../database-engine/install-windows/installation-for-sql-server-2016.md)  


