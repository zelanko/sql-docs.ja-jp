---
title: ブレークポイントの切り替え
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c477ab89-a1cd-4f2c-aa7c-40525041100f
author: rothja
ms.author: jroth
ms.openlocfilehash: fddaf9b23f5a67548a47ffc8cccc30baa7df5478
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85068457"
---
# <a name="toggle-a-breakpoint"></a>ブレークポイントの切り替え
  [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメント上でブレークポイントを設定することを、ブレークポイントの切り替えと呼びます。  
  
## <a name="breakpoints"></a>ブレークポイント  
 ブレークポイントが設定されると、ステートメントの左側の灰色のバーにアイコンとして表示されます。 このアイコンはブレークポイント グリフと呼ばれます。 [!INCLUDE[tsql](../../includes/tsql-md.md)] ブレークポイントは、完全な [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントに適用されます。 ブレークポイントが切り替えられると、デバッガーは、関連付けられている [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを強調表示します。  
  
 1 行に複数の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントがある場合、ステートメントごとにブレークポイントを切り替えることができます。 ウィンドウの左側にある灰色のバーをクリックすると、行の最初のステートメントのブレークポイントが切り替わります。 ステートメントの任意の箇所を強調表示するか、ステートメント内にカーソルを移動してから、F9 キーを押すか、 **[デバッグ]** メニューの **[ブレークポイントの設定/解除]** をクリックすることにより、後続のステートメント内でブレークポイントを切り替えることができます。 1 行に複数のブレークポイントがある場合、左側の灰色のバーにブレークポイント グリフが 1 つだけ表示されます。  
  
 ブレークポイントを切り替えた後に、ブレークポイントでプロパティの編集や一時的な無効化などさまざまな操作を実行できます。 詳細については、「 [Transact-SQL ブレークポイント](transact-sql-breakpoints.md)」を参照してください。  
  
## <a name="toggle-a-breakpoint"></a>ブレークポイントの切り替え  
 **Transact-SQL ステートメントでブレークポイントを切り替えるには**  
  
1.  [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントの左側にある灰色のバーをクリックします。  
  
2.  または、ステートメントの任意の箇所を強調表示するか、ステートメント内にカーソルを移動してから、次のいずれかを実行します。  
  
    -   F9 キーを押します。  
  
    -   **[デバッグ]** メニューの **[ブレークポイントの設定/解除]** をクリックする。  
  
  
