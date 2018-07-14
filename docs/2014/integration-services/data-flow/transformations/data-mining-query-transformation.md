---
title: データ マイニング クエリ変換 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataminingquerytrans.f1
helpviewer_keywords:
- Data Mining Query transformation
- prediction queries [Integration Services]
ms.assetid: 7960133b-a3e1-48af-ba43-55ed78c38e71
caps.latest.revision: 42
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 295b615c859fa3524e07fa83f4142396cdf6e4c4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37192152"
---
# <a name="data-mining-query-transformation"></a>データ マイニング クエリ変換
  データ マイニング クエリ変換は、データ マイニング モデルに対して予測クエリを実行します。 この変換には、データ マイニング拡張機能 (DMX) クエリを作成するためのクエリ ビルダーが含まれています。 このクエリ ビルダーを使用すると、DMX 言語を使用して、既存のマイニング モデルに対して変換入力データを評価する、カスタム ステートメントを作成できます。 詳細については、「[データ マイニング拡張機能 (DMX) リファレンス](/sql/dmx/data-mining-extensions-dmx-reference)」を参照してください。  
  
 同じデータ マイニング構造で複数のモデルが構築されている場合、1 回の変換で複数の予測クエリを実行することもできます。 詳細については、次を参照してください。[データ マイニング クエリ インターフェイス](../../../analysis-services/data-mining/data-mining-query-tools.md)します。  
  
## <a name="configuration-of-the-data-mining-query-transformation"></a>データ マイニング クエリ変換の構成  
 データ マイニング クエリ変換は、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 接続マネージャーを使用して [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] プロジェクト、またはマイニング構造とマイニング モデルを含む [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のインスタンスに接続します。 詳しくは、「 [Analysis Services 接続マネージャー](../../connection-manager/analysis-services-connection-manager.md)」をご覧ください。  
  
 この変換は 1 つの入力と 1 つの出力をとります。 エラー出力はサポートされていません。  
  
 プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 **[データ マイニング クエリ変換エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [データ マイニング クエリ変換エディター&#40;マイニング モデル タブ&#41;](../../data-mining-query-transformation-editor-mining-model-tab.md)  
  
-   [データ マイニング クエリ変換エディター&#40;マイニング モデル タブ&#41;](../../data-mining-query-transformation-editor-mining-model-tab.md)  
  
 **[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。 **[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [共通プロパティ](../../common-properties.md)  
  
-   [変換のカスタム プロパティ](transformation-custom-properties.md)  
  
 データ フロー コンポーネントのプロパティの設定方法については、「 [データ フロー コンポーネントのプロパティを設定する](../set-the-properties-of-a-data-flow-component.md)」を参照してください。  
  
  
