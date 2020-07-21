---
title: Teradata の接続の種類 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: b02779c2-a6b9-453c-815f-adad53353952
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4a47fb239121b1e354923fc42ed3da29716fdba5
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66107018"
---
# <a name="teradata-connection-type-ssrs"></a>Teradata の接続の種類 (SSRS)
  Teradata リレーショナル データベースのデータをレポートに含めるには、種類が Teradata のレポート データ ソースに基づいたデータセットが必要です。 このビルトイン データ ソースの種類は、.NET Managed Provider for Teradata データ処理拡張機能に基づいています。  
  
 このトピックの情報を使用して、データ ソースを構築してください。 詳細な手順については、「[データ接続またはデータソース &#40;レポートビルダーと SSRS&#41;の追加と検証](add-and-verify-a-data-connection-report-builder-and-ssrs.md)」を参照してください。  
  
##  <a name="connection-string"></a><a name="Connection"></a> 接続文字列  
 データ ソースへの接続に使用する接続情報および資格情報については、データベース管理者に問い合わせてください。 次の接続文字列の例では、IP アドレスで指定したサーバー上の Teradata データベースを指定しています。  
  
```  
data source=<IP Address>  
```  
  
 接続文字列の例について詳しくは、「 [レポート ビルダーでのデータ接続、データ ソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-report-builder.md)」をご覧ください。  
  
##  <a name="credentials"></a><a name="Credentials"></a> [資格情報]  
 クエリの実行、ローカルでのレポートのプレビュー、およびレポート サーバーからのレポートのプレビューには、資格情報が必要です。  
  
 レポートをパブリッシュした後、レポートをレポート サーバーで実行するときに、データを取得するための権限が有効な状態になるように、データ ソースの資格情報を変更する必要が生じる場合があります。  
  
 詳細については、「 [Reporting Services のデータ接続、データソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)」または「[レポートビルダーで資格情報を指定する](../specify-credentials-in-report-builder.md)」を参照してください。  

##  <a name="remarks"></a><a name="Remarks"></a> 解説  
 Teradata データ ソースに接続するには、システム管理者が、Teradata データベースからのデータの取得をサポートするバージョンの .NET Data Provider for Teradata をインストールしておく必要があります。 このデータ プロバイダーは、レポート ビルダーがインストールされているコンピューターとレポート サーバーにインストールされている必要があります。  
  
 このデータ プロバイダーでは使用できないレポート配信モードもあります。 このデータ処理拡張機能では、データ ドリブン サブスクリプションを使ったレポートの配信はサポートされません。 詳細については、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [オンライン ブック](https://go.microsoft.com/fwlink/?linkid=121312) の [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のドキュメントの「[サブスクライバー データに対して外部データ ソースを使用する &#40;データ ドリブン サブスクリプション&#41;](../subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md)」を参照してください。  

##  <a name="report-models"></a><a name="Models"></a> レポート モデル  
 Teradata データ ソースに基づくレポート モデルからデータセットを作成するには、モデルを [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] のモデル デザイナーでデザインし、レポート サーバーでパブリッシュする必要があります。  

##  <a name="related-sections"></a><a name="Related"></a> 関連項目  
 次に示すセクションでは、レポート データの概念が詳細に説明されているほか、データに関連するレポートのパーツを定義し、カスタマイズし、使用する方法が説明されています。  
  
 [レポート &#40;レポートビルダーおよび SSRS&#41;にデータを追加する](report-datasets-ssrs.md)  
 レポートのデータへのアクセスの概要について説明します。  
  
 [レポート ビルダーでのデータ接続、データ ソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 データ接続とデータ ソースについて説明します。  
  
 [レポート埋め込みデータセットと共有データセット (レポート ビルダーおよび SSRS)](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 埋め込みデータセットと共有データセットについて説明します。  
  
 [データセット フィールド コレクション (レポート ビルダーおよび SSRS)](dataset-fields-collection-report-builder-and-ssrs.md)  
 データセット クエリによって生成されるフィールド コレクションについて説明します。  
  
 [Reporting Services でサポートされるデータ ソース &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [オンライン ブックの [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ドキュメント](https://go.microsoft.com/fwlink/?linkid=121312))。  
 各データ拡張機能のプラットフォームおよびバージョン サポートに関する詳細な情報です。  
  
 [Using SQL Server 2008 Reporting Services with the .NET Framework Data Provider for Teradata (英語)](https://go.microsoft.com/fwlink/?LinkID=130848)  
 このデータ拡張機能の使用に関する詳細な情報です。  

## <a name="see-also"></a>参照  
 [レポートパラメーター &#40;レポートビルダーとレポートデザイナー&#41;](../report-design/report-parameters-report-builder-and-report-designer.md)   
 [データのフィルター処理、グループ化、並べ替え &#40;レポートビルダーと SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [式 &#40;レポート ビルダーおよび SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md)  
