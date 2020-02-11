---
title: MDX のための Analysis Services の接続の種類 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: bd2e7148-3124-4e07-9734-22333127c3be
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: dbd62eff94b1a885198c62a9a36cb8eef7ba57c7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68892126"
---
# <a name="analysis-services-connection-type-for-mdx-ssrs"></a>MDX のための Analysis Services の接続の種類 (SSRS)
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]キューブのデータをレポートに含めるには、種類[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]がのレポートデータソースに基づくデータセットが必要です。 このビルトイン データ ソースの種類は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データ拡張機能に基づいています。 ディメンション、階層、レベル、主要業績評価指標 (kpi)、メジャー、および属性に関するメタデータを[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]キューブから取得して、レポートデータとして使用することができます。  
  
 このデータ処理拡張機能は、複数の値を持つパラメーター、サーバー集計、および接続文字列とは別に管理される資格情報をサポートしています。  
  
 このトピックの情報を使用して、データ ソースを構築してください。 詳細な手順については、「[データ接続またはデータソース &#40;レポートビルダーと SSRS&#41;の追加と検証](add-and-verify-a-data-connection-report-builder-and-ssrs.md)」を参照してください。  
  
##  <a name="Connection"></a>接続文字列  
 
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] キューブに接続する場合は、サーバー上の Analysis Services インスタンスのデータベース オブジェクトに接続します。 データベースには、複数のキューブが構成されている場合があります。 クエリ デザイナーでのキューブの指定は、クエリの作成時に行います。 接続文字列の例を次に示します。  
  
```  
data source=<server name>;initial catalog=<database name>  
```  
  
 接続文字列の例の詳細については、「 [レポート ビルダーでのデータ接続、データ ソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-report-builder.md)」を参照してください。  
  
  
  
##  <a name="Credentials"></a>認証  
 クエリの実行、ローカルでのレポートのプレビュー、およびレポート サーバーからのレポートのプレビューには、資格情報が必要です。  
  
 レポートをパブリッシュした後、レポートをレポート サーバーで実行するときに、データを取得するための権限が有効な状態になるように、データ ソースの資格情報を変更する必要が生じる場合があります。  
  
 レポート作成クライアントから、次のオプションを使用して資格情報を指定します。  
  
-   現在の Windows ユーザー (統合セキュリティとも呼ばれます)。  
  
-   保存されているユーザー名とパスワードを使用する。  
  
-   ユーザーに資格情報を要求する。 このオプションでは Windows 統合セキュリティのみがサポートされます。  
  
