---
title: "条件分割変換エディター |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.conditionalsplittransformation.f1
helpviewer_keywords:
- Conditional Split Transformation Editor
ms.assetid: c30e1633-537a-4837-9991-6203c6f2a21e
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 769f9562af7bac75a488854319ba87ff8088329c
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="conditional-split-transformation-editor"></a>条件分割変換エディター
  **[条件分割変換エディター]** を使用すると、式の作成、式が評価される順序の設定、条件分割の出力の名前付けを行うことができます。 このダイアログ ボックスには、式の作成に使用する、数学関数、文字列関数、日付/時刻関数や演算子が含まれています。 True として評価される最初の条件は、行が送信される出力を決定します。  
  
> [!NOTE]  
>  条件分割変換は、1 つの出力に対してのみ各入力行を送信します。 複数の条件を入力した場合、変換によって、条件が True である最初の出力に各行が送信され、その行に対して後続する条件は無視されます。 複数の条件を継続して評価する必要がある場合、データ フローで複数の条件分割変換の連結が必要となることがあります。  
  
 条件分割変換の詳細については、「 [条件分割変換](../../../integration-services/data-flow/transformations/conditional-split-transformation.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **書**  
 行を選択し、右側の矢印キーを使用して、式を評価する順序を変更します。  
  
 **[出力名]**  
 出力名を指定します。 既定は数字の付いた場合の一覧ですが、一意のわかりやすい名前を選択することもできます。  
  
 **条件**  
 式を入力するか、使用可能な列、変数、関数、および演算子の一覧からドラッグして式を作成します。  
  
 このプロパティの値は、プロパティ式を使用して指定することができます。  
  
 **:**   [Integration Services &#40;SSIS&#41; の式](../../../integration-services/expressions/integration-services-ssis-expressions.md)、[ &#40;SSIS 式&#41;](../../../integration-services/expressions/operators-ssis-expression.md)、および [ &#40;SSIS 式&#41;](../../../integration-services/expressions/functions-ssis-expression.md)  
  
 **[既定の出力名]**  
 既定の出力の名前を入力するか、既定を使用します。  
  
 **[エラー出力の構成]**  
 [[エラー出力の構成]](http://msdn.microsoft.com/library/5f8da390-fab5-44f8-b268-d8fa313ce4b9) ダイアログ ボックスを使用して、エラーの処理方法を指定します。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../../integration-services/integration-services-error-and-message-reference.md)   
 [条件分割変換を使用してデータセットを分割します。](../../../integration-services/data-flow/transformations/split-a-dataset-by-using-the-conditional-split-transformation.md)  
  
  
