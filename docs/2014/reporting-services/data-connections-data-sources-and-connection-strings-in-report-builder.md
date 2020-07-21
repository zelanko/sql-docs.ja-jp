---
title: レポートビルダーのデータ接続、データソース、および接続文字列 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10421"
ms.assetid: 7e103637-4371-43d7-821c-d269c2cc1b34
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: eb8d81c9c47f00ed84036accf86768d084072c4d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66109489"
---
# <a name="data-connections-data-sources-and-connection-strings-in-report-builder"></a>レポート ビルダーでのデータ接続、データ ソース、および接続文字列
  データをレポートに含めるには、データ接続とデータセットを作成します。 データ接続には、外部データ ソースにアクセスする方法に関する情報が含まれています。 データセットには、データ接続を使用して取得するデータを指定するクエリ コマンドが含まれています。  
  
1.  **レポート データ ペインのデータ ソース** 埋め込みデータ ソースを作成するか、共有データ ソースを追加すると、レポート データ ペインにデータ ソースが表示されます。  
  
2.  **[接続] ダイアログ ボックス** 接続文字列を作成したり、接続文字列を貼り付けたりするには、[接続] ダイアログ ボックスを使用します。  
  
3.  **データ接続情報** 接続文字列は、データ拡張機能に渡されます。  
  
4.  **資格情報** 資格情報は、接続文字列とは別個に管理されます。  
  
5.  **データ拡張機能/データ プロバイダー** データへの接続は、複数のデータ アクセス レイヤーを通じて行われる場合があります。  
  
