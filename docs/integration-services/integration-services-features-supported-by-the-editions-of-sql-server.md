---
title: "Integration Services の SQL Server のエディションでサポートされる機能 |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: integration-services
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5018225-68bb-4f34-ae4a-ead79d8ad13a
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 8cc1fcfdeae8742a93916dfb08c9db1215f88721
ms.openlocfilehash: e9d1b8851f113fa44264230a79d0e496007ed96b
ms.contentlocale: ja-jp
ms.lasthandoff: 10/17/2017

---
# <a name="integration-services-features-supported-by-the-editions-of-sql-server"></a>SQL Server のエディションでサポートされている integration Services 機能
 このトピックでは、 [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)]のさまざまなエディションでサポートされる SQL Server Integration Services (SSIS) の機能の詳細について説明します。  

Evaluation および Developer エディションでサポートされる機能、Enterprise Edition の次の表に示された機能を参照してください。
  
最新のリリース ノートと新しい情報は、次の記事を参照してください。
-   [SQL Server 2016 リリース ノート](../sql-server/sql-server-2016-release-notes.md)
-   [SQL Server 2016 の Integration Services の新機能](../integration-services/what-s-new-in-integration-services-in-sql-server-2016.md)
-   [SQL Server 2017 の Integration Services の新機能](../integration-services/what-s-new-in-integration-services-in-sql-server-2017.md)
    
**SQL Server 2016 をお試しください。**    

180 日の試用期間中、SQL Server Evaluation Edition をご利用いただけます。  
    
> [![Evaluation Center からダウンロードする](../analysis-services/media/download.png)](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016) **[Evaluation Center から SQL Server 2016 をダウンロードする](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016)**    
    
## <a name="ISNew"></a>SQL Server 2017 で新しい Integration Services の機能
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|スケール アウト マスター|はい|||||
|スケール アウト ワーカー|はい|可 <sup>1</sup>|TBD|TBD|TBD|
|Microsoft Dynamics AX および Microsoft Dynamics CRM OData コンポーネントでサポート<sup>2</sup>|はい|はい||||

<sup>1</sup>スケール アウト ワーカーが、SQL Server Enterprise のインスタンスで実行する必要がありますもスケール アウトの企業専用の機能を必要とするパッケージを実行する場合。

<sup>2</sup> Service Pack 1 の SQL Server 2016 では、この機能はサポートされてもします。

## <a name="IEWiz"></a>SQL Server インポートおよびエクスポート ウィザード

|機能|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|SQL Server インポートおよびエクスポート ウィザード|可|可|可|可|はい|  

## <a name="IS"></a> Integration Services  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|組み込みのデータ ソース コネクタ|可|可|||| 
|組み込みのタスクと変換|可|はい||||  
|Odbc 入力元および by Attunity の変換先|はい|可|||| 
|Azure データ ソース コネクタおよびタスク|可|はい||||  
|Hadoop と HDFS コネクタおよびタスク|はい|可||||  
|基本的なデータ プロファイリング ツール|可|はい|||| 

## <a name="ISAA"></a>Integration Services – 拡張元および変換先  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|高パフォーマンスの Oracle ソースと by Attunity の変換先|はい|||||  
|高パフォーマンスの Teradata 変換元と by Attunity の変換先|はい|||||  
|SAP BW 変換元と変換先|はい|||||  
|データ マイニング モデル トレーニング変換先|はい|||||  
|ディメンション処理変換先|はい|||||  
|パーティション処理変換先|はい|||||  
  
## <a name="ISAT"></a>Integration Services – 詳細なタスクおよび変換  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|変更データ キャプチャ コンポーネント by Attunity <sup>1</sup>|はい|||||  
|データ マイニング クエリ変換|はい|||||  
|あいまいグループ化とあいまい参照変換|はい|||||  
|用語抽出と用語参照変換|はい|||||  

<sup>1</sup> by Attunity の Change Data Capture コンポーネントには Enterprise edition が必要とします。 Change Data Capture Service と Change Data Capture Designer、ただし、不要 Enterprise edition です。 使用できます、Designer および Service コンピューターに SSIS がインストールされていません。

