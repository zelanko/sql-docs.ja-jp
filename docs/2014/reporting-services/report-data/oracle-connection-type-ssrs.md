---
title: Oracle の接続の種類 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 9db86dd2-beda-42d8-8af7-2629d58a8e3d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0021f77134075e18bcae4f3caeea92c1cbcdae73
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66107195"
---
# <a name="oracle-connection-type-ssrs"></a>Oracle の接続の種類 (SSRS)
  Oracle データベースのデータをレポートで使用するには、種類が Oracle のレポート データ ソースに基づいたデータセットが必要です。 このビルトイン データ ソースの種類は、.NET Framework Managed Provider for Oracle に基づいており、Oracle クライアント ソフトウェア コンポーネントが必要です。  
  
 このトピックの情報を使用して、データ ソースを構築してください。 詳細な手順については、「[データ接続またはデータソース &#40;レポートビルダーと SSRS&#41;の追加と検証](add-and-verify-a-data-connection-report-builder-and-ssrs.md)」を参照してください。  
  
##  <a name="connection-string"></a><a name="Connection"></a>接続文字列  
 データ ソースへの接続に使用する接続情報および資格情報については、データベース管理者に問い合わせてください。 次に示す接続文字列の例では、Unicode を使用して "Oracle9" というサーバー上の Oracle データベースを指定しています。 サーバー名は、Tnsnames.ora 構成ファイルで Oracle サーバー インスタンス名として定義されたものと一致する必要があります。  
  
```  
Data Source="Oracle9"; Unicode="True"  
```  
  
 接続文字列の例の詳細については、「 [レポート ビルダーでのデータ接続、データ ソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-report-builder.md)」を参照してください。  
  
##  <a name="credentials"></a><a name="Credentials"></a>認証  
 クエリの実行、ローカルでのレポートのプレビュー、およびレポート サーバーからのレポートのプレビューには、資格情報が必要です。  
  
 レポートをパブリッシュした後、レポートをレポート サーバーで実行するときに、データを取得するための権限が有効な状態になるように、データ ソースの資格情報を変更する必要が生じる場合があります。  
  
 詳細については、「 [Reporting Services のデータ接続、データソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)」または「[レポートビルダーで資格情報を指定する](../specify-credentials-in-report-builder.md)」を参照してください。  
  

  
##  <a name="queries"></a><a name="Query"></a>問い合わせ  
 データセットを作成するには、ボックスの一覧からストアド プロシージャを選択するか、SQL クエリを作成します。 クエリを作成するには、テキストベースのクエリ デザイナーを使用する必要があります。 詳細については、「[テキストベースのクエリ デザイナーのユーザー インターフェイス &#40;レポート ビルダー&#41;](text-based-query-designer-user-interface-report-builder.md)」を参照してください。  
  
 結果セットを 1 つだけ返すストアド プロシージャを指定できます。 カーソル ベースのクエリは使用できません。  
  
##  <a name="parameters"></a><a name="Parameters"></a>パラメータ  
 クエリにクエリ変数が含まれている場合は、対応するレポート パラメーターが自動的に生成されます。 この拡張機能では、名前付きパラメーターがサポートされます。 Oracle Version 9 以降の場合、複数値パラメーターがサポートされます。  
  
 レポート パラメーターは、既定のプロパティ値を使用して作成されます。この既定のプロパティ値は、変更が必要になることがあります。 たとえば、各レポート パラメーターのデータ型は **Text**です。 レポート パラメーターを作成した後に、既定値の変更が必要になる場合があります。 詳細については、「 [レポート パラメーター (レポート ビルダーおよびレポート デザイナー)](../report-design/report-parameters-report-builder-and-report-designer.md)にあります。  
  

  
##  <a name="remarks"></a><a name="Remarks"></a> 解説  
 Oracle データ ソースに接続するには、システム管理者が、Oracle データベースからのデータの取得をサポートするバージョンの .NET Data Provider for Oracle をインストールしておく必要があります。 このデータ プロバイダーは、レポート ビルダーがインストールされているコンピューターとレポート サーバーにインストールされている必要があります。  
  
 詳細については、「  
  
-   msdn.microsoft.com の「[.NET Framework Data Provider for Oracle の使用](https://go.microsoft.com/fwlink/?LinkId=112314) 」  
  
-   [Reporting Services を使用して Oracle データ ソースの構成およびアクセスを行う方法](https://support.microsoft.com/kb/834305)  
  
-   [NETWORK SERVICE セキュリティ プリンシパルに権限を追加する方法](https://support.microsoft.com/kb/870668)  
  
###### <a name="alternate-data-extensions"></a>代替データ拡張機能  
 Oracle データベースからのデータの取得は、OLE DB のデータ ソースの種類を使用して行うこともできます。 詳細については、「[OLE DB の接続の種類 &#40;SSRS&#41;](ole-db-connection-type-ssrs.md)」を参照してください。  
  
###### <a name="report-models"></a>レポート モデル  
 Oracle データベースに基づくモデルを作成することもできます。  
  
###### <a name="platform-and-version-information"></a>プラットフォームおよびバージョン情報  
 プラットフォームおよびバージョン サポートの詳細については、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [オンライン ブック](https://go.microsoft.com/fwlink/?linkid=121312)にある [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ドキュメントの「[Reporting Services でサポートされるデータ ソース (SSRS)](../create-deploy-and-manage-mobile-and-paginated-reports.md)」を参照してください。  
  

  
##  <a name="how-to-topics"></a><a name="HowTo"></a>操作方法に関するトピック  
 データ接続、データ ソース、およびデータセットを操作する手順について説明します。  
  
 [データ接続またはデータソース &#40;レポートビルダーと SSRS&#41;に追加して検証する](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [共有データセットまたは埋め込みデータセットの作成 (レポート ビルダーおよび SSRS)](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [データセットへのフィルターの追加 (レポート ビルダーおよび SSRS)](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
 
  
##  <a name="related-sections"></a><a name="Related"></a> 関連セクション  
 次に示すセクションでは、レポート データの概念が詳細に説明されているほか、データに関連するレポートのパーツを定義し、カスタマイズし、使用する方法が説明されています。  
  
 [レポート &#40;レポートビルダーおよび SSRS&#41;にデータを追加する](report-datasets-ssrs.md)  
 レポートのデータへのアクセスの概要について説明します。  
  
 [レポート ビルダーでのデータ接続、データ ソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 データ接続とデータ ソースについて説明します。  
  
 [レポート埋め込みデータセットと共有データセット &#40;レポートビルダーと SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 埋め込みデータセットと共有データセットについて説明します。  
  
 [データセット フィールド コレクション &#40;レポート ビルダーおよび SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md)  
 クエリによって生成されるデータセット フィールド コレクションについて説明します。  
  
 [Reporting Services でサポートされるデータ ソース &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [オンライン ブックの [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ドキュメント](https://go.microsoft.com/fwlink/?linkid=121312))。  
 各データ拡張機能のプラットフォームおよびバージョン サポートに関する詳細な情報です。  
  

  
## <a name="see-also"></a>参照  
 [レポートパラメーター &#40;レポートビルダーとレポートデザイナー&#41;](../report-design/report-parameters-report-builder-and-report-designer.md)   
 [データのフィルター処理、グループ化、並べ替え &#40;レポートビルダーと SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [式 &#40;レポート ビルダーおよび SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
