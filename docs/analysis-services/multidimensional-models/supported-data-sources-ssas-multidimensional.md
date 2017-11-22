---
title: "サポートされているデータ ソース (SSAS - 多次元) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Analysis Services, data sources
- data sources [Analysis Services], about data sources
- Analysis Services, data sources
- connections [Analysis Services]
- SSAS, data sources
ms.assetid: c97e0f8d-7ddd-4941-8b51-e7832f30fbbe
caps.latest.revision: "69"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 69f1519d6b3c03294469707a7e1485955f864a2e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="supported-data-sources-ssas---multidimensional"></a>サポートされるデータ ソース (SSAS - 多次元)
  このトピックでは、多次元モデルで使用できるデータ ソースの種類について説明します。  
  
##  <a name="bkmk_supported_ds"></a> サポートされるデータ ソース  
 次の表のデータ ソースからデータを取得できます。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]をインストールする際のセットアップで、各データ ソースに対して挙げられているプロバイダーはインストールされません。 プロバイダーは、他のアプリケーションと共にコンピューターに既にインストールされている場合もあれば、プロバイダーをダウンロードしてインストールしなくてはならない場合もあります。  
  
> [!NOTE]  
>  Oracle OLE DB プロバイダーなどのサード パーティ プロバイダーを使用して、サード パーティ製データベースと接続することもできます。ただし、その場合は、プロバイダーの提供元が使用するデータベースをサポートしていることが条件となります。  
  
|||||  
|-|-|-|-|  
|ソース|バージョン|ファイルの種類|プロバイダー*|  
|Access データベース|Microsoft Access 2010、2013、2016|.accdb または .mdb|Microsoft Jet 4.0 OLE DB Provider|  
|SQL Server リレーショナル データベース*|Microsoft SQL Server 2008、2008 R2、2012、2014、2016、 [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)] 、Microsoft Analytics Platform System (APS)<br /><br /> <br /><br /> 注: [!INCLUDE[ssSDS](../../includes/sssds-md.md)] の詳細については、 [Azure.com](http://go.microsoft.com/fwlink/?LinkID=157856)を参照してください。<br /><br /> 注: Analytics Platform System (APS) は以前は SQL Server Parallel Dataware House (PDW) と呼ばれていました。 当初、Analysis Services から PDW に接続するには、特別なデータ プロバイダーが必要でした。 このプロバイダーは、SQL Server 2012 で変更されました。 SQL Server 2012 以降、PDW/APS への接続には、SQL Server Native Client が使用されます。 APS の詳細については、Web サイト「 [Microsoft Analytics Platform System](http://www.microsoft.com/en-us/server-cloud/products/analytics-platform-system/resources.aspx)」を参照してください。|(該当なし)|OLE DB Provider for SQL Server<br /><br /> SQL Server Native Client OLE DB プロバイダー<br /><br /> SQL Server Native 11.0 Client OLE DB プロバイダー<br /><br /> .NET Framework Data Provider for SQL Client|  
|Oracle リレーショナル データベース|Oracle 9i、10g、11g、12g|(該当なし)|Oracle OLE DB プロバイダー<br /><br /> .NET Framework Data Provider for Oracle Client<br /><br /> .NET Framework Data Provider for SQL Server<br /><br /> OraOLEDB<br /><br /> MSDASQL|  
|Teradata リレーショナル データベース|Teradata V2R6、V12|(該当なし)|TDOLEDB OLE DB プロバイダー<br /><br /> .Net Data Provider for Teradata|  
|Informix リレーショナル データベース|V11.10|(該当なし)|Informix OLE DB プロバイダー|  
|IBM DB2 リレーショナル データベース|8.1|(該当なし)|DB2OLEDB|  
|Sybase Adaptive Server Enterprise (ASE) リレーショナル データベース|15.0.2|(該当なし)|Sybase OLE DB プロバイダー|  
|その他のリレーショナル データベース|(該当なし)|(該当なし)|OLE DB プロバイダー|  
  
 \* ODBC データ ソースは、多次元ソリューションではサポートされていません。 Analysis Services 自体が接続を処理しますが、MSDASQL ドライバーを使用している場合でも、ソリューションの作成に使用される [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] のデザイナーは ODBC データ ソースには接続できません。 ビジネス要件に ODBC データ ソースが含まれている場合は、代わりに表形式のソリューションを作成することを検討してください。  
  
 ** 一部の機能では、オンプレミスで実行される SQL Server リレーショナル データベースが必要です。 具体的には、書き戻しと ROLAP ストレージでは、基になるデータ ソースが SQL Server リレーショナル データベースであることが必要です。  
  
## <a name="see-also"></a>参照  
 [サポートされているデータ ソース &#40;SSAS テーブル&#41;](../../analysis-services/tabular-models/data-sources-supported-ssas-tabular.md)   
 [多次元モデルのデータ ソース](../../analysis-services/multidimensional-models/data-sources-in-multidimensional-models.md)   
 [多次元モデルのデータ ソース ビュー](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)  
  
  
