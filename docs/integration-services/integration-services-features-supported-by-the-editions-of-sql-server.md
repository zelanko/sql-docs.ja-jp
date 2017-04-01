---
title: "SQL Server の各エディションがサポートする Integration Services の機能 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e5018225-68bb-4f34-ae4a-ead79d8ad13a
caps.latest.revision: 15
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 14
---
# SQL Server の各エディションがサポートする Integration Services の機能
 このトピックでは、[!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] のさまざまなエディションでサポートされる SQL Server Integration Services (SSIS) の機能の詳細について説明します。  

Evaluation Edition および Developer Edition でサポートされている機能については、SQL Server Enterprise Edition をご覧ください。 
  
最新のリリース ノートと新機能については、以下の情報を参照してください。
-   [SQL Server 2016 リリース ノート](../sql-server/sql-server-2016-release-notes.md)
-   [SQL Server 2016 の Integration Services の新機能](../integration-services/what-s-new-in-integration-services-in-sql-server-2016.md)
-   [SQL Server vNext の Integration Services の新機能](../integration-services/what-s-new-in-integration-services-in-sql-server-vnext.md)
    
**SQL Server 2016 をお試しください。**    

180 日の試用期間中、SQL Server Evaluation Edition をご利用いただけます。  
    
> [![Evaluation Center からダウンロードする](../analysis-services/media/download.png)](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016) **[Evaluation Center から SQL Server 2016 をダウンロードする](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016)**    
    
> ![Azure Virtual Machine のアイコン](../analysis-services/media/azure-virtual-machine-small.png) **[SQL Server 2016 がインストール済みの Virtual Machine をすぐにご利用いただけます](https://azure.microsoft.com/en-us/marketplace/partners/microsoft/sqlserver2016rtmenterprisewindowsserver2012r2/?wt.mc_id=sqL16_vm)**    

##  <a name="a-nameisanew-integration-services-features-in-sql-server-vnext"></a><a name="IS"></a>SQL Server vNext の新しい Integration Services 機能
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|開発者|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Scale Out|可||||||可|
|OData コンポーネントで Microsoft Dynamics AX および Microsoft Dynamics CRM をサポート <sup>1</sup>|可|可|||||可|

<sup>1</sup> この機能は、SQL Server 2016 Service Pack 1 でもサポートされています。

##  <a name="a-nameisa-integration-services"></a><a name="IS"></a> Integration Services  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|開発者|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|組み込みのデータ ソース コネクタ|可|可|可|可|可|可|可|  
|Azure データ ソース コネクタおよびタスク|可|可|可|可|可|可|可|  
|SQL Server インポートおよびエクスポート ウィザード|可|可|可|可|可|可|可|  
|Hadoop/HDFS コネクタおよびタスク|可|可|可||||可|  
|SSIS デザイナーおよびランタイム|可|可|||||可|  
|組み込みのタスクと変換|可|可|||||可|  
|基本的なデータ プロファイリング ツール|可|可|||||可|  
|Attunity の Change Data Capture Service for Oracle|可||||||可|  
|Attunity の Change Data Capture Designer for Oracle|可||||||はい| 

##  <a name="a-nameisaaa-integration-services---advanced-adapters"></a><a name="ISAA"></a> Integration Services – 拡張アダプター  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|開発者|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|高パフォーマンスの Oracle 変換先|可||||||可|  
|高パフォーマンスの Teradata 変換先|可||||||可|  
|SAP BW 変換元と変換先|可||||||可|  
|データ マイニング モデル トレーニング変換先アダプター|可||||||可|  
|ディメンション処理の変換先アダプター|可||||||可|  
|パーティション処理の変換先アダプター|可||||||可|  
|Attunity 変更データ キャプチャ コンポーネント|可||||||可|  
|Attunity ODBC (Open Database Connectivity) 接続|可||||||はい|  
  
##  <a name="a-nameisata-integration-services---advanced-transforms"></a><a name="ISAT"></a>Integration Services – 詳細な変換  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|開発者|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|永続性 (高パフォーマンス) 参照|可||||||可|  
|データ マイニング クエリ変換|可||||||可|  
|あいまいグループ化変換とあいまい参照変換|可||||||可|  
|用語抽出と用語参照変換|可||||||可|  
  