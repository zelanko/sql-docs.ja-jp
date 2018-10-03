---
title: Oracle の接続の種類 (SSRS) | Microsoft Docs
ms.date: 01/11/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-data
ms.topic: conceptual
ms.assetid: 9db86dd2-beda-42d8-8af7-2629d58a8e3d
author: markingmyname
ms.author: maghan
ms.openlocfilehash: ee96150a0c83a87cf276c3678d7b9e4758079b69
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47843970"
---
# <a name="oracle-connection-type-ssrs"></a>Oracle の接続の種類 (SSRS)
Oracle データベースのデータをレポートで使用するには、種類が Oracle のレポート データ ソースに基づいたデータセットが必要です。 このビルトイン データ ソースの種類は、Oracle Data Provider を直接使用し、Oracle クライアント ソフトウェア コンポーネントが必要です。

Oracle クライアント ツールをインストールするには、次の操作を実行します。
 
1.  [Oracle のダウンロード サイト](http://www.oracle.com/us/products/tools/index-090165.html)に移動します
2.  Windows 用 ODAC 12c リリース 4 (12.1.0.2.4) をダウンロードします (サーバー用の 64 ビット、ツール用の 32 ビット)。
3.  Data Provider for .NET 4 をインストールします
  
 このトピックの情報を使用して、データ ソースを構築してください。 手順については、「 [データ接続を追加および確認する (レポート ビルダーおよび SSRS)](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)」を参照してください。  
  
##  <a name="Connection"></a> 接続文字列  
 データ ソースへの接続に使用する接続情報および資格情報については、データベース管理者に問い合わせてください。 次に示す接続文字列の例では、Unicode を使用して "Oracle9" というサーバー上の Oracle データベースを指定しています。 サーバー名は、Tnsnames.ora 構成ファイルで Oracle サーバー インスタンス名として定義されたものと一致する必要があります。  
  
```  
Data Source="Oracle"; Unicode="True"  
```  
  
 接続文字列の例の詳細については、「 [レポート ビルダーでのデータ接続、データ ソース、および接続文字列](http://msdn.microsoft.com/library/7e103637-4371-43d7-821c-d269c2cc1b34)」を参照してください。  
  
##  <a name="Credentials"></a> [資格情報]  
 クエリの実行、ローカルでのレポートのプレビュー、およびレポート サーバーからのレポートのプレビューには、資格情報が必要です。  
  
 レポートをパブリッシュした後、レポートをレポート サーバーで実行するときに、データを取得するための権限が有効な状態になるように、データ ソースの資格情報を変更する必要が生じる場合があります。  
  
 詳しくは、「[データ接続、データ ソース、および接続文字列 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)」または「[レポート ビルダーでの資格情報の指定](http://msdn.microsoft.com/library/7412ce68-aece-41c0-8c37-76a0e54b6b53)」を参照してください。  
  
  
##  <a name="Query"></a> クエリ  
 データセットを作成するには、ボックスの一覧からストアド プロシージャを選択するか、SQL クエリを作成します。 クエリを作成するには、テキストベースのクエリ デザイナーを使用する必要があります。 詳細については、「[テキストベースのクエリ デザイナーのユーザー インターフェイス &#40;レポート ビルダー&#41;](../../reporting-services/report-data/text-based-query-designer-user-interface-report-builder.md)」を参照してください。  
  
 結果セットを 1 つだけ返すストアド プロシージャを指定できます。 カーソル ベースのクエリは使用できません。  
  
##  <a name="Parameters"></a> パラメーター  
 クエリにクエリ変数が含まれている場合は、対応するレポート パラメーターが自動的に生成されます。 この拡張機能では、名前付きパラメーターがサポートされます。 Oracle Version 9 以降の場合、複数値パラメーターがサポートされます。  
  
 レポート パラメーターは、既定のプロパティ値を使用して作成されます。この既定のプロパティ値は、変更が必要になることがあります。 たとえば、各レポート パラメーターのデータ型は **Text**です。 レポート パラメーターを作成した後に、既定値の変更が必要になる場合があります。 詳細については、MSDN の「 [レポート パラメーター &#40;レポート ビルダーおよびレポート デザイナー&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)の種類のレポート データ ソースに基づいたデータセットが必要です。  
  
  
##  <a name="Remarks"></a> 解説  
 Oracle データ ソースに接続するには、システム管理者が、Oracle データベースからのデータの取得をサポートするバージョンの .NET Data Provider for Oracle をインストールしておく必要があります。 このデータ プロバイダーは、レポート ビルダーがインストールされているコンピューターとレポート サーバーにインストールされている必要があります。  
  
 詳細については、以下を参照してください。  
  
-   msdn.microsoft.com の「[.NET Framework Data Provider for Oracle の使用](http://go.microsoft.com/fwlink/?LinkId=112314) 」  
  
-   [Reporting Services を使用して Oracle データ ソースの構成およびアクセスを行う方法](http://support.microsoft.com/kb/834305)  
  
-   [NETWORK SERVICE セキュリティ プリンシパルに権限を追加する方法](http://support.microsoft.com/kb/870668)  
  
###### <a name="alternate-data-extensions"></a>代替データ拡張機能  
 Oracle データベースからのデータの取得は、OLE DB のデータ ソースの種類を使用して行うこともできます。 詳細については、「[OLE DB の接続の種類 &#40;SSRS&#41;](../../reporting-services/report-data/ole-db-connection-type-ssrs.md)」を参照してください。  
  
###### <a name="report-models"></a>レポート モデル  
 Oracle データベースに基づくモデルを作成することもできます。  
  
###### <a name="platform-and-version-information"></a>プラットフォームおよびバージョン情報  
 プラットフォームおよびバージョン サポートの詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [オンライン ブック](http://go.microsoft.com/fwlink/?linkid=121312)にある [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ドキュメントの「[Reporting Services でサポートされるデータ ソース (SSRS)](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md)」を参照してください。  
  
  
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
 [レポート パラメーター (レポート ビルダーおよびレポート デザイナー)](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [データのフィルター、グループ化、および並べ替え (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [式 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)  
  
  
