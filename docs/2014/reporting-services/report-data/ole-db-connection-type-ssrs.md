---
title: OLE DB の接続の種類 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d00cb13b-e1c2-4300-a195-3da1430a2df1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9d79ef7ae57894470f58701fd51a1d9ddd1b7126
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68891985"
---
# <a name="ole-db-connection-type-ssrs"></a>OLE DB の接続の種類 (SSRS)
  OLE DB データ プロバイダーのデータを含めるには、種類が OLE DB のレポート データ ソースに基づいたデータセットが必要です。 このビルトイン データ ソースの種類は、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] OLE DB データ処理拡張機能に基づいています。  
  
 OLE DB は、クライアントがさまざまなデータ プロバイダーに接続できるようにするデータ アクセス テクノロジです。 データ ソースの種類に OLE DB を選択したら、特定のデータ プロバイダーを選択する必要があります。 パラメーターや資格情報などの機能のサポートは、選択したデータ プロバイダーによって異なります。  
  
 このトピックの情報を使用して、データ ソースを構築してください。 詳細な手順については、「[データ接続またはデータソース &#40;レポートビルダーと SSRS&#41;の追加と検証](add-and-verify-a-data-connection-report-builder-and-ssrs.md)」を参照してください。  
  
##  <a name="connection-string"></a><a name="Connection"></a> 接続文字列  
 OLE DB データ処理拡張機能の接続文字列は、使用するデータ プロバイダーに依存します。 一般的な接続文字列は、データ プロバイダーでサポートされる名前と値のペアで構成されます。 たとえば、次の接続文字列は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client の OLE DB プロバイダーおよび AdventureWorks データベースを指定しています。  
  
```  
Provider=SQLNCLI10.1;Data Source=server; Initial Catalog=AdventureWorks  
```  
  
 使用する接続文字列は、接続先の外部データ ソースによって異なります。 データ プロバイダーに固有の接続文字列プロパティを設定するには、 **[データ ソースのプロパティ]** ダイアログ ボックスの **[全般]** ページで **[構築]** ボタンをクリックし、 **[接続プロパティ]** ダイアログ ボックスを開きます。 **[データ リンク プロパティ]** ダイアログ ボックスで、拡張データ ソース プロパティを設定します。  
  
 接続文字列の例については、「 [レポート ビルダーでのデータ接続、データ ソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-report-builder.md)」を参照してください。  
  
  
  
##  <a name="credentials"></a><a name="Credentials"></a> [資格情報]  
 クエリの実行、ローカルでのレポートのプレビュー、およびレポート サーバーからのレポートのプレビューには、資格情報が必要です。  
  
 レポートをパブリッシュした後、レポートをレポート サーバーで実行するときに、データを取得するための権限が有効な状態になるように、データ ソースの資格情報を変更する必要が生じる場合があります。  
  
 詳細については、「 [Reporting Services のデータ接続、データソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)」または「[レポートビルダーで資格情報を指定する](../specify-credentials-in-report-builder.md)」を参照してください。  
  
###### <a name="special-characters-in-a-password"></a>パスワードの特殊文字  
 OLE DB データ ソースの構成時に、パスワードが要求されるように設定したり、接続文字列にパスワードを含めた場合、ユーザーによって入力されたパスワードに句読点などの特殊文字が含まれていると、基になるデータ ソースのドライバーによってはその特殊文字を検証することができません。 レポートを処理する際に、この問題によって、"パスワードが無効です" というメッセージが表示される場合があります。  
  
> [!NOTE]  
>  パスワードなどのログイン情報を接続文字列に追加しないことをお勧めします。 レポート ビルダーでは、 **[データ ソース]** ダイアログ ボックスに、資格情報の入力に使用できるタブが別に用意されています。  
  
  
  
##  <a name="parameters"></a><a name="Parameters"></a> パラメーター  
 OLE DB プロバイダーによっては、無名パラメーターはサポートされても名前付きパラメーターはサポートされない場合があります。 パラメーターは、クエリ内でプレースホルダーを使用して位置を指定することで渡されます。 プレースホルダー文字は、データ プロバイダーによってサポートされている構文で決まります。  
  
 
  
##  <a name="remarks"></a><a name="Remarks"></a> 解説  
 OLEDB は、特定のデータ ソースのデータ プロバイダーを作成するためのネイティブ テクノロジです。 COM (コンポーネント オブジェクト モデル) インターフェイスを基盤とした、 ODBC よりも新しく ADO.NET データ プロバイダーよりも古いテクノロジです。 OLEDB データ プロバイダーは、他の COM コンポーネントと同様にオペレーティング システムに登録されます。 OLEDB データ プロバイダーはマイクロソフトとサード パーティ ベンダーから入手できます。 マイクロソフトは、ODBC ドライバーとの通信を仲介する OLEDB データ プロバイダーである MSDASQL も提供しています。 詳細については、「[ODBC 接続の種類 &#40;SSRS&#41;](odbc-connection-type-ssrs.md)」を参照してください。  
  
 目的のデータを正常に取得するには、データ プロバイダーでサポートされるクエリ構文を使用する必要があります。 サポートされるパラメーターはデータ プロバイダーによって異なります。 詳細については、使用するデータ プロバイダー向けのトピックを参照してください。 次に例を示します。  
  
-   [Analysis Services OLE DB Provider &#40;Analysis Services - 多次元データ&#41;](../../analysis-services/dev-guide/analysis-services-ole-db-provider-analysis-services-multidimensional-data.md)  
  
-   [.NET Framework Data Provider for Oracle の使用](https://go.microsoft.com/fwlink/?LinkId=112314)  
  
-   [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
 特定の OLE DB データ プロバイダーの詳細については、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のドキュメント ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [オンライン ブック](https://go.microsoft.com/fwlink/?linkid=121312)) の「[Reporting Services でサポートされるデータ ソース &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md)」を参照してください。  
  
  
  
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
  
 [Reporting Services でサポートされるデータ ソース &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [オンライン ブックの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ドキュメント](https://go.microsoft.com/fwlink/?linkid=121312))。  
 各データ拡張機能のプラットフォームおよびバージョン サポートに関する詳細な情報です。  
  
 
  
## <a name="see-also"></a>参照  
 [レポートパラメーター &#40;レポートビルダーとレポートデザイナー&#41;](../report-design/report-parameters-report-builder-and-report-designer.md)   
 [データのフィルター処理、グループ化、並べ替え &#40;レポートビルダーと SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [式 &#40;レポート ビルダーおよび SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
