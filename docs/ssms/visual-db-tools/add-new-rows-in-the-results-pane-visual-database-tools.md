---
title: 結果ペインへの新しい行の追加
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- View Designer, Results pane
- inserting rows
- Query Designer [SQL Server], Results pane
- Results pane
- adding rows
- row additions [SQL Server], Results pane
ms.assetid: 59891c84-3f54-4ab9-8b86-72c59627b480
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.openlocfilehash: fed22c3c4922f74cb3462db4ac6617e6ee7a7c5f
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "75253430"
---
# <a name="add-new-rows-in-the-results-pane-visual-database-tools"></a>結果ペインに新しい行を追加する (Visual Database Tools)

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

新しいデータを入力するか、メモ帳や Excel などのプログラムから新しいデータを貼り付けることで、新しいデータを追加できます。 行を貼り付ける場合は、貼り付けるデータの列の数と型が貼り付け先のテーブルと一致している必要があります。 結果ペインには、一度に複数の行を貼り付けることもできます。  
  
データを入力する方法については、「[結果更新の規則 (Visual Database Tools)](../../ssms/visual-db-tools/rules-for-updating-results-visual-database-tools.md)」を参照してください。  
  
### <a name="to-add-a-new-data-row"></a>新しいデータ行を追加するには  
  
1.  結果ペインの 1 番下まで移動します。ここには、新しいデータ行の追加に使用できる空の行があります。  
  
    すべての列の初期値は、 *NULL*になります。  
  
    > [!TIP]  
    > 最初の空の行に直接移動するには、結果ペインの下部にあるナビゲーション バーを使用します。  
  
2.  クリップボードから行を貼り付ける場合は、新規の行の左側にあるボタンをクリックして新規の行を選択します。  
  
    > [!NOTE]  
    > 貼り付けた行に、データベースにコミットできないものがある場合は、コミットできなかった行を通知するメッセージが表示されます。  
  
3.  新規の行にデータを入力します。 データを貼り付ける場合は、 **[編集]** メニューの **[貼り付け]** をクリックします。  
  
4.  その行から離れると、データがデータベースにコミットされます。  
  
行を保存するときにエラーが発生した場合は、クエリおよびビュー デザイナーによりメッセージが表示され、編集していた行に戻ります。 この場合は、次のいずれかの操作を行うことができます。  
  
-   行にさらに編集を加えることにより、エラーの原因を取り除く。  
  
-   Esc キーを押すことにより、編集を取り消す。 変更したセル内で Esc キーを押すと、そのセルに加えた変更だけが取り消されます。 変更していないセル内で Esc キーを押すと、行全体に加えた変更が取り消されます。  
  
## <a name="see-also"></a>参照  
[結果ペインのデータの操作 (Visual Database Tools)](../../ssms/visual-db-tools/work-with-data-in-the-results-pane-visual-database-tools.md)  
[クエリに関する基本操作の実行 (Visual Database Tools)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  