-   資格情報を必要としない。 このオプションを使用するには、レポート サーバーで自動実行アカウントを構成しておく必要があります。 詳しくは、msdn.microsoft.com で [Reporting Services に関するドキュメント](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)の「[自動実行アカウントの構成 &#40;SSRS 構成マネージャー&#41;](https://go.microsoft.com/fwlink/?linkid=121312)」をご覧ください。  
  
 詳細については、「 [Reporting Services のデータ接続、データソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)」または「[レポートビルダーで資格情報を指定する](../specify-credentials-in-report-builder.md)」を参照してください。  
  
  
  
##  <a name="Query"></a>問い合わせ  
 
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データ ソースへのデータ接続を実行したら、データセットを作成して、キューブから取得するデータを指定する多次元式 (MDX) クエリを定義します。 MDX グラフィカル クエリ デザイナーを使用して、データ ソースの基になるデータ構造で参照および選択を行います。  
  
 クエリは、次の方法で指定できます。  
  
-   クエリを対話形式で作成します。 Analysis Services MDX クエリ デザイナーでは、次のビューがサポートされています。  
  
    -   **デザインビュー**ディメンション、メンバー、メンバープロパティ、メジャー、および Kpi をメタデータブラウザーから**データ**ペインにドラッグして、MDX クエリを作成します。 計算されるメンバー ペインから、計算されるメンバーをデータ ペインにドラッグして、追加のデータセット フィールドを定義できます。  
  
    -   **クエリビュー**ディメンション、メンバー、メンバープロパティ、メジャー、および Kpi をメタデータブラウザーからクエリペインにドラッグして、MDX クエリを作成します。 クエリ ペインでは、直接 MDX テキストを編集できます。 計算されるメンバーを計算されるメンバー ペインからクエリ ペインにドラッグして、追加のデータセット フィールドを定義します。  
  
     詳細については、「[Analysis Services の MDX クエリ デザイナーのユーザー インターフェイス (レポート ビルダー)](../analysis-services-mdx-query-designer-user-interface-report-builder.md)」を参照してください。  
  
-   レポートから既存の MDX クエリをインポートします。 
  **[クエリのインポート]** ボタンを使用して、.rdl ファイルを参照し、クエリをインポートします。 クエリは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データ ソースに基づく埋め込みデータセットを含むレポートからインポートできます。 MDX クエリを .mdx ファイルから直接インポートすることはできません。  
  
 デザイン時には、クエリを実行して結果セットを表示します。 クエリの結果は、フラットな行セットとして自動的に取得されます。 クエリの結果セットの列には、データセットのフィールド コレクションが設定されます。 クエリを作成した後、メタデータから生成されたデータセット フィールド コレクションがレポート データ ペインに表示されます。 レポートの実行時には、外部データ ソースから実際のデータが返されます。  
  
 
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データ処理拡張機能では、拡張データセット フィールド プロパティがサポートされています。 これらの値は外部データ ソースから取得できますが、レポート データ ペインには表示されません。 
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] コレクションを使用すれば、`Fields` データ処理拡張機能でサポートされている拡張フィールド プロパティをレポートで使用できます。 データ ソースに値を持つプロパティについては、`FormattedValue`、`Color`、`UniqueName` などの定義済みプロパティの値にアクセスできます。 詳細については、「 [Analysis Services データベースの拡張フィールドプロパティ &#40;SSRS&#41;](extended-field-properties-for-an-analysis-services-database-ssrs.md))」を参照してください。  
  
  
  
##  <a name="Parameters"></a> パラメーター  
 クエリ パラメーターを含めるには、クエリ デザイナーのフィルター領域でフィルターを作成し、そのフィルターをパラメーターとして設定します。 各パラメーターに対して、使用可能な値を提供するデータセットが自動的に作成されます。 既定では、これらのデータセットはレポート データ ペインに表示されません。 詳細については、「[Analysis Services の MDX クエリ デザイナーでのパラメーターの定義 &#40;レポート ビルダーおよび SSRS&#41;](define-parameters-in-the-mdx-query-designer-for-analysis-services.md)」と「[多次元データのパラメーター値の非表示データセットの表示 &#40;レポート ビルダーおよび SSRS&#41;](show-hidden-datasets-for-parameter-values-multidimensional-data.md)」を参照してください。  
  
 各レポート パラメーターの既定のデータ型は **Text**です。 レポート パラメーターを作成した後に、既定値の変更が必要になる場合があります。 詳細については、「 [レポート パラメーター (レポート ビルダーおよびレポート デザイナー)](../report-design/report-parameters-report-builder-and-report-designer.md)にあります。  
  
  
  
##  <a name="Remarks"></a> 解説  
 Analysis Services データ拡張機能は、XMLA (XML for Analysis) プロトコルに基づいています。 キューブからの結果セットは、XMLA プロトコルを使用して、フラットな行セットとして取得されます。 不規則階層はサポートされていません。 詳細については、「 [不規則階層](https://docs.microsoft.com/analysis-services/multidimensional-models/user-defined-hierarchies-ragged-hierarchies)」を参照してください。  
  
 
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] キューブからのデータの取得は、OLE DB のデータ ソースの種類を使用して行うこともできます。 詳細については、「[OLE DB の接続の種類 &#40;SSRS&#41;](ole-db-connection-type-ssrs.md)」を参照してください。  
  
 バージョン サポートの詳細については、[](../create-deploy-and-manage-mobile-and-paginated-reports.md) オンライン ブック[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]にある  ドキュメントの「[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Reporting Services でサポートされるデータ ソース &#40;SSRS&#41;](https://go.microsoft.com/fwlink/?linkid=121312)」を参照してください。  
  
  
  
##  <a name="Related"></a>関連セクション  
 次に示すセクションでは、レポート データの概念が詳細に説明されているほか、データに関連するレポートのパーツを定義、カスタマイズ、および使用する手順が説明されています。  
  
 [レポート &#40;レポートビルダーおよび SSRS&#41;にデータを追加する](report-datasets-ssrs.md)  
 レポートのデータへのアクセスの概要について説明します。  
  
 [レポート ビルダーでのデータ接続、データ ソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 データ接続とデータ ソースについて説明します。  
  
 [レポート埋め込みデータセットと共有データセット (レポート ビルダーおよび SSRS)](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 埋め込みデータセットと共有データセットについて説明します。  
  
 [データセット フィールド コレクション &#40;レポート ビルダーおよび SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md)  
 クエリによって生成されるデータセット フィールド コレクションについて説明します。  
  
 [SSRS&#41;&#40;の Analysis Services データベースの拡張フィールドプロパティ](extended-field-properties-for-an-analysis-services-database-ssrs.md)  
 XMLA データ プロバイダーで使用できるその他のフィールドについて説明します。  
  
 [Reporting Services によってサポートされるデータソース &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [オンラインブック](https://go.microsoft.com/fwlink/?linkid=121312)の[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]ドキュメントを参照してください。  
 各データ拡張機能のプラットフォームおよびバージョン サポートに関する詳細な情報です。  
  
  
  
## <a name="see-also"></a>参照  
 [レポート パラメーター (レポート ビルダーおよびレポート デザイナー)](../report-design/report-parameters-report-builder-and-report-designer.md)   
 [データのフィルター、グループ化、および並べ替え (レポート ビルダーおよび SSRS)](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [式 &#40;レポート ビルダーおよび SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
