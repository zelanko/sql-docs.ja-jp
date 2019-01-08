---
title: '[ウォッチ] ウィンドウ | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Watch Window [Transact-SQL]
ms.assetid: 23f3baa4-14c2-4262-92f7-3f43fcfa0436
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 01caaf26257c06aae8cb7668693fd3ff6b8b5135
ms.sourcegitcommit: 40c3b86793d91531a919f598dd312f7e572171ec
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/13/2018
ms.locfileid: "53328752"
---
# <a name="watch-window"></a>[ウォッチ] ウィンドウ
  **[ウォッチ]** ウィンドウには、選択した式に関する情報が表示されます。 ウォッチ ウィンドウを最大 4 つがあります。**ウォッチ 1**、**ウォッチ 2、3 を見る**、および**4 を見る**します。 式は、 **[呼び出し履歴]** ウィンドウで選択された現在の呼び出し履歴フレームのスコープ内で評価されます。 変数と式を確認するには、デバッグ モードである必要があります。  
  
## <a name="task-list"></a>タスク一覧  
 **[ウォッチ] ウィンドウにアクセスするには**  
  
-   **[デバッグ]** メニューの **[ウィンドウ]** をクリックし、 **[ウォッチ]** をクリックします。次に、 **[ウォッチ 1]**、 **[ウォッチ 2]、[ウォッチ 3]**、 **[ウォッチ 4]** のいずれかをクリックします。  
  
 **式の値を変更するには**  
  
-   式を右クリックし、 **[値の編集]** を選択します。  
  
## <a name="columns"></a>[列]  
 **名前**  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーによって一覧表示される式です。 次の式がサポートされています。  
  
-   変数。  
  
-   パラメーター。  
  
-   名前が @@ で始まるシステム関数。  
  
-   1 つまたは複数の変数、パラメーター、またはシステム関数に演算子を適用して作成された式 (@IntegerCounter + 1、FirstName + LastName など)。  
  
-   など、単一の値を返す TRANSACT-SQL ステートメント:SELECT CharacterCol FROM MyTable 場所 PrimaryKey = 1。  
  
 **[値]**  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] [名前] **で指定した式が**デバッガーによって評価された後に返される値が表示されます。  
  
 式の長さが **[値]** 列の幅よりも長い場合は、その式の **[値]** セルにポインターを移動するとツールヒントに完全な値が表示されます。  
  
 **[値]** セルの虫眼鏡アイコンは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガー ビジュアライザーが使用可能であることを示します。 一覧では、 **[テキスト ビジュアライザー]**、 **[XML ビジュアライザー]**、または **[HTML ビジュアライザー]** を指定できます。 デバッガー ビジュアライザーを開始するには、虫眼鏡アイコンをクリックします。 [!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーによりダイアログ ボックスが開き、データがそのデータ型に適した形式で表示されます。  
  
 **型**  
 式のデータ型を表示します。  
  
## <a name="see-also"></a>参照  
 [Transact-SQL デバッガー](transact-sql-debugger.md)   
 [Transact-SQL デバッガー情報](transact-sql-debugger-information.md)   
 [[ローカル] ウィンドウ](transact-sql-debugger-locals-window.md)   
 [[呼び出し履歴] ウィンドウ](transact-sql-debugger-call-stack-window.md)   
 [[クイック ウォッチ] ダイアログ ボックス](transact-sql-debugger-quickwatch-dialog-box.md)   
 [式 &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/expressions-transact-sql)  
