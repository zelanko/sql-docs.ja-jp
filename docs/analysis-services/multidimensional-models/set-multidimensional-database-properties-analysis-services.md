---
title: "多次元データベースのプロパティ設定 (Analysis Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プロパティ [Analysis Services], データベース"
ms.assetid: a8be5b3f-3148-448a-976c-7222705155d9
caps.latest.revision: 24
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 24
---
# 多次元データベースのプロパティ設定 (Analysis Services)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベース プロパティには、[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] データベース デザイナーで構成できるものが多数あります。  
  
 このデザイナーでは、次の種類のタスクを実行できます。  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースにオンライン モードで接続している場合は、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースの名前を変更できます。 プロジェクト モードで作業している場合は、プロジェクトの次の配置のためにデータベース名を変更できます。 詳細については、「[多次元データベース名の変更 (Analysis Services)](../../analysis-services/multidimensional-models/rename-a-multidimensional-database-analysis-services.md)」および「[Analysis Services プロジェクトのプロパティの構成 (SSDT)](../../analysis-services/multidimensional-models/configure-analysis-services-project-properties-ssdt.md)」を参照してください。  
  
-   ユーザーに表示するデータベースの説明を入力できます。 また、データベースの名前も表示できますが、変更はできません。 データベース名を変更するには、プロジェクトのプロパティを編集する必要があります。  
  
-   1 つまたは複数の言語によるデータベース名と説明の翻訳を提供できます。 詳細については、「[キューブの翻訳](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-translations.md)、「[ディメンションの翻訳](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimension-translations.md)」、および「[Analysis Services での翻訳のサポート](../../analysis-services/translation-support-in-analysis-services.md)」を参照してください。  
  
-   既定の勘定科目の種類のマッピングを表示し、必要に応じて変更できます。 勘定科目の種類のマッピングは、1 つまたは複数のメジャーで *ByAccount* 集計関数を使用する場合に使用します。 勘定科目の種類ごとに別名を指定し、その勘定科目の種類に関連する既存の集計関数を変更できます。 既定の集計を変更する方法の詳細については、「[準加法の動作の定義](../../analysis-services/multidimensional-models/define-semiadditive-behavior.md)」を参照してください。  
  
## データベース プロパティ  
 上記に加え、データベースのプロパティには、[プロパティ] ウィンドウで構成できるものが複数あります。  
  
|プロパティ|Description|  
|--------------|-----------------|  
|[集計プレフィックス]|データベース内のすべてのパーティションの集計名に使用される共通のプレフィックスです。 詳細については、「[AggregationPrefix 要素 (ASSL)](../../analysis-services/scripting/properties/aggregationprefix-element-assl.md)」を参照してください。|  
|[照合順序]|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトを [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスに配置すると、ここで別の値を指定しない限り、データベースには Collation サーバー プロパティの値が継承されます。|  
|DataSourceImpersonationInfo|データベース内のすべてのデータ ソース オブジェクトに対して既定の権限借用モードを指定します。 これは、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サービスで、オブジェクトの処理、サーバーの同期、および OpenQuery や SystemOpenSchema のデータ マイニング ステートメントの実行に使用するモードです。|  
|[推定サイズ]|ディスク上のデータベース ファイルの推定サイズを提供します。 データが複数の場所に格納されている場合、この推定値はデータベース フォルダーの下に格納されているデータ ファイルのみに制限されます。<br /><br /> **EstimatedSize** は、メモリの推定の基礎としても使用できます。 通常、メモリ要件は、データベースがメモリに読み込まれるときに作成される追加のデータ構造により、ディスク上のデータのサイズよりも大きくなります。<br /><br /> メモリ要件を詳しく推定するには、データベースのメモリ要件を把握する手段として、タスク マネージャーを使用してデータベースを処理する前後の Analysis Services プロセス メモリを確認し、使用されたメモリを調べることもできます。|  
|言語|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトを [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスに配置すると、ここで別の値を指定しない限り、データベースには Language サーバー プロパティの値が継承されます。|  
|MasterDataSource ID|リモート パーティションで使用します。 詳細については、「[リモート パーティション](../Topic/Remote%20Partitions.md)」を参照してください。|  
  
## 参照  
 [[データベースのプロパティ] ダイアログ ボックス (SSAS - 多次元)](../Topic/Database%20Properties%20Dialog%20Box%20\(SSAS%20-%20Multidimensional\).md)   
 [Analysis Services プロジェクトのプロパティの構成 (SSDT)](../../analysis-services/multidimensional-models/configure-analysis-services-project-properties-ssdt.md)  
  
  