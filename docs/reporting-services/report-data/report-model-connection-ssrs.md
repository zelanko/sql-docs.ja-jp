---
title: レポート モデルの接続 (SSRS) | Microsoft Docs
ms.date: 03/17/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-data
ms.topic: conceptual
ms.assetid: da880fb8-13cc-4d5f-b992-91ed0ec3ca7d
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 6fb1b5f810af0385195ad1f2f6bec048152887e8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47856810"
---
# <a name="report-model-connection-ssrs"></a>レポート モデルの接続 (SSRS)
  レポート モデルのデータを含めるには、レポート モデルに基づいたデータセットがデータ ソースとして必要です。 他のレポート データ ソースとは異なり、レポート モデルにはデータ拡張機能がありません。 レポート ビルダーでは、レポート サーバーを参照して、モデルを直接選択します。 レポート デザイナーでは、レポート モデルへの URL を指定します。  
  
 このトピックの情報を使用して、データ ソースを構築してください。 手順については、「 [データ接続を追加および確認する (レポート ビルダーおよび SSRS)](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)」を参照してください。  
  
##  <a name="Connection"></a> 接続文字列  
 レポート モデルをデータ ソースとして使用する場合、接続文字列は必要ありません。 レポート モデルに接続するには、レポート サーバーまたは SharePoint サイトを参照してパブリッシュしたモデルを選びます。 SharePoint サイトでのレポート モデルのファイル名拡張子は .smdl です。  
  
 接続文字列の例の詳細については、「 [レポート ビルダーでのデータ接続、データ ソース、および接続文字列](http://msdn.microsoft.com/library/7e103637-4371-43d7-821c-d269c2cc1b34)」を参照してください。  
  
  
##  <a name="Credentials"></a> [資格情報]  
 クエリの実行、ローカルでのレポートのプレビュー、およびレポート サーバーからのレポートのプレビューには、資格情報が必要です。  
  
 レポートをパブリッシュした後、レポートをレポート サーバーで実行するときに、データを取得するための権限が有効な状態になるように、データ ソースの資格情報を変更する必要が生じる場合があります。  
  
 詳細については、「 [レポート ビルダーでの資格情報の指定](http://msdn.microsoft.com/library/7412ce68-aece-41c0-8c37-76a0e54b6b53)」を参照してください。  
  
  
##  <a name="Query"></a> クエリ  
 エンティティ、フィールド、およびクエリのフィルターを対話的に指定するには、レポート モデル クエリ デザイナーを使用します。 モデルのエンティティやフィールドが、レポート データ ペインに表示されるデータセット フィールド コレクションになります。  
  
  
##  <a name="Parameters"></a> パラメーター  
 レポート パラメーターを追加するには、レポート モデル クエリ デザイナーのプロンプトでフィルターを作成します。  
  
 レポート パラメーターは、既定のプロパティ値を使用して作成されます。この既定のプロパティ値は、変更が必要になることがあります。 各レポート パラメーターの既定のデータ型は **Text**です。 基になるデータのデータ型が異なる場合は、パラメーターのデータ型を変更する必要があります。  
  
 詳細については、「 [レポート パラメーター (レポート ビルダーおよびレポート デザイナー)](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)にあります。  
  
  
##  <a name="Remarks"></a> 解説  
 このデータ プロバイダーでは使用できないレポート配信モードもあります。 このデータ処理拡張機能では、データ ドリブン サブスクリプションを使ったレポートの配信はサポートされません。 詳細については、「[サブスクライバー データに対して外部データ ソースを使用する (データ ドリブン サブスクリプション)](../../reporting-services/subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md)」を参照してください。  
  
  
##  <a name="HowTo"></a> 操作方法に関するトピック  
 データ接続、データ ソース、およびデータセットを操作する手順について説明します。  
  
 [データ接続を追加および確認する (レポート ビルダーおよび SSRS)](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [共有データセットまたは埋め込みデータセットの作成 (レポート ビルダーおよび SSRS)](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [データセットへのフィルターの追加 (レポート ビルダーおよび SSRS)](../../reporting-services/report-data/add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
  
##  <a name="Related"></a> 関連項目  
 次に示すセクションでは、レポート データの概念が詳細に説明されているほか、データに関連するレポートのパーツを定義し、カスタマイズし、使用する方法が説明されています。  
  
 [レポート データセット (SSRS)](../../reporting-services/report-data/report-datasets-ssrs.md)  
 レポートのデータへのアクセスの概要について説明します。  
  
 [レポート ビルダーでのデータ接続、データ ソース、および接続文字列](http://msdn.microsoft.com/library/7e103637-4371-43d7-821c-d269c2cc1b34)  
 データ接続とデータ ソースについて説明します。  
  
 [レポート埋め込みデータセットと共有データセット (レポート ビルダーおよび SSRS)](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 埋め込みデータセットと共有データセットについて説明します。  
  
 [データセット フィールド コレクション (レポート ビルダーおよび SSRS)](../../reporting-services/report-data/dataset-fields-collection-report-builder-and-ssrs.md)  
 クエリによって生成されるデータセット フィールド コレクションについて説明します。  
  
 [Reporting Services でサポートされるデータ ソース &#40;SSRS&#41;](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md) ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [オンライン ブックの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ドキュメント](http://go.microsoft.com/fwlink/?linkid=121312))。  
 各データ拡張機能のプラットフォームおよびバージョン サポートに関する詳細な情報です。  
  
  
## <a name="see-also"></a>参照  
 [レポートの検索、表示、管理 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)   
 [レポート パラメーター (レポート ビルダーおよびレポート デザイナー)](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [データのフィルター、グループ化、および並べ替え (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [式 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)  
  
  
