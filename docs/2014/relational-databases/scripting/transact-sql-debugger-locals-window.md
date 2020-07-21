---
title: '[ローカル] ウィンドウ'
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Locals Window [Transact-SQL]
ms.assetid: 59bea640-7823-4b4d-832c-f384d83cca2f
author: rothja
ms.author: jroth
ms.openlocfilehash: 6f8f62eb69a50d7543af41dddb9c62c842d17151
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85063300"
---
# <a name="locals-window"></a>ローカル ウィンドウ
  **[ローカル]** ウィンドウには、 [!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーの現在のスコープ内にあるローカル式についての情報が表示されます。 スコープは、 **[呼び出し履歴]** ウィンドウで選択された現在の呼び出し履歴フレームに設定されます。 ローカル式を表示するには、デバッグ モードである必要があります。  
  
## <a name="task-list"></a>タスク一覧  
 **[ローカル] ウィンドウにアクセスするには**  
  
-   **[デバッグ]** メニューの **[ウィンドウ]** をポイントし、 **[ローカル]** をクリックします。  
  
 **式の値を変更するには**  
  
-   式を右クリックし、 **[値の編集]** を選択します。  
  
## <a name="columns"></a>[列]  
 **Name**  
 ローカル式の名前です。 [!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーでは、変数、パラメーター、および名前が @@ で始まるシステム関数が一覧表示されます。  
  
 **Value**  
 ローカル式に現在割り当てられている値を表示します。 式に値が割り当てられていない場合、この列は空白です。  
  
 式の長さが **[値]** 列の幅よりも長い場合は、その式の **[値]** セルにポインターを移動するとツールヒントに完全な値が表示されます。  
  
 **[値]** セルの虫眼鏡アイコンは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガー ビジュアライザーが使用可能であることを示します。 一覧では、 **[テキスト ビジュアライザー]** 、 **[XML ビジュアライザー]** 、または **[HTML ビジュアライザー]** を指定できます。 デバッガー ビジュアライザーを開始するには、虫眼鏡アイコンをクリックします。 [!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーによりダイアログ ボックスが開き、データがそのデータ型に適した形式で表示されます。  
  
 **Type**  
 式のデータ型を表示します。  
  
## <a name="see-also"></a>参照  
 [Transact-SQL デバッガー](transact-sql-debugger.md)   
 [Transact-SQL デバッガー情報](transact-sql-debugger-information.md)   
 [[ウォッチ] ウィンドウ](transact-sql-debugger-watch-window.md)   
 [[呼び出し履歴] ウィンドウ](transact-sql-debugger-call-stack-window.md)   
 [[クイック ウォッチ] ダイアログ ボックス](transact-sql-debugger-quickwatch-dialog-box.md)   
 [式 &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/expressions-transact-sql)  
