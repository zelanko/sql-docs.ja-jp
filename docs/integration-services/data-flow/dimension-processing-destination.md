---
title: "ディメンション処理変換先 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.dimensionprocessingdest.f1"
helpviewer_keywords: 
  - "ディメンション処理変換先"
  - "ディメンションの読み込み"
  - "変換先 [Integration Services], ディメンション処理"
  - "ディメンション [Analysis Services], 処理"
ms.assetid: 4c49bb95-7259-42f4-a785-bb6aaf5f8566
caps.latest.revision: 40
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 40
---
# ディメンション処理変換先
  ディメンション処理変換先は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のディメンションを読み込んで処理します。 ディメンションの詳細については、「[ディメンション (Analysis Services - 多次元データ)](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)」を参照してください。  
  
 ディメンション処理変換先には、次の機能が含まれます。  
  
-   増分処理、完全処理、または更新処理を実行するオプション。  
  
-   エラー構成。ディメンション処理がエラーを無視するか、または指定した数のエラー発生後に停止するかどうかを指定します。  
  
-   ディメンション テーブルの列への入力列のマッピング  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトの処理に関する詳細については、「[処理オプションと設定 (Analysis Services)](../../analysis-services/multidimensional-models/processing-options-and-settings-analysis-services.md)」を参照してください。  
  
## ディメンション処理変換先の構成  
 ディメンション処理変換先は、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 接続マネージャーを接続して、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクト、または、変換先が処理するディメンションを含む [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスに接続します。 詳細については、「[Analysis Services 接続マネージャー](../../integration-services/connection-manager/analysis-services-connection-manager.md)」を参照してください。  
  
 この変換先は 1 つの入力をとります。 エラー出力はサポートされていません。  
  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 **[ディメンション処理変換先エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [ディメンション処理変換先エディター ([接続マネージャー] ページ)](../Topic/Dimension%20Processing%20Destination%20Editor%20\(Connection%20Manager%20Page\).md)  
  
-   [ディメンション処理変換先エディター ([マッピング] ページ)](../Topic/Dimension%20Processing%20Destination%20Editor%20\(Mappings%20Page\).md)  
  
-   [ディメンション処理変換先エディター ([詳細設定] ページ)](../Topic/Dimension%20Processing%20Destination%20Editor%20\(Advanced%20Page\).md)  
  
 **[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。 **[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [共通プロパティ](../Topic/Common%20Properties.md)  
  
 データ フロー コンポーネントのプロパティの設定方法については、「[データ フロー コンポーネントのプロパティを設定する](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)」を参照してください。  
  
## 参照  
 [データ フロー](../../integration-services/data-flow/data-flow.md)   
 [Integration Services の変換](../../integration-services/data-flow/transformations/integration-services-transformations.md)  
  
  