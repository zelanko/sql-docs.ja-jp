---
title: ダイアグラムのテーブル間のリレーションシップの作成 (Visual Database Tools) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- diagrams [SQL Server], designing
ms.assetid: 28e9630c-dff4-46cc-bb0e-fe77998b6ac2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ab36ebfefbfd3d8cee8e6da7caadf86eb4a10032
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63184278"
---
# <a name="create-relationships-between-tables-on-a-diagram-visual-database-tools"></a>ダイアグラムでテーブル間のリレーションシップを作成する方法 (Visual Database Tools)
  ダイアグラム デザイナーでは、テーブル間で列をドラッグすることにより、異なるテーブルの列の間にリレーションシップを作成できます。  
  
### <a name="to-create-a-relationship-graphically"></a>リレーションシップをグラフィカルに作成するには  
  
1.  データベース デザイナーで、別のテーブル内の列に関連付ける 1 つ以上のデータベース列の行セレクターをクリックします。  
  
2.  選択した列を関連テーブルにドラッグします。  
  
3.  
  **[外部キーのリレーションシップ]** ダイアログ ボックスと **[テーブルと列]** ダイアログ ボックスが表示されます。後者のダイアログ ボックスが手前に表示されます。  
  
4.  **リレーションシップ名**には FK_*localtable*_*foreigntable*という形式のシステム指定名があります。 この値は変更できます。  
  
5.  
  **[主キー テーブル]** に適切なテーブルが指定されていることを確認します。  
  
6.  グリッドには、ローカル列とそれに対応する外部列が表示されます。 テーブル列の追加や削除またはマッピングの変更が可能です。  
  
7.  **[OK]** を選択します。  
  
     
  **[外部キーのリレーションシップ]** ダイアログ ボックスが表示されます。 **選択したリレーションシップ**は、作成したリレーションシップを示します。  
  
8.  グリッド内のリレーションシップのプロパティを変更します。  
  
9. 
  **[OK]** をクリックしてリレーションシップを作成します。  
  
     データベース デザイナーでは、選択した列間のリレーションシップが表示されます。  
  
## <a name="see-also"></a>参照  
 [[テーブルと列] ダイアログボックス &#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [Unique 制約と Check 制約](../../relational-databases/tables/unique-constraints-and-check-constraints.md)   
 [データベース ダイアグラムでのテーブルの使用 (Visual Database Tools)](work-with-tables-in-database-diagram-visual-database-tools.md)  
  
  
