---
title: "Teradata の接続の種類 (SSRS) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b02779c2-a6b9-453c-815f-adad53353952
caps.latest.revision: 10
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: c74e24e12f97d264780e712a1e7e5f3fbea6f9fb
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="teradata-connection-type-ssrs"></a>Teradata の接続の種類 (SSRS)
  Teradata リレーショナル データベースのデータをレポートに含めるには、種類が Teradata のレポート データ ソースに基づいたデータセットが必要です。 このビルトイン データ ソースの種類は、.NET Managed Provider for Teradata データ処理拡張機能に基づいています。  
  
 このトピックの情報を使用して、データ ソースを構築してください。 手順については、「 [データ接続を追加および確認する (レポート ビルダーおよび SSRS)](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)」を参照してください。  
  
##  <a name="Connection"></a> 接続文字列  
 データ ソースへの接続に使用する接続情報および資格情報については、データベース管理者に問い合わせてください。 次の接続文字列の例では、IP アドレスで指定したサーバー上の Teradata データベースを指定しています。  
  
```  
data source=<IP Address>  
```  
  
 接続文字列の例の詳細については、「 [レポート ビルダーでのデータ接続、データ ソース、および接続文字列](http://msdn.microsoft.com/library/7e103637-4371-43d7-821c-d269c2cc1b34)」を参照してください。  
  
##  <a name="Credentials"></a> [資格情報]  
 クエリの実行、ローカルでのレポートのプレビュー、およびレポート サーバーからのレポートのプレビューには、資格情報が必要です。  
  
 レポートをパブリッシュした後、レポートをレポート サーバーで実行するときに、データを取得するための権限が有効な状態になるように、データ ソースの資格情報を変更する必要が生じる場合があります。  
  
 詳しくは、「[データ接続、データ ソース、および接続文字列 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)」または「[レポート ビルダーでの資格情報の指定](http://msdn.microsoft.com/library/7412ce68-aece-41c0-8c37-76a0e54b6b53)」を参照してください。  
  
  
##  <a name="Remarks"></a> 解説  
 Teradata データ ソースに接続するには、システム管理者が、Teradata データベースからのデータの取得をサポートするバージョンの .NET Data Provider for Teradata をインストールしておく必要があります。 このデータ プロバイダーは、レポート ビルダーがインストールされているコンピューターとレポート サーバーにインストールされている必要があります。  
  
 このデータ プロバイダーでは使用できないレポート配信モードもあります。 このデータ処理拡張機能では、データ ドリブン サブスクリプションを使ったレポートの配信はサポートされません。 詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [オンライン ブック](http://go.microsoft.com/fwlink/?linkid=121312) の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のドキュメントの「[サブスクライバー データに対して外部データ ソースを使用する (データ ドリブン サブスクリプション)](../../reporting-services/subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md)」を参照してください。  
  
  
##  <a name="Models"></a> レポート モデル  
 Teradata データ ソースに基づくレポート モデルからデータセットを作成するには、モデルを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] のモデル デザイナーでデザインし、レポート サーバーでパブリッシュする必要があります。  
  
  
##  <a name="Related"></a> 関連項目  
 次に示すセクションでは、レポート データの概念が詳細に説明されているほか、データに関連するレポートのパーツを定義し、カスタマイズし、使用する方法が説明されています。  
  
 [レポート データセット (SSRS)](../../reporting-services/report-data/report-datasets-ssrs.md)  
 レポートのデータへのアクセスの概要について説明します。  
  
 [データ接続、データ ソース、およびレポート ビルダーでの接続文字列](http://msdn.microsoft.com/library/7e103637-4371-43d7-821c-d269c2cc1b34)  
 データ接続とデータ ソースについて説明します。  
  
 [レポート埋め込みデータセットおよび共有データセット &#40; です。レポート ビルダーおよび SSRS &#41; です。](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 埋め込みデータセットと共有データセットについて説明します。  
  
 [データセット フィールド コレクションと &#40; です。レポート ビルダーおよび SSRS &#41; です。](../../reporting-services/report-data/dataset-fields-collection-report-builder-and-ssrs.md)  
 データセット クエリによって生成されるフィールド コレクションについて説明します。  
  
 [Reporting Services でサポートされるデータ ソース (SSRS)](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md) ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [オンライン ブック](http://go.microsoft.com/fwlink/?linkid=121312)の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ドキュメント)  
 各データ拡張機能のプラットフォームおよびバージョン サポートに関する詳細な情報です。  
  
 [Using SQL Server 2008 Reporting Services with the .NET Framework Data Provider for Teradata (英語)](http://go.microsoft.com/fwlink/?LinkID=130848)  
 このデータ拡張機能の使用に関する詳細な情報です。  
  
  
## <a name="see-also"></a>参照  
 [レポート パラメーターと &#40; です。レポート ビルダーおよびレポート デザイナーと &#41; です。](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [フィルター、グループ、およびデータを並べ替える &#40; です。レポート ビルダーおよび SSRS &#41; です。](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [式と &#40; です。レポート ビルダーおよび SSRS &#41; です。](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)  
  
  
