---
title: "SQL Server の各エディションがサポートする Integration Services の機能 | Microsoft Docs"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: integration-services
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5018225-68bb-4f34-ae4a-ead79d8ad13a
caps.latest.revision: "15"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 9d7a5ad6abf892a9b8ab0b125336e13cf1318100
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2017
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
|Scale Out Master|はい|||||
|Scale Out Worker|はい|可 <sup>1</sup>|TBD|TBD|TBD|
|OData コンポーネントで Microsoft Dynamics AX および Microsoft Dynamics CRM をサポート <sup>2</sup>|はい|はい||||

<sup>1</sup> Scale Out で Enterprise のみの機能を必要とするパッケージを実行する場合は、Scale Out Worker を SQL Server Enterprise のインスタンスでも実行する必要があります。

<sup>2</sup> この機能は、SQL Server 2016 Service Pack 1 でもサポートされています。

## <a name="IEWiz"></a> SQL Server インポートおよびエクスポート ウィザード

|機能|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|SQL Server インポートおよびエクスポート ウィザード|可|可|可|可|はい|  

## <a name="IS"></a> Integration Services  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|組み込みのデータ ソース コネクタ|可|可|||| 
|組み込みのタスクと変換|可|はい||||  
|Attunity ODBC ソース/ターゲット|はい|可|||| 
|Azure データ ソース コネクタおよびタスク|可|はい||||  
|Hadoop/HDFS コネクタおよびタスク|はい|可||||  
|基本的なデータ プロファイリング ツール|可|はい|||| 

## <a name="ISAA"></a> Integration Services – 高度なソース/ターゲット  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Attunity 高パフォーマンス Oracle ソース/ターゲット|はい|||||  
|Attunity 高パフォーマンス Teradata ソース/ターゲット|はい|||||  
|SAP BW 変換元と変換先|はい|||||  
|データ マイニング モデル トレーニング変換先|はい|||||  
|ディメンション処理変換先|はい|||||  
|パーティション処理変換先|はい|||||  
  
## <a name="ISAT"></a> Integration Services - 高度なタスクおよび変換  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Attunity 変更データ キャプチャ コンポーネント <sup>1</sup>|はい|||||  
|データ マイニング クエリ変換|はい|||||  
|あいまいグループ化とあいまい参照変換|はい|||||  
|用語抽出および用語参照変換|はい|||||  

<sup>1</sup> Attunity 変更データ キャプチャ コンポーネントには Enterprise Edition が必要です。 ただし、Change Data Capture Service と Change Data Capture Designer では Enterprise Edition は不要です。 Designer および Service は、SSIS がインストールされていないコンピューターで使用できます。
