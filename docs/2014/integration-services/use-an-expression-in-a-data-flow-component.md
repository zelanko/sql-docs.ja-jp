---
title: データフローコンポーネント | で式を使用するMicrosoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- components [Integration Services], data flow
- expressions [Integration Services], data flow components
ms.assetid: 9181b998-d24a-41fb-bb3c-14eee34f910d
author: janinezhang
ms.author: janinez
ms.openlocfilehash: d08d256946fbeb2f5b70057fc0d6992758b3a211
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84972632"
---
# <a name="use-an-expression-in-a-data-flow-component"></a>データ フロー コンポーネントで式を使用する
  この手順では、条件分割変換または派生列変換に式を追加する方法について説明します。 条件分割変換では、式を使用して、変換出力にデータ行を出力する条件を定義します。また、派生列変換では、式を使用して、列に割り当てる値を定義します。  
  
 変換に式を実装するには、あらかじめパッケージに少なくとも 1 つのデータ フロー タスクとソースが含まれている必要があります。 パッケージにアイテムを追加する方法の詳細については、次のトピックを参照してください。  
  
-   [制御フローのタスクまたはコンテナーを追加または削除する](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
    
  
-   [データ フローでコンポーネントを追加または削除する](data-flow/add-or-delete-a-component-in-a-data-flow.md)  
  
-   [データ フロー内でコンポーネントを連結する](data-flow/connect-components-in-a-data-flow.md)  
  
### <a name="to-create-an-expression"></a>式を作成するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。  
  
2.  ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。  
  
3.  [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーの **[制御フロー]** タブをクリックし、式を実装するデータ フローを含むデータ フロー タスクをクリックします。  
  
4.  **[データ フロー]** タブをクリックし、 **[ツールボックス]** からデザイン画面に条件分割変換または派生列変換のいずれかをドラッグします。  
  
5.  緑色のコネクタをソースまたは変換から条件分割変換または派生列変換にドラッグします。  
  
6.  変換をダブルクリックして、変換のダイアログ ボックスを開きます。  
  
7.  左側のペインで **[変数]** を展開し、システム変数およびユーザー定義変数を表示します。また、 **[列]** を展開して、変換の入力列を表示します。  
  
8.  右側のペインで **[数学関数]**、 **[文字列関数]**、 **[日付/時刻関数]**、 **[NULL 関数]**、 **[型キャスト]**、および **[演算子]** を展開して、式の文法で用意されている関数、キャスト、および演算子にアクセスします。  
  
9. 変換に応じて、次のいずれかの操作を実行し、式を作成します。  
  
    -   **[条件分割変換エディター]** ダイアログ ボックスで、変数、列、関数、演算子、およびキャストを **[条件]** 列にドラッグします。 ドラッグする代わりに、 **[条件]** 列に式を直接入力することもできます。  
  
    -   **[派生列変換エディター]** ダイアログ ボックスで、変数、列、関数、演算子、およびキャストを **[式]** 列にドラッグします。 ドラッグする代わりに、 **[式]** 列に式を直接入力することもできます。  
  
        > [!NOTE]  
        >  **[条件]** 列または **[式]** 列からフォーカスを外したときに、式テキストが強調表示された場合、式の文法が間違っていることを示します。  
  
10. [**OK**] をクリックして、ダイアログ ボックスを終了します。  
  
    > [!NOTE]  
    >  式が有効でない場合、式に文法エラーがあることを示す警告が表示されます。  
  
## <a name="see-also"></a>参照  
 [SSIS&#41; 式の Integration Services &#40;](expressions/integration-services-ssis-expressions.md)   
 [条件分割変換](data-flow/transformations/conditional-split-transformation.md)   
 [派生列変換](data-flow/transformations/derived-column-transformation.md)   
 [データフロータスク](control-flow/data-flow-task.md)   
 [データ フロー](data-flow/data-flow.md)  
  
  
