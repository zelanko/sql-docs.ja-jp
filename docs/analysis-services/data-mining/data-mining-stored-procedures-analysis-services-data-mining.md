---
title: "データ マイニングのストアド プロシージャ (Analysis Services - データ マイニング) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "データ マイニングであるストアド プロシージャ [Analysis Services]"
ms.assetid: a751856d-33bd-4788-9593-317b2826132d
caps.latest.revision: 26
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 26
---
# データ マイニングのストアド プロシージャ (Analysis Services - データ マイニング)
  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]以降の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、任意のマネージ言語で記述できるストアド プロシージャがサポートされています。 サポートされているマネージ言語には、[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET、C#、および Managed C++ があります。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] では、**CALL** ステートメントを使用してストアド プロシージャを直接呼び出すか、データ マイニング拡張機能 (DMX) クエリの一部としてストアド プロシージャを呼び出すことができます。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ストアド プロシージャの呼び出し方法の詳細については、「[ストアド プロシージャの呼び出し](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/calling-stored-procedures.md)」を参照してください。  
  
 [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] のプログラミングの一般的な情報については、「[データ マイニングのプログラミング](../../analysis-services/data-mining-programming.md)」を参照してください。  
  
 データ マイニング オブジェクトのプログラミング方法の詳細については、MSDN ライブラリの「[SQL Server データ マイニングのプログラミング](http://go.microsoft.com/fwlink/?LinkId=93735)」を参照してください。  
  
> [!NOTE]  
>  マイニング モデルにクエリを実行する場合、特に新しいデータ マイニング ソリューションをテストする場合は、データ マイニング エンジンで内部的に使用されるシステム ストアド プロシージャを呼び出すと便利です。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用して [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバーでトレースを作成した後、データ マイニング モデルを作成、参照、およびクエリすることで、これらのシステム ストアド プロシージャの名前を表示できます。 ただし、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] では、異なるバージョン間でのシステム ストアド プロシージャの互換性を保証していないため、実稼働システムではシステム ストアド プロシージャを呼び出さないでください。 代わりに、互換性を維持するために、DMX または XML/A を使用して独自のクエリを作成してください。  
  
## このセクションの内容  
  
-   [SystemGetCrossValidationResults &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/systemgetcrossvalidationresults-analysis-services-data-mining.md)  
  
-   [SystemGetClusterCrossValidationResults &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/systemgetclustercrossvalidationresults-analysis-services-data-mining.md)  
  
-   [SystemGetAccuracyResults &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/systemgetaccuracyresults-analysis-services-data-mining.md)  
  
-   [SystemGetClusterAccuracyResults &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/systemgetclusteraccuracyresults-analysis-services-data-mining.md)  
  
## リファレンス  
 [Analysis Services の管理タスクのスクリプト作成](../../analysis-services/instances/script-administrative-tasks-in-analysis-services.md)  
  
## 参照  
 [相互検証 &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/cross-validation-analysis-services-data-mining.md)   
 [[相互検証] タブ &#40;[マイニング精度チャート] ビュー&#41;](../Topic/Cross-Validation%20Tab%20\(Mining%20Accuracy%20Chart%20View\).md)   
 [ストアド プロシージャの呼び出し](../../relational-databases/native-client-odbc-stored-procedures/calling-a-stored-procedure.md)  
  
  