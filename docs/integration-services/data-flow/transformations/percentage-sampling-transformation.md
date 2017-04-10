---
title: "比率サンプリング変換 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.percentagesamplingtrans.f1"
helpviewer_keywords: 
  - "マイニング モデルのテスト"
  - "サンプリング シード [Integration Services]"
  - "データ マイニング [Analysis Services], サンプル データ セット"
  - "比率サンプリング変換"
  - "サンプル データセット [Integration Services]"
  - "データセット [Integration Services], サンプル"
  - "マイニング モデルのトレーニング"
ms.assetid: 59767e52-f732-4b3f-8602-be50d0a64ef2
caps.latest.revision: 46
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 46
---
# 比率サンプリング変換
  比率サンプリング変換は、変換入力行の比率を選択することにより、サンプル データセットを作成します。 サンプル データセットとは、変換入力からランダムに行を選択し、その結果、入力のサンプルとなるデータセットのことです。  
  
> [!NOTE]  
>  比率サンプリング変換は、指定した比率に加え、サンプル出力に行を含めるかどうかを決定するアルゴリズムを使用します。 したがって、サンプル出力の行数は、指定した比率を正確に反映しない場合があります。 たとえば、25,000 行の入力データセットに対して 10% を指定した場合、2,500 行のサンプルが生成されず、サンプルの行がこの数を多少前後することがあります。  
  
 比率サンプリング変換は、特にデータ マイニングに役立ちます。 この変換を使用すると、データセットをランダムに 2 つのデータセットに分割できます。たとえば、1 つをデータ マイニング モデルの学習用に、もう 1 つはそのモデルのテスト用に分割します。  
  
 また、比率サンプリング変換は、パッケージ開発用のサンプル データセットを作成するうえで役立ちます。 比率サンプリング変換をデータ フローに適用すると、データの特性を保持したまま、データセットのサイズを一様に縮小できます。 したがって、テスト パッケージは、サイズは小さいが代表的なデータセットを使用するため、実行速度は速くなります。  
  
## 比率サンプリング変換の構成  
 サンプリング シードを指定して、変換が行の選択に使用する乱数ジェネレーターの動作を変更できます。 同じサンプリング シードが使用される場合、この変換は、常に同じサンプル出力を作成します。 シードを指定しない場合、この変換はオペレーティング システムのティック数を使用して乱数を作成します。 したがって、パッケージの開発やテスト中に変換結果を確認する際は標準シードを使用するように選択し、パッケージの稼働時にはランダム シードを使用するように変更します。  
  
 この変換は、行サンプリング変換と同様です。ただし、行サンプリング変換は、指定する入力行数を選択してサンプル データセットを作成します。 詳細については、「 [Row Sampling Transformation](../../../integration-services/data-flow/transformations/row-sampling-transformation.md)」を参照してください。  
  
 比率サンプリング変換には、**SamplingValue** カスタム プロパティがあります。 このプロパティは、パッケージの読み込み時にプロパティ式で更新できます。 詳細については、「[Integration Services (SSIS) の式](../../../integration-services/expressions/integration-services-ssis-expressions.md)」、「[パッケージでプロパティ式を使用する](../../../integration-services/expressions/use-property-expressions-in-packages.md)」、および「[変換のカスタム プロパティ](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)」を参照してください。  
  
 この変換は、1 つの入力と 2 つの出力をとります。 エラー出力はサポートされていません。  
  
 プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 **[比率サンプリング変換エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、「[比率サンプリング変換エディター](../../../integration-services/data-flow/transformations/percentage-sampling-transformation-editor.md)」を参照してください。  
  
 **[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。 **[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [共通プロパティ](../Topic/Common%20Properties.md)  
  
-   [変換のカスタム プロパティ](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)  
  
 プロパティの設定方法の詳細については、「[データ フロー コンポーネントのプロパティを設定する](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)」を参照してください。  
  
  