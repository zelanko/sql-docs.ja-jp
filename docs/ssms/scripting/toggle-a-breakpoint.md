---
title: ブレークポイントの切り替え | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: c477ab89-a1cd-4f2c-aa7c-40525041100f
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 20a7c05dff339e56be8faef3cdd9503d993fc590
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "65821843"
---
# <a name="toggle-a-breakpoint"></a>ブレークポイントの切り替え
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメント上でブレークポイントを設定することを、ブレークポイントの切り替えと呼びます。  
  
## <a name="breakpoints"></a>ブレークポイント  
 ブレークポイントが設定されると、ステートメントの左側の灰色のバーにアイコンとして表示されます。 このアイコンはブレークポイント グリフと呼ばれます。 [!INCLUDE[tsql](../../includes/tsql-md.md)] ブレークポイントは、完全な [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントに適用されます。 ブレークポイントが切り替えられると、デバッガーは、関連付けられている [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを強調表示します。  
  
 1 行に複数の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントがある場合、ステートメントごとにブレークポイントを切り替えることができます。 ウィンドウの左側にある灰色のバーをクリックすると、行の最初のステートメントのブレークポイントが切り替わります。 ステートメントの任意の箇所を強調表示するか、ステートメント内にカーソルを移動してから、F9 キーを押すか、 **[デバッグ]** メニューの **[ブレークポイントの設定/解除]** をクリックすることにより、後続のステートメント内でブレークポイントを切り替えることができます。 1 行に複数のブレークポイントがある場合、左側の灰色のバーにブレークポイント グリフが 1 つだけ表示されます。  
  
 ブレークポイントを切り替えた後に、ブレークポイントでプロパティの編集や一時的な無効化などさまざまな操作を実行できます。 詳細については、「 [Transact-SQL ブレークポイント](../../relational-databases/scripting/transact-sql-breakpoints.md)」を参照してください。  
  
## <a name="toggle-a-breakpoint"></a>ブレークポイントの切り替え  
 **Transact-SQL ステートメントでブレークポイントを切り替えるには**  
  
1.  [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントの左側にある灰色のバーをクリックします。  
  
2.  または、ステートメントの任意の箇所を強調表示するか、ステートメント内にカーソルを移動してから、次のいずれかを実行します。  
  
    -   F9 キーを押します。  
  
    -   **[デバッグ]** メニューの **[ブレークポイントの設定/解除]** をクリックする。  
  
  
