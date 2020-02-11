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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66107018"
---
# <a name="teradata-connection-type-ssrs"></a>Teradata の接続の種類 (SSRS)
  Teradata リレーショナル データベースのデータをレポートに含めるには、種類が Teradata のレポート データ ソースに基づいたデータセットが必要です。 このビルトイン データ ソースの種類は、.NET Managed Provider for Teradata データ処理拡張機能に基づいています。  
  
 このトピックの情報を使用して、データ ソースを構築してください。 詳細な手順については、「[データ接続またはデータソース &#40;レポートビルダーと SSRS&#41;の追加と検証](add-and-verify-a-data-connection-report-builder-and-ssrs.md)」を参照してください。  
  
##  <a name="Connection"></a>接続文字列  
 データ ソースへの接続に使用する接続情報および資格情報については、データベース管理者に問い合わせてください。 次の接続文字列の例では、IP アドレスで指定したサーバー上の Teradata データベースを指定しています。  
  
```  
data source=<IP Address>  
```  
  
 接続文字列の例の詳細については、「 [レポート ビルダーでのデータ接続、データ ソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-report-builder.md)」を参照してください。  
  
##  <a name="Credentials"></a>認証  
 クエリの実行、ローカルでのレポートのプレビュー、およびレポート サーバーからのレポートのプレビューには、資格情報が必要です。  
  
 レポートをパブリッシュした後、レポートをレポート サーバーで実行するときに、データを取得するための権限が有効な状態になるように、データ ソースの資格情報を変更する必要が生じる場合があります。  
  
 詳細については、「 [Reporting Services のデータ接続、データソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)」または「[レポートビルダーで資格情報を指定する](../specify-credentials-in-report-builder.md)」を参照してください。  

##  <a name="Remarks"></a> 解説  
 Teradata データ ソースに接続するには、システム管理者が、Teradata データベースからのデータの取得をサポートするバージョンの .NET Data Provider for Teradata をインストールしておく必要があります。 このデータ プロバイダーは、レポート ビルダーがインストールされているコンピューターとレポート サーバーにインストールされている必要があります。  
  
 このデータ プロバイダーでは使用できないレポート配信モードもあります。 このデータ処理拡張機能では、データ ドリブン サブスクリプションを使ったレポートの配信はサポートされません。 詳細については、[](../subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md)オンライン ブック[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] の  のドキュメントの「[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [サブスクライバー データに対して外部データ ソースを使用する &#40;データ ドリブン サブスクリプション&#41;](https://go.microsoft.com/fwlink/?linkid=121312)」を参照してください。  

##  <a name="Models"></a>レポートモデル  
 Teradata データソースに基づくレポートモデルからデータセットを作成するには、モデルをの[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]モデルデザイナーでデザインし、レポートサーバーにパブリッシュする必要があります。  

##  <a name="Related"></a>関連セクション  
 次に示すセクションでは、レポート データの概念が詳細に説明されているほか、データに関連するレポートのパーツを定義、カスタマイズ、および使用する手順が説明されています。  
  
 [レポート &#40;レポートビルダーおよび SSRS&#41;にデータを追加する](report-datasets-ssrs.md)  
 レポートのデータへのアクセスの概要について説明します。  
  
 [レポート ビルダーでのデータ接続、データ ソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 データ接続とデータ ソースについて説明します。  
  
 [レポート埋め込みデータセットと共有データセット (レポート ビルダーおよび SSRS)](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 埋め込みデータセットと共有データセットについて説明します。  
  
 [データセット フィールド コレクション &#40;レポート ビルダーおよび SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md)  
 データセット クエリによって生成されるフィールド コレクションについて説明します。  
  
 [Reporting Services によってサポートされるデータソース &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [オンラインブック](https://go.microsoft.com/fwlink/?linkid=121312)の[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]ドキュメントを参照してください。  
 各データ拡張機能のプラットフォームおよびバージョン サポートに関する詳細な情報です。  
  
 [Teradata の .NET Framework Data Provider での SQL Server 2008 Reporting Services の使用](https://go.microsoft.com/fwlink/?LinkID=130848)  
 このデータ拡張機能の使用に関する詳細な情報です。  

## <a name="see-also"></a>参照  
 [レポート パラメーター (レポート ビルダーおよびレポート デザイナー)](../report-design/report-parameters-report-builder-and-report-designer.md)   
 [データのフィルター、グループ化、および並べ替え (レポート ビルダーおよび SSRS)](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [式 &#40;レポート ビルダーおよび SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md)  
