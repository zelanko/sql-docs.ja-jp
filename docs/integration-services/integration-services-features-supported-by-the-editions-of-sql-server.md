---
title: SQL Server の各エディションがサポートする Integration Services の機能 | Microsoft Docs
ms.custom: ''
ms.date: 07/26/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: e5018225-68bb-4f34-ae4a-ead79d8ad13a
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 4d1b99431f48d9bbf9b53bb57f1b0bcf2291a6c1
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/20/2019
ms.locfileid: "58276218"
---
# <a name="integration-services-features-supported-by-the-editions-of-sql-server"></a>SQL Server の各エディションがサポートする Integration Services の機能
 このトピックでは、 [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)]のさまざまなエディションでサポートされる SQL Server Integration Services (SSIS) の機能の詳細について説明します。  

Evaluation Edition と Developer Edition でサポートされている機能については、下の表に記載されている Enterprise Edition の機能をご覧ください。
  
最新のリリース ノートと新機能については、以下の記事を参照してください。
-   [SQL Server 2016 リリース ノート](../sql-server/sql-server-2016-release-notes.md)
-   [SQL Server 2016 の Integration Services の新機能](../integration-services/what-s-new-in-integration-services-in-sql-server-2016.md)
-   [SQL Server 2017 の Integration Services の新機能](../integration-services/what-s-new-in-integration-services-in-sql-server-2017.md)
    
**SQL Server 2016 をお試しください。**    

180 日の試用期間中、SQL Server Evaluation Edition をご利用いただけます。  
    
> [![Evaluation Center からダウンロードする](../analysis-services/media/download.png)](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016) **[Evaluation Center から SQL Server 2016 をダウンロードする](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016)**    
    
## <a name="ISNew"></a> SQL Server 2017 の新しい Integration Services 機能
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Scale Out Master|可|||||
|Scale Out Worker|可|はい <sup>1</sup>|TBD|TBD|TBD|
|OData コンポーネントで Microsoft Dynamics AX および Microsoft Dynamics CRM をサポート <sup>2</sup>|可|可||||

<sup>1</sup> Scale Out で Enterprise のみの機能を必要とするパッケージを実行する場合は、Scale Out Worker を SQL Server Enterprise のインスタンスでも実行する必要があります。

<sup>2</sup> この機能は、SQL Server 2016 Service Pack 1 でもサポートされています。

## <a name="IEWiz"></a> SQL Server インポートおよびエクスポート ウィザード

|機能|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|SQL Server インポートおよびエクスポート ウィザード|可|[はい]|[はい]|[はい]|可|  

## <a name="IS"></a> Integration Services  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|組み込みのデータ ソース コネクタ|可|可|||| 
|組み込みのタスクと変換|可|可||||  
|ODBC のソースとターゲット |可|可|||| 
|Azure データ ソース コネクタおよびタスク|可|可||||  
|Hadoop/HDFS コネクタおよびタスク|可|可||||  
|基本的なデータ プロファイリング ツール|可|可|||| 

## <a name="ISAA"></a> Integration Services – 高度なソース/ターゲット  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Attunity 高パフォーマンス Oracle ソース/ターゲット|可|||||  
|Attunity 高パフォーマンス Teradata ソース/ターゲット|可|||||  
|SAP BW 変換元と変換先|可|||||  
|データ マイニング モデル トレーニング変換先|可|||||  
|ディメンション処理変換先|可|||||  
|パーティション処理変換先|可|||||  
  
## <a name="ISAT"></a> Integration Services - 高度なタスクおよび変換  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Attunity 変更データ キャプチャ コンポーネント <sup>1</sup>|可|||||  
|データ マイニング クエリ変換|可|||||  
|あいまいグループ化とあいまい参照変換|可|||||  
|用語抽出および用語参照変換|可|||||  

<sup>1</sup> Attunity 変更データ キャプチャ コンポーネントには Enterprise Edition が必要です。 ただし、Change Data Capture Service と Change Data Capture Designer では Enterprise Edition は不要です。 Designer および Service は、SSIS がインストールされていないコンピューターで使用できます。
