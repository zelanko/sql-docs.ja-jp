---
title: '[クイック ウォッチ] ダイアログ ボックス | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- vs.debug.quickwatch
helpviewer_keywords:
- QuickWatch Dialog [Transact-SQL]
ms.assetid: d6bbb373-1452-41f2-bdc5-86ae689c3dc0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9fcb20846ba21876044d50c80856600214eed354
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66063386"
---
# <a name="quickwatch-dialog-box"></a>[クイック ウォッチ] ダイアログ ボックス
  [!INCLUDE[tsql](../../includes/tsql-md.md)] コードのデバッグ時に **[クイック ウォッチ]** ダイアログ ボックスを使用すると、変数やパラメーターなど、1 つの [!INCLUDE[tsql](../../includes/tsql-md.md)] 式のデータ型や値をすばやく表示できます。 複数の式を確認するために、 **[ウォッチ]** ウィンドウに式を追加することもできます。  
  
## <a name="task-list"></a>タスク一覧  
 **[クイック ウォッチ] ダイアログ ボックスにアクセスするには**  
  
-   **[デバッグ]** メニューの **[クイック ウォッチ]** をクリックします。  
  
 **式に関する情報を表示するには**  
  
1.  **[式]** ボックスで、目的の式を入力または選択します。 次の [!INCLUDE[tsql](../../includes/tsql-md.md)] 式がサポートされています。  
  
    -   変数。  
  
    -   パラメーター。  
  
    -   名前が @@ で始まるシステム関数。  
  
    -   1 つまたは複数の変数、パラメーター、またはシステム関数に演算子を適用して作成された式 (@IntegerCounter + 1、FirstName + LastName など)。  
  
    -   単一の値を返す Transact-SQL ステートメント(SELECT CharacterCol FROM MyTable WHERE PrimaryKey = 1 など)。  
  
2.  **[再評価]** をクリックします。  
  
 **[ウォッチ] ウィンドウにクイック ウォッチの式を追加するには**  
  
-   **[ウォッチ式の追加]** をクリックします。  
  
 **クイック ウォッチの式の値を変更するには**  
  
-   式を右クリックし、 **[値の編集]** を選択します。  
  
## <a name="options"></a>および  
 **[式の一覧]**  
 現在選択されている式を表示します。 このドロップダウン リストには、選択して表示できる式のセットが含まれています。 一覧の式は、 **[呼び出し履歴]** ウィンドウで現在選択されているスタック フレームのスコープで使用できる式です。 別の式を表示するには、式を入力するか、一覧から式を選択します。 [!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーでは、変数、パラメーター、および名前が @@ で始まるシステム関数の式がサポートされます。  
  
 **[値グリッド]**  
 現在監視されている式のプロパティを表示します。  
  
 **名前**  
 監視対象の [!INCLUDE[tsql](../../includes/tsql-md.md)] 式です。  
  
 **[値]**  
 式に現在割り当てられている値を表示します。 式に現在値がない場合は、空白になります。  
  
 式の長さが **[値]** 列の幅よりも長い場合は、その式の **[値]** セルにポインターを移動するとツールヒントに完全な値が表示されます。  
  
 **[値]** セルの虫眼鏡アイコンは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガー ビジュアライザーが使用可能であることを示します。 一覧では、 **[テキスト ビジュアライザー]** 、 **[XML ビジュアライザー]** 、または **[HTML ビジュアライザー]** を指定できます。 デバッガー ビジュアライザーを開始するには、虫眼鏡アイコンをクリックします。 [!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーによりダイアログ ボックスが開き、データがそのデータ型に適した形式で表示されます。  
  
 **型**  
 式のデータ型を表示します。  
  
## <a name="see-also"></a>関連項目  
 [Transact-SQL デバッガー](transact-sql-debugger.md)   
 [Transact-SQL デバッガー情報](transact-sql-debugger-information.md)   
 [[ウォッチ] ウィンドウ](transact-sql-debugger-watch-window.md)   
 [[ローカル] ウィンドウ](transact-sql-debugger-locals-window.md)   
 [[呼び出し履歴] ウィンドウ](transact-sql-debugger-call-stack-window.md)   
 [式 &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/expressions-transact-sql)  
  
  
