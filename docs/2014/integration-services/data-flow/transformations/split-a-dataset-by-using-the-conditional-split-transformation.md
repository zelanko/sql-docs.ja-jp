---
title: 条件分割変換を使用してデータセットを分割する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Conditional Split transformation
- splitting dataset
- datasets [Integration Services], splitting
ms.assetid: 23b3e84f-9296-4dc9-81c0-c7f06ae3f1ff
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ffd2dc9912d30c21d8d258ed09a4e42460a82937
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85430109"
---
# <a name="split-a-dataset-by-using-the-conditional-split-transformation"></a>条件分割変換を使用してデータセットを分割する
  条件分割変換を追加して構成するには、パッケージに 1 つ以上のデータ フロー タスクと 1 つの変換元があらかじめ含まれている必要があります。  
  
### <a name="to-conditionally-split-a-dataset"></a>データセットを条件に応じて分割するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] プロジェクトを開きます。  
  
2.  ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。  
  
3.  **[データ フロー]** タブをクリックし、 **[ツールボックス]** で、条件分割変換をデザイン画面にドラッグします。  
  
4.  条件分割変換をデータ フローに連結します。連結するには、データ ソースまたは前の変換から条件分割変換にコネクタをドラッグします。  
  
5.  条件分割変換をダブルクリックします。  
  
6.  **[条件分割変換エディター]** で、変数、列、関数、および演算子を、グリッドの **[条件]** 列にドラッグし、条件として使用する式を構築します。 **[条件]** 列には、式を直接入力することもできます。  
  
    > [!NOTE]  
    >  1 つの変数または列を、複数の式で使用できます。  
  
    > [!NOTE]  
    >  式が有効でない場合、式のテキストは強調表示され、列のツールヒントにエラーの説明が表示されます。  
  
7.  必要に応じ、 **[出力名]** 列の値を変更します。 既定の名前は、Case 1、Case 2 などとなります。  
  
8.  条件が評価される順序を変更するには、上矢印または下矢印をクリックします。  
  
    > [!NOTE]  
    >  該当する可能性が最も高い条件を、一覧の先頭に配置します。  
  
9. 必要に応じて、どの条件にも一致しないデータ行の、既定の出力名を変更します。  
  
10. エラー出力を構成するには、 **[エラー出力の構成]** をクリックします。 詳細については、「 [データ フロー コンポーネントでエラー出力を構成する](../../configure-an-error-output-in-a-data-flow-component.md)」を参照してください。  
  
11. **[OK]** をクリックします。  
  
12. 更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [Conditional Split Transformation](conditional-split-transformation.md)   
 [Integration Services の変換](integration-services-transformations.md)   
 [Integration Services のパス](../integration-services-paths.md)   
 [Integration Services のデータ型](../integration-services-data-types.md)   
 [データ フロー タスク](../../control-flow/data-flow-task.md)   
 [Integration Services &#40;SSIS&#41; 式](../../expressions/integration-services-ssis-expressions.md)  
  
  
