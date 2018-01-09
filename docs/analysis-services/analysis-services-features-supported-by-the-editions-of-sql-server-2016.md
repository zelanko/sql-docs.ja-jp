---
title: "Analysis Services の SQL Server 2016 の各エディションでサポートされている機能 |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/29/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-tabular
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f09d7be1-bd63-43f8-b91c-bf19166b4457
caps.latest.revision: "4"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 0b69db6baee27296bf9544801b627c884d68795b
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="analysis-services-features-supported-by-the-editions-of-sql-server-2016"></a>SQL Server 2016 の各エディションがサポートする Analysis Services の機能
[!INCLUDE[ssas-appliesto-sql2016-later](../includes/ssas-appliesto-sql2016-later.md)]

このトピックでは、SQL Server 2016 Analysis Services のさまざまなエディションでサポートされる機能の詳細を説明します。 Evaluation および Developer エディションでサポートされる機能、Enterprise edition を参照してください。

## <a name="analysis-services-servers"></a>Analysis Services (サーバー)
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Developer|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|スケーラブルな共有データベース|可||||||可|  
|データベースのバックアップ/復元、アタッチ/デタッチ|可|可|||||可|  
|データベースの同期|可||||||可|  
|Always On フェールオーバー クラスター インスタンス|可<br /><br /> ノードの数はオペレーティング システムの最大容量|可<br /><br /> 2 つのノードのサポート|||||可<br /><br /> ノードの数はオペレーティング システムの最大容量|  
|プログラミング (AMO、ADOMD.Net、OLEDB、XML/A、ASSL、TMSL)|可|可|||||可|  
  
## <a name="tabular-models"></a>テーブル モデル 
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Developer|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|階層|はい|可|||||はい|  
|KPI|はい|可|||||はい|  
|パースペクティブ|はい||||||はい|  
|翻訳|可|可|||||可|  
|DAX 計算、DAX クエリ、MDX クエリ|可|可|||||可|  
|行レベルのセキュリティ|可|可|||||可|  
|複数パーティション|可||||||可|  
|インメモリ ストレージ モード|可|可|||||可|  
|DirectQuery ストレージ モード|可||||||可|  

## <a name="multidimensional-models"></a>多次元モデル 
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Developer|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|準加法メジャー|可|不可 <sup>1</sup>|||||可|  
|階層|はい|可|||||はい|  
|KPI|はい|可|||||はい|  
|パースペクティブ|はい||||||可|  
|アクション|可|可|||||可|  
|勘定科目インテリジェンス|可|可|||||可|  
|タイム インテリジェンス|可|可|||||可|  
|カスタム ロールアップ|可|可|||||可|  
|キューブの書き戻し|可|可|||||可|  
|ディメンションの書き戻し|可||||||可|  
|セルの書き戻し|可|可|||||可|  
|ドリルスルー|可|可|||||可|  
|高度な階層の種類 (親子、不規則階層)|可|可|||||可|  
|高度なディメンション (参照ディメンション、多対多ディメンション)|可|可|||||可|  
|リンク メジャーとディメンション|可|可  <sup>2</sup> |||||可|  
|翻訳|可|可|||||可|  
|集計|可|可|||||可|  
|複数パーティション|可|可 (3 つまで)|||||可|  
|プロアクティブ キャッシュ|可||||||可|  
|カスタム アセンブリ (ストアド プロシージャ)|可|可|||||可|  
|MDX クエリおよびスクリプト|可|可|||||可|  
|DAX クエリ|可|可|||||可|  
|ロールベースのセキュリティ モデル|可|可|||||可|  
|ディメンションおよびセル レベルのセキュリティ|可|可|||||可|  
|スケーラブルな文字列ストレージ|可|可|||||可|  
|MOLAP、ROLAP、および HOLAP ストレージ モード|可|可|||||可|  
|バイナリおよび圧縮 XML の転送|可|可|||||可|  
|プッシュモード処理|可||||||可|  
|直接書き戻し|可||||||可|  
|メジャー式|可||||||可|  
  
 <sup>1</sup> LastChild 準加法メジャーは Standard Edition でサポートされますが、他の準加法メジャー (None、FirstChild、FirstNonEmpty、LastNonEmpty、AverageOfChildren、ByAccount など) はサポートされません。 加法メジャー (Sum、Count、Min、Max など) や非加法メジャー (DistinctCount) はすべてのエディションでサポートされます。  
  <sup>2</sup>リンクのメジャーとディメンションが、同じデータベース内の他のデータベースまたはインスタンスからではなく standard edition をサポートしています。
  
## <a name="power-pivot-for-sharepoint"></a>Power Pivot for SharePoint  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Developer|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|共有サービス アーキテクチャに基づく SharePoint ファーム統合|可||||||可|  
|使用状況レポート|可||||||可|  
|状態の監視のルール|可||||||可|  
|Power Pivot ギャラリー|可||||||可|  
|Power Pivot データ更新|可||||||可|  
|Power Pivot データ フィード|可||||||可|  
  
## <a name="data-mining"></a>データ マイニング  
  
|機能名|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Developer|  
|------------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|標準アルゴリズム|可|可|||||可|  
|データ マイニング ツール (ウィザード、エディター、クエリ ビルダー)|可|可|||||可|  
|相互検証|可||||||可|  
|マイニング構造データのフィルター選択したサブセットのモデル|可||||||可|  
|時系列: ARTXP 法と ARIMA 法のカスタムな組み合わせ|可||||||可|  
|時系列: 新しいデータでの予測|可||||||可|  
|無制限の同時 DM クエリ|可||||||可|  
|データ マイニング アルゴリズムの構成とチューニングの拡張オプション|可||||||可|  
|プラグイン アルゴリズムのサポート|可||||||可|  
|並列モデル処理|可||||||可|  
|時系列: 系列のクロス予測|可||||||可|  
|アソシエーション ルールの無制限の属性|可||||||可|  
|シーケンス予測|可||||||可|  
|複数の Naïve Bayes の予測ターゲット、ニューラル ネットワーク、およびロジスティック回帰|可||||||可|  
  
 ## <a name="see-also"></a>参照  
 [SQL Server 2016 の製品仕様](http://msdn.microsoft.com/library/6445fd53-6844-4170-a86b-7fe76a9f64cb)   
 [SQL Server 2016 のインストール](../database-engine/install-windows/installation-for-sql-server-2016.md)  


