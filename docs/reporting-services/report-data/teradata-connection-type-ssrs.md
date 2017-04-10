---
title: "Teradata の接続の種類 (SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b02779c2-a6b9-453c-815f-adad53353952
caps.latest.revision: 10
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 9
---
# Teradata の接続の種類 (SSRS)
  Teradata リレーショナル データベースのデータをレポートに含めるには、種類が Teradata のレポート データ ソースに基づいたデータセットが必要です。 このビルトイン データ ソースの種類は、.NET Managed Provider for Teradata データ処理拡張機能に基づいています。  
  
 このトピックの情報を使用して、データ ソースを構築してください。 手順については、「[データ接続を追加および確認する &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)」を参照してください。  
  
##  <a name="Connection"></a> 接続文字列  
 データ ソースへの接続に使用する接続情報および資格情報については、データベース管理者に問い合わせてください。 次の接続文字列の例では、IP アドレスで指定したサーバー上の Teradata データベースを指定しています。  
  
```  
data source=<IP Address>  
```  
  
 接続文字列の例の詳細については、「[レポート ビルダーでのデータ接続、データ ソース、および接続文字列](../Topic/Data%20Connections,%20Data%20Sources,%20and%20Connection%20Strings%20in%20Report%20Builder.md)」を参照してください。  
  
##  <a name="Credentials"></a> [資格情報]  
 クエリの実行、ローカルでのレポートのプレビュー、およびレポート サーバーからのレポートのプレビューには、資格情報が必要です。  
  
 レポートをパブリッシュした後、レポートをレポート サーバーで実行するときに、データを取得するための権限が有効な状態になるように、データ ソースの資格情報を変更する必要が生じる場合があります。  
  
 詳細については、「[データ接続、データ ソース、および接続文字列 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)」または「[レポート ビルダーでの資格情報の指定](../Topic/Specify%20Credentials%20in%20Report%20Builder.md)」を参照してください。  
  
 ![[トップに戻る] リンクで使用される矢印アイコン](../../analysis-services/instances/media/uparrow16x16.png "[トップに戻る] リンクで使用される矢印アイコン") [トップに戻る](#BackToTop)  
  
##  <a name="Remarks"></a> 解説  
 Teradata データ ソースに接続するには、システム管理者が、Teradata データベースからのデータの取得をサポートするバージョンの .NET Data Provider for Teradata をインストールしておく必要があります。 このデータ プロバイダーは、レポート ビルダーがインストールされているコンピューターとレポート サーバーにインストールされている必要があります。  
  
 このデータ プロバイダーでは使用できないレポート配信モードもあります。 このデータ処理拡張機能では、データ ドリブン サブスクリプションを使ったレポートの配信はサポートされません。 詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [オンライン ブック](http://go.microsoft.com/fwlink/?linkid=121312) の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のドキュメントの「[サブスクライバー データに対して外部データ ソースを使用する &#40;データ ドリブン サブスクリプション&#41;](../../reporting-services/subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md)」を参照してください。  
  
 ![[トップに戻る] リンクで使用される矢印アイコン](../../analysis-services/instances/media/uparrow16x16.png "[トップに戻る] リンクで使用される矢印アイコン") [トップに戻る](#BackToTop)  
  
##  <a name="Models"></a> レポート モデル  
 Teradata データ ソースに基づくレポート モデルからデータセットを作成するには、モデルを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] のモデル デザイナーでデザインし、レポート サーバーでパブリッシュする必要があります。  
  
 ![[トップに戻る] リンクで使用される矢印アイコン](../../analysis-services/instances/media/uparrow16x16.png "[トップに戻る] リンクで使用される矢印アイコン") [トップに戻る](#BackToTop)  
  
##  <a name="Related"></a> 関連項目  
 次に示すセクションでは、レポート データの概念が詳細に説明されているほか、データに関連するレポートのパーツを定義、カスタマイズ、および使用する手順が説明されています。  
  
 [レポート データセット &#40;SSRS&#41;](../../reporting-services/report-data/report-datasets-ssrs.md)  
 レポートのデータへのアクセスの概要について説明します。  
  
 [レポート ビルダーでのデータ接続、データ ソース、および接続文字列](../Topic/Data%20Connections,%20Data%20Sources,%20and%20Connection%20Strings%20in%20Report%20Builder.md)  
 データ接続とデータ ソースについて説明します。  
  
 [レポート埋め込みデータセットと共有データセット &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 埋め込みデータセットと共有データセットについて説明します。  
  
 [データセット フィールド コレクション &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-data/dataset-fields-collection-report-builder-and-ssrs.md)  
 データセット クエリによって生成されるフィールド コレクションについて説明します。  
  
 [Reporting Services でサポートされるデータ ソース &#40;SSRS&#41;](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md) ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [オンライン ブック](http://go.microsoft.com/fwlink/?linkid=121312) の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ドキュメント)。  
 各データ拡張機能のプラットフォームおよびバージョン サポートに関する詳細な情報です。  
  
 [Using SQL Server 2008 Reporting Services with the .NET Framework Data Provider for Teradata (英語)](http://go.microsoft.com/fwlink/?LinkID=130848)  
 このデータ拡張機能の使用に関する詳細な情報です。  
  
 ![[トップに戻る] リンクで使用される矢印アイコン](../../analysis-services/instances/media/uparrow16x16.png "[トップに戻る] リンクで使用される矢印アイコン") [トップに戻る](#BackToTop)  
  
## 参照  
 [レポート パラメーター &#40;レポート ビルダーおよびレポート デザイナー&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [データのフィルター、グループ化、および並べ替え &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [式 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)  
  
  