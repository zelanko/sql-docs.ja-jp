---
title: Analysis Services の SQL Server のエディションでサポートされる機能 |Microsoft Docs
ms.date: 06/25/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9947b10e01864f66bf26d6599e43814ab37dadc6
ms.sourcegitcommit: ce5770d8b91c18ba5ad031e1a96a657bde4cae55
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2019
ms.locfileid: "67388205"
---
# <a name="analysis-services-features-supported-by-sql-server-edition"></a>SQL Server のエディションでサポートされている analysis Services 機能
[!INCLUDE[ssas-appliesto-sql2016-later](../includes/ssas-appliesto-sql2016-later.md)]

この記事では、SQL Server 2016、2017 年 2019 Analysis Services のさまざまなエディションでサポートされる機能について説明します。 評価版は、Enterprise edition の機能をサポートします。

## <a name="analysis-services-servers"></a>Analysis Services (サーバー)
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Developer|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|スケーラブルな共有データベース|はい||||||はい|  
|データベースのバックアップ/復元、アタッチ/デタッチ|はい|[はい]|||||はい|  
|データベースの同期|はい||||||はい|  
|Always On フェールオーバー クラスター インスタンス|はい<br /><br /> ノードの数はオペレーティング システムの最大容量|はい<br /><br /> 2 つのノードのサポート|||||はい<br /><br /> ノードの数はオペレーティング システムの最大容量|  
|プログラミング (AMO、ADOMD.Net、OLEDB、XML/A、ASSL、TMSL)|はい|[はい]|||||はい|  
  
## <a name="tabular-models"></a>テーブル モデル 
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Developer|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|階層|はい|[はい]|||||はい|  
|KPI|はい|[はい]|||||はい|  
|パースペクティブ|はい||||||はい|  
|翻訳|はい|[はい]|||||はい|  
|DAX 計算、DAX クエリ、MDX クエリ|はい|[はい]|||||はい|  
|行レベルのセキュリティ|はい|[はい]|||||はい|  
|複数パーティション|はい||||||はい|  
|計算グループ|[はい] (SQL Server 2019 以降)|[はい] (SQL Server 2019 以降)|||||[はい] (SQL Server 2019 以降)|  
|インメモリ ストレージ モード|はい|[はい]|||||はい|  
|DirectQuery モード|はい|[はい] (SQL Server 2019 以降)|||||はい|  

## <a name="multidimensional-models"></a>多次元モデル 
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Developer|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|準加法メジャー|はい|不可 <sup>1</sup>|||||[はい]|  
|階層|はい|[はい]|||||はい|  
|KPI|はい|[はい]|||||はい|  
|パースペクティブ|はい||||||はい|  
|アクション|はい|[はい]|||||はい|  
|勘定科目インテリジェンス|はい|[はい]|||||はい|  
|タイム インテリジェンス|はい|[はい]|||||はい|  
|カスタム ロールアップ|はい|[はい]|||||はい|  
|キューブの書き戻し|はい|[はい]|||||はい|  
|ディメンションの書き戻し|はい||||||はい|  
|セルの書き戻し|はい|[はい]|||||はい|  
|ドリルスルー|はい|[はい]|||||はい|  
|高度な階層の種類 (親子、不規則階層)|はい|[はい]|||||はい|  
|高度なディメンション (参照ディメンション、多対多ディメンション)|はい|[はい]|||||はい|  
|リンク メジャーとディメンション|はい|可  <sup>2</sup> |||||はい|  
|翻訳|はい|[はい]|||||はい|  
|集計|はい|[はい]|||||はい|  
|複数パーティション|はい|可 (3 つまで)|||||はい|  
|プロアクティブ キャッシュ|[はい]||||||はい|  
|カスタム アセンブリ (ストアド プロシージャ)|[はい]|[はい]|||||はい|  
|MDX クエリおよびスクリプト|はい|[はい]|||||はい|  
|DAX クエリ|はい|[はい]|||||はい|  
|ロールベースのセキュリティ モデル|はい|[はい]|||||はい|  
|ディメンションおよびセル レベルのセキュリティ|はい|[はい]|||||はい|  
|スケーラブルな文字列ストレージ|はい|[はい]|||||はい|  
|MOLAP、ROLAP、および HOLAP ストレージ モード|はい|[はい]|||||はい|  
|バイナリおよび圧縮 XML の転送|はい|[はい]|||||はい|  
|プッシュモード処理|はい||||||はい|  
|メジャー式|はい||||||はい|  
  
 <sup>1</sup> LastChild 準加法メジャーは Standard Edition でサポートされますが、他の準加法メジャー (None、FirstChild、FirstNonEmpty、LastNonEmpty、AverageOfChildren、ByAccount など) はサポートされません。 加法メジャー (Sum、Count、Min、Max など) や非加法メジャー (DistinctCount) はすべてのエディションでサポートされます。  
  <sup>2</sup> Standard Edition では、同じデータベース内でのメジャーおよびディメンションのリンク設定をサポートしますが、他のデータベースまたはインスタンスからのリンク設定はサポートしません。
  
## <a name="power-pivot-for-sharepoint"></a>Power Pivot for SharePoint  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Developer|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|共有サービス アーキテクチャに基づく SharePoint ファーム統合|はい||||||はい|  
|使用状況レポート|はい||||||はい|  
|状態の監視のルール|はい||||||はい|  
|Power Pivot ギャラリー|はい||||||はい|  
|Power Pivot データ更新|[はい]||||||はい|  
|Power Pivot データ フィード|はい||||||はい|  
  
## <a name="data-mining"></a>データ マイニング  
  
|機能名|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Developer|  
|------------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|標準アルゴリズム|はい|[はい]|||||はい|  
|データ マイニング ツール (ウィザード、エディター、クエリ ビルダー)|はい|[はい]|||||はい|  
|相互検証|はい||||||はい|  
|マイニング構造データのフィルター選択したサブセットのモデル|はい||||||はい|  
|時系列:カスタムな組み合わせ ARTXP と ARIMA 法|はい||||||はい|  
|時系列:新しいデータでの予測|はい||||||はい|  
|無制限の同時 DM クエリ|はい||||||はい|  
|データ マイニング アルゴリズムの構成とチューニングの拡張オプション|はい||||||はい|  
|プラグイン アルゴリズムのサポート|はい||||||[はい]|  
|並列モデル処理|はい||||||はい|  
|時系列: 系列のクロス予測|はい||||||はい|  
|アソシエーション ルールの無制限の属性|はい||||||はい|  
|シーケンス予測|はい||||||はい|  
|複数の Naïve Bayes の予測ターゲット、ニューラル ネットワーク、およびロジスティック回帰|[はい]||||||はい|  
  