6.  **外部データ ソース** リレーショナル データベース、多次元データベース、SharePoint リスト、Web サービス、またはレポート モデルからデータを取得します。  
  
 詳細については、「[埋め込みデータ接続と共有データ接続またはデータソース &#40;レポートビルダーと SSRS&#41;](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md) 」と「データ[接続、データソース、および接続 Reporting Services 文字列](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)」を参照してください。  
  
 定義済みの共有データ ソース、共有データセット、およびレポート パーツを使用してデータをレポートに含めることもできます。 これらのアイテムには、必要な接続情報は既に存在します。 詳細については、「[レポート &#40;レポートビルダーおよび SSRS&#41;にデータを追加する](report-data/report-datasets-ssrs.md)」を参照してください。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../includes/ssrbrddup-md.md)]  
  
 ![rs_DataSourcesStory](media/rs-datasourcesstory.gif "rs_DataSourcesStory")  
  
##  <a name="connection-string-examples"></a><a name="ConnectionString"></a>接続文字列の例  
 データ接続には、通常は外部データ ソースの所有者によって提供される接続文字列が含まれています。 次の表に、各種の外部データ ソースの接続文字列の例を示します。  
  
|**データ ソース**|**例**|**説明**|  
|---------------------|-----------------|---------------------|  
|ローカル サーバー上の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データベース|`data source="(local)";initial catalog=AdventureWorks2012`|データソースの種類を`SQL Server`に設定します。|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンス データベース|`Data Source=localhost\MSSQL12.InstanceName; Initial Catalog= AdventureWorks2012`|データソースの種類を`SQL Server`に設定します。|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Express データベース|`Data Source=localhost\MSSQL12.SQLEXPRESS; Initial Catalog= AdventureWorks2012`|データソースの種類を`SQL Server`に設定します。|  
|ローカル サーバー上の [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベース|`data source=localhost;initial catalog=Adventure Works DW 2012`|データソースの種類を`SQL Server Analysis Services`に設定します。|  
|SharePoint リスト|`data source=http://MySharePointWeb/MySharePointSite/`|データソースの種類を`SharePoint List`に設定します。|  
||||  
|レポート モデル|適用されません。|レポート モデルに対しては接続文字列は必要はありません。 レポート ビルダーで、レポート サーバーを参照し、そのレポート モデルである .smdl ファイルを選択します。|  
|Oracle サーバー|`data source=myserver`|データ ソースの種類を `Oracle` に設定します。 レポート ビルダーがインストールされているコンピューターとレポート サーバーに、Oracle クライアント ツールがインストールされている必要があります。|  
|SAP NetWeaver BI データ ソース|`DataSource=http://mySAPNetWeaverBIServer:8000/sap/bw/xml/soap/xmla`|データ ソースの種類を `SAP NetWeaver BI` に設定します。|  
|Hyperion Essbase データ ソース|`Data Source=http://localhost:13080/aps/XMLA; Initial Catalog=Sample`|データ ソースの種類を `Hyperion Essbase` に設定します。|  
|Teradata データ ソース|`data source=`* \<NN>。\<NNN>。\<NNN>。N \<>*`;`|データ ソースの種類を `Teradata` に設定します。 接続文字列は、各フィールドが 1 ～ 3 桁の 4 つのフィールドで構成されるインターネット プロトコル (IP) アドレスです。|  
|Teradata データ ソース|`Database=` *\<データベース名>* `; data source=` *\<NN*N *>.\<NNN>.\<NNN>.\<N*NN*>*`;Use X Views=False;Restrict to Default Database=True`|前の例と同様に、データ ソースの種類を `Teradata` に設定します。 Database タグで指定した既定のデータベースのみを使用して、データ間の関係を自動的に検出しないようにしてください。|  
|XML データ ソース、Web サービス|`data source=http://adventure-works.com/results.aspx`|データ ソースの種類を `XML` に設定します。 接続文字列は、Web サービス記述言語 (WSDL) をサポートする Web サービスの URL です。|  
|XML データ ソース、XML ドキュメント|`http://localhost/XML/Customers.xml`|データ ソースの種類を `XML` に設定します。 接続文字列は XML ドキュメントへの URL です。|  
|XML データ ソース、埋め込み XML ドキュメント|*空*|データ ソースの種類を `XML` に設定します。 XML データはレポート定義に埋め込まれています。|  
  
 各接続の種類の詳細については、「 [ssrs&#41;&#40;の外部データソースからのデータの追加](report-data/add-data-from-external-data-sources-ssrs.md)」および「 [Reporting Services &#40;Ssrs&#41;でサポートされるデータソース](create-deploy-and-manage-mobile-and-paginated-reports.md)」を参照してください。  
  

  
##  <a name="creating-data-sources"></a><a name="Creating"></a>データソースの作成  
 埋め込みデータ ソースを作成するには、データへのアクセスに必要な接続文字列と資格情報が必要です。 通常、この情報は、データ ソースの所有者から得られます。 データ接続は、データ ソースの一部としてレポート定義に格納されます。 資格情報は、接続とは別に管理されます。 詳細な手順については、「[データ接続またはデータソース &#40;レポートビルダーと SSRS&#41;の追加と検証](report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)」を参照してください。  
  
> [!NOTE]  
>  資格情報によっては、レポート ビルダーが使用するすべてのシナリオをサポートしていない場合があります。レポート ビルダーが使用するシナリオには、クエリ デザイナーでのクエリの実行、コンピューターがレポート サーバーに接続していない場合のレポートのプレビュー、レポート サーバーからのレポートの実行があります。 可能な限り共有データソースを使用することをお勧めします。 レポート サーバー上の共有データ ソースごとに資格情報を保存できます。 詳細については、「 [レポート ビルダーでの資格情報の指定](../../2014/reporting-services/specify-credentials-in-report-builder.md)」を参照してください。  
  
 共有データソースを作成するには、レポートサーバー上にデータソースを直接作成するためにレポートマネージャーを使用するか、でレポートデザイナーの[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]ような作成環境を使用する必要があります。 詳細については、「 [SSRS&#41;&#40;の埋め込みデータソースまたは共有データソースの作成](../../2014/reporting-services/create-an-embedded-or-shared-data-source-ssrs.md)」を参照してください。  
  

  
## <a name="see-also"></a>参照  
 [レポート &#40;レポートビルダーおよび SSRS&#41;にデータを追加する](report-data/report-datasets-ssrs.md)   
 [レポート パーツ &#40;レポート ビルダーおよび SSRS&#41;](report-parts-report-builder-and-ssrs.md)  
  
  
