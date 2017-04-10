---
title: "SQL Server 2016 の各エディションがサポートする Analysis Services の機能 | Microsoft Docs"
ms.custom: ""
ms.date: "09/02/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
  - "analysis-services/multidimensional-tabular"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f09d7be1-bd63-43f8-b91c-bf19166b4457
caps.latest.revision: 4
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 3
---
# SQL Server 2016 の各エディションがサポートする Analysis Services の機能
このトピックでは、 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]のさまざまなエディションでサポートされる機能の詳細について説明します。  
  
 180 日の試用期間中、SQL Server Evaluation Edition をご利用いただけます。  
  
 最新のリリース ノートについては、「 [SQL Server 2016 Release Notes](../sql-server/sql-server-2016-release-notes.md)」を参照してください。 新機能に関する最新情報については、「[Analysis Services の新機能](../analysis-services/what-s-new-in-analysis-services.md)」を参照してください。
    
 **SQL Server 2016 をお試しください。**    
    
 > [![Evaluation Center からダウンロードする](../analysis-services/media/download.png)](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016) **[Evaluation Center から SQL Server 2016 をダウンロードする](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016)**    
    
> ![Azure 仮想マシンのアイコン](../analysis-services/media/azure-virtual-machine-small.png) **[SQL Server 2016 がインストール済みの仮想マシンをすぐにご利用いただけます](https://azure.microsoft.com/en-us/marketplace/partners/microsoft/sqlserver2016rtmenterprisewindowsserver2012r2/?wt.mc_id=sqL16_vm)**    
    
  
 Evaluation Edition および Developer Edition でサポートされている機能については、SQL Server Enterprise Edition をご覧ください。
  
 各 SQL Server テクノロジの表に移動するには、それぞれのリンクをクリックしてください。 
 
 -  [Analysis Services](#SSAS)  
  
-   [BI セマンティック モデル (多次元)](#BIMD)  
  
-   [BI セマンティック モデル (テーブル)](#BIT)  
  
-   [Power Pivot for SharePoint](#PPSP)  
  
-   [データ マイニング](#DM)  
  
-   [Business Intelligence クライアント](#BIC)  

##  <a name="SSAS"></a> Analysis Services  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|開発者|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|スケーラブルな共有データベース|はい||||||可|  
|データベースのバックアップ/復元、アタッチ/デタッチ|可|可|||||はい|  
|データベースの同期|はい||||||はい|  
|Always On フェールオーバー クラスター インスタンス|はい<br /><br /> ノードの数はオペレーティング システムの最大容量|はい<br /><br /> 2 つのノードのサポート|||||はい<br /><br /> ノードの数はオペレーティング システムの最大容量|  
|プログラミング (AMO、ADOMD.Net、OLEDB、XML/A、ASSL、TMSL)|可|可|||||可|  
  
##  <a name="BIMD"></a> BI セマンティック モデル (多次元)  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|開発者|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|準加法メジャー|可|不可 <sup>1</sup>|||||はい|  
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
|ドリルスルー|はい|可|||||可|  
|高度な階層の種類 (親子、不規則階層)|可|可|||||可|  
|高度なディメンション (参照ディメンション、多対多ディメンション)|可|可|||||はい|  
|リンク メジャーとディメンション|可|可 <sup>2</sup> |||||可|  
|翻訳|はい|可|||||はい|  
|集計|はい|可|||||はい|  
|複数パーティション|はい|可 (3 つまで)|||||はい|  
|プロアクティブ キャッシュ|はい||||||可|  
|カスタム アセンブリ (ストアド プロシージャ)|可|可|||||はい|  
|MDX クエリおよびスクリプト|はい|可|||||はい|  
|DAX クエリ|はい|可|||||可|  
|ロールベースのセキュリティ モデル|可|可|||||可|  
|ディメンションおよびセル レベルのセキュリティ|可|可|||||はい|  
|スケーラブルな文字列ストレージ|はい|可|||||はい|  
|MOLAP、ROLAP、および HOLAP ストレージ モード|はい|可|||||はい|  
|バイナリおよび圧縮 XML の転送|はい|可|||||可|  
|プッシュモード処理|可||||||はい|  
|直接書き戻し|はい||||||はい|  
|メジャー式|はい||||||可|  
  
 <sup>1</sup> LastChild 準加法メジャーは Standard Edition でサポートされますが、他の準加法メジャー (None、FirstChild、FirstNonEmpty、LastNonEmpty、AverageOfChildren、ByAccount など) はサポートされません。 加法メジャー (Sum、Count、Min、Max など) や非加法メジャー (DistinctCount) はすべてのエディションでサポートされます。  
  <sup>2</sup> Standard Edition では、同じデータベース内でのメジャーおよびディメンションのリンク設定をサポートしますが、他のデータベースまたはインスタンスからのリンク設定はサポートしません。
   
##  <a name="BIT"></a> BI セマンティック モデル (テーブル)  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|開発者|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|階層|はい|可|||||はい|  
|KPI|はい|可|||||はい|  
|パースペクティブ|はい||||||はい|  
|翻訳|はい|可|||||はい|  
|DAX 計算、DAX クエリ、MDX クエリ|はい|可|||||可|  
|行レベルのセキュリティ|可|可|||||はい|  
|複数パーティション|はい||||||可|  
|インメモリ ストレージ モード|可|可|||||はい|  
|DirectQuery ストレージ モード|はい||||||はい|  
  
##  <a name="PPSP"></a> Power Pivot for SharePoint  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|開発者|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|共有サービス アーキテクチャに基づく SharePoint ファーム統合|はい||||||はい|  
|使用状況レポート|はい||||||はい|  
|状態の監視のルール|はい||||||はい|  
|Power Pivot ギャラリー|はい||||||はい|  
|Power Pivot データ更新|はい||||||はい|  
|Power Pivot データ フィード|はい||||||はい|  
  
##  <a name="DM"></a> データ マイニング  
  
|機能名|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|開発者|  
|------------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|標準アルゴリズム|はい|可|||||可|  
|データ マイニング ツール (ウィザード、エディター、クエリ ビルダー)|可|可|||||はい|  
|相互検証|はい||||||はい|  
|マイニング構造データのフィルター選択したサブセットのモデル|はい||||||はい|  
|時系列: ARTXP 法と ARIMA 法のカスタムな組み合わせ|はい||||||はい|  
|時系列: 新しいデータでの予測|はい||||||はい|  
|無制限の同時 DM クエリ|はい||||||はい|  
|データ マイニング アルゴリズムの構成とチューニングの拡張オプション|はい||||||可|  
|プラグイン アルゴリズムのサポート|可||||||はい|  
|並列モデル処理|はい||||||可|  
|時系列: 系列のクロス予測|可||||||はい|  
|アソシエーション ルールの無制限の属性|はい||||||はい|  
|シーケンス予測|はい||||||はい|  
|複数の Naïve Bayes の予測ターゲット、ニューラル ネットワーク、およびロジスティック回帰|はい||||||可|  
  
##  <a name="BIC"></a> Business Intelligence クライアント  
 次のソフトウェア クライアント アプリケーションを Microsoft ダウンロード センターから入手できます。これらのアプリケーションは、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスで使用するビジネス インテリジェンス ドキュメントの作成に役立ちます。 作成したドキュメントをサーバー環境でホストする場合は、そのドキュメントの種類をサポートする [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のエディションを使用してください。 これらのクライアント アプリケーションで作成したドキュメントをホストするのに必要なサーバー機能を備えた [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エディションを次の表に示します。  
  
|ツール名|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|開発者|  
|---------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Excel および Visio 2010 用データ マイニング アドイン (.xlsx、.vsdx)|可|可|||||可|  
|[!INCLUDE[ssGeminiClient](../includes/ssgeminiclient-md.md)] 2010 および 2013 (.xlsx)|可||||||可|  
|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] (.xlsx)|可||||||可|  
  
> [!NOTE]  
>  1.  [!INCLUDE[ssGeminiClient](../includes/ssgeminiclient-md.md)] データ モデルを含むブックを作成するための Excel アドインです。  [!INCLUDE[ssGeminiClient](../includes/ssgeminiclient-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] に依存しませんが、SharePoint でデータ モデルを含む Excel ブックの共有およびコラボレーションを行うには、[!INCLUDE[ssGeminiShort](../includes/ssgeminishort-md.md)] が必要です。 この機能は、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Enterprise Edition の一部として使用できます。  
>   
>      Excel 2016 では、Power Pivot 機能が組み込まれているので、Power Pivot アドインが不要になりました。  
> 2.  上記の表は、これらのクライアント ツールを有効にするために必要な [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エディションを示しています。ただし、これらのツールは、どのエディションの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] にホストされているデータにもアクセスできます。  
  
 ## 参照  
 [SQL Server 2016 の各エディションでサポートされる機能](Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md)  
 [SQL Server 2016 の製品仕様](../Topic/Product%20Specifications%20for%20SQL%20Server%202016.md)   
 [SQL Server 2016 のインストール](../database-engine/install-windows/installation-for-sql-server-2016.md)  

