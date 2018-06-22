---
title: '[結合] ダイアログ ボックス (Visual Database Tools) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vdt.ppg.joinline
- vdtsql.chm:69638
ms.assetid: 0d9516bb-4ad3-4fcf-bb77-93474dea698f
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e6adb9f0f9ee0d265124e0c3648279516018eb92
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36084009"
---
# <a name="join-dialog-box-visual-database-tools"></a>[結合] ダイアログ ボックス (Visual Database Tools)
  このダイアログ ボックスを使用すると、テーブルを結合するオプションを指定できます。 このダイアログにアクセスするには、 **[デザイン]** ペインで結合線を選択します。 次に、 **[プロパティ]** ウィンドウの **[結合条件と種類]** をクリックして、プロパティの右側に表示される省略記号 ( **[...]** ) をクリックします。  
  
 既定では、関連するテーブルは内部結合によって結合されます。この場合、結合列に一致した情報を含んでいる行に基づいて、結果セットが作成されます。 **[結合]** ダイアログ ボックスのオプションを設定することにより、別の演算子に基づいて結合を指定したり、外部結合を指定したりできます。  
  
 テーブルの結合の詳細については、「 [結合を使用したクエリ (Visual Database Tools)](visual-database-tools.md)」を参照してください。  
  
## <a name="options"></a>および  
  
|**項目**|**定義**|  
|--------------|--------------------|  
|**Table**|結合するテーブルまたはテーブル値オブジェクトの名前です。 ここではテーブルの名前は変更できません。この情報は参照用としてのみ表示されます。|  
|**列**|テーブルの結合に使用する列の名前です。 演算子一覧の演算子によって、列のデータ間の関係を指定します。 ここでは列の名前は変更できません。この情報は参照用としてのみ表示されます。|  
|**[演算子]**|結合列を関連付けるために使用する演算子を指定します。 等号 (=) 以外の演算子を指定する場合は、一覧で選択します。 プロパティ ページを閉じると、選択した演算子が結合線の菱形記号の中に次のように表示されます。<br /><br /> ![Visual Database Tools のアイコン](../../database-engine/media//dv3wbii.gif "Visual Database Tools のアイコン")|  
|**すべての行から\<table1 >**|右側のテーブルに対応する一致がない場合でも、左側のテーブルのすべての行を出力に含めるように指定します。 右側のテーブルに一致するデータのない列は、NULL として出力されます。 このオプションを選択することは、SQL ステートメントで LEFT OUTER JOIN を指定することと同じです。|  
|**すべての行から\<table2 >**|左側のテーブルに対応する一致がない場合でも、右側のテーブルのすべての行を出力に含めるように指定します。 左側のテーブルに一致するデータのない列は、NULL として出力されます。 このオプションを選択することは、SQL ステートメントで RIGHT OUTER JOIN を指定することと同じです。|  
  
 両方のすべてを選択すると**から行\<table1 >** と**からすべての行\<table2 >** SQL ステートメントで FULL OUTER JOIN を指定することと同じです。  
  
 外部結合を作成するためにオプションを選択すると、結合線中の菱形記号が変化して、結合が LEFT OUTER、RIGHT OUTER、FULL OUTER のいずれであるかを示します。  
  
> [!NOTE]  
>  この "LEFT" や "RIGHT" という単語は、必ずしも [ダイアグラム] ペイン内のテーブルの位置に対応しません。 "LEFT" とは、SQL ステートメントでキーワード JOIN の左側に名前が記述されるテーブルを示し、"RIGHT" とは、SQL ステートメントでキーワード JOIN の右側に名前が記述されるテーブルを示しています。 **[ダイアグラム]** ペイン内でテーブルを移動しても、この意味でのテーブルの左右が入れ替わることはありません。  
  
## <a name="see-also"></a>参照  
 [クエリの結合で&#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [クエリおよびビューのデザインの操作方法に関するトピック (Visual Database Tools)](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  