---
title: "パーティション処理変換先 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.partitionprocessingdest.f1
helpviewer_keywords:
- partitions [Analysis Services], processing
- Partition Processing destination [Integration Services]
- destinations [Integration Services], Partition Processing
ms.assetid: 36c592ff-3f78-4a58-b496-31c1c8eee131
caps.latest.revision: 44
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 036b792f9895c6b5d56438ce52455aeb5622e0ba
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="partition-processing-destination"></a>パーティション処理変換先
  パーティション処理変換先は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のパーティションを読み込んで処理します。 パーティションの詳細については、「[パーティション (Analysis Services - 多次元データ)](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)」を参照してください。  
  
 パーティション処理変換先には、次の機能が含まれます。  
  
-   増分処理、完全処理、または更新処理を実行するオプション。  
  
-   エラー構成。処理中のエラーを無視するか、またはエラーが指定した回数に達した場合、処理を停止するかを指定します。  
  
-   パーティション分割列への入力列のマッピング。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトの処理に関する詳細については、「[処理オプションと設定 (Analysis Services)](../../analysis-services/multidimensional-models/processing-options-and-settings-analysis-services.md)」を参照してください。  
  
> [!NOTE]  
>  ここで説明されているタスクは、Analysis Services テーブル モデルには適用されません。  テーブル モデルで入力列をパーティション列にマップすることはできません。 代わりに Analysis Services DDL 実行タスク [Analysis Services Execute DDL Task](../../integration-services/control-flow/analysis-services-execute-ddl-task.md) を使用してパーティションを処理することができます。  
  
## <a name="configuration-of-the-partition-processing-destination"></a>パーティション処理変換先の構成  
 パーティション処理変換先は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 接続マネージャーを接続して、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクト、または変換先が処理するキューブとパーティションを含む [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスに接続します。 詳細については、「 [Analysis Services 接続マネージャー](../../integration-services/connection-manager/analysis-services-connection-manager.md)」を参照してください。  
  
 この変換先は 1 つの入力をとります。 エラー出力はサポートされていません。  
  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 **[パーティション処理変換先エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [パーティション処理変換先エディター ([接続マネージャー] ページ)](../../integration-services/data-flow/partition-processing-destination-editor-connection-manager-page.md)  
  
-   [パーティション処理変換先エディター ([マッピング] ページ)](../../integration-services/data-flow/partition-processing-destination-editor-mappings-page.md)  
  
-   [パーティション処理変換先エディター ([詳細設定] ページ)](../../integration-services/data-flow/partition-processing-destination-editor-advanced-page.md)  
  
 **[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。 **[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [共通プロパティ](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [パーティション処理変換先のカスタム プロパティ](../../integration-services/data-flow/partition-processing-destination-custom-properties.md)  
  
 データ フロー コンポーネントのプロパティの設定方法については、「 [データ フロー コンポーネントのプロパティを設定する](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)」を参照してください。  
  
  
