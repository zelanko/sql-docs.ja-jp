---
title: "データ マイニング クエリ変換 | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.dataminingquerytrans.f1"
helpviewer_keywords: 
  - "データ マイニング クエリ変換"
  - "予測クエリ [Integration Services]"
ms.assetid: 7960133b-a3e1-48af-ba43-55ed78c38e71
caps.latest.revision: 43
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 43
---
# データ マイニング クエリ変換
  データ マイニング クエリ変換は、データ マイニング モデルに対して予測クエリを実行します。 この変換には、データ マイニング拡張機能 (DMX) クエリを作成するためのクエリ ビルダーが含まれています。 このクエリ ビルダーを使用すると、DMX 言語を使用して、既存のマイニング モデルに対して変換入力データを評価する、カスタム ステートメントを作成できます。 詳細については、「[データ マイニング拡張機能 (DMX) リファレンス](../../../dmx/data-mining-extensions-dmx-reference.md)」を参照してください。  
  
 同じデータ マイニング構造で複数のモデルが構築されている場合、1 回の変換で複数の予測クエリを実行することもできます。 詳細については、「[データ マイニング クエリ ツール](../../../analysis-services/data-mining/data-mining-query-tools.md)」を参照してください。  
  
## データ マイニング クエリ変換の構成  
 データ マイニング クエリ変換は、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 接続マネージャーを使用して [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] プロジェクト、またはマイニング構造とマイニング モデルを含む [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のインスタンスに接続します。 詳細については、「[Analysis Services 接続マネージャー](../../../integration-services/connection-manager/analysis-services-connection-manager.md)」を参照してください。  
  
 この変換は 1 つの入力と 1 つの出力をとります。 エラー出力はサポートされていません。  
  
 プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 **[データ マイニング クエリ変換エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [[データ マイニング クエリ変換エディター] ([マイニング モデル] タブ)](../Topic/Data%20Mining%20Query%20Transformation%20Editor%20\(Mining%20Model%20Tab\).md)  
  
-   [[データ マイニング クエリ変換エディター] ([マイニング モデル] タブ)](../Topic/Data%20Mining%20Query%20Transformation%20Editor%20\(Mining%20Model%20Tab\).md)  
  
 **[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。 **[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [共通プロパティ](../Topic/Common%20Properties.md)  
  
-   [変換のカスタム プロパティ](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)  
  
 プロパティの設定方法の詳細については、「[データ フロー コンポーネントのプロパティを設定する](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)」を参照してください。  
  
  