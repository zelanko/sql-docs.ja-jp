---
title: "精度チャートの入力としての入れ子になったテーブルのデータを使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Mining Accuracy Chart [Analysis Services], nested tables
- Mining Accuracy Chart [Analysis Services], input tables
- nested tables
- adding nested tables
ms.assetid: 162e0686-ada3-4dd3-9151-9589926e6613
caps.latest.revision: 24
author: Minewiskan
ms.author: owend
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6ebe50e260a7de9520c75e534548d342fa3b2b68
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="using-nested-table-data-as-an-input-for-an-accuracy-chart"></a>入れ子になったテーブルのデータを精度チャートの入力として使用する方法
  外部データを使用してマイニング モデルの精度をテストする際、マイニング モデルに入れ子になったテーブルが含まれている場合は、外部データにもケース テーブルと関連する入れ子になったテーブルが格納されている必要があります。  
  
 このトピックでは、モデルのテストに使用する入れ子になったテーブルを操作する方法、モデルおよび外部データの入れ子になったテーブルとケース テーブルをマップする方法、および入れ子になったテーブルにフィルターを適用する方法について説明します。  
  
 入れ子になったテーブルを操作するときは、次のヒントに留意してください。  
  
-   **[マイニング モデルのテスト ケースを使用する]** または **[マイニング構造のテスト ケースを使用する]**というオプションを選択すると、ケース テーブルまたは入れ子になったテーブルを指定する必要がありません。 これらのオプションを使用すると、テスト データの定義がマイニング構造に格納され、精度チャートの作成時にそのテスト データが自動的に選択されます。  
  
-   データ ソースのケース テーブルと入れ子になったテーブルとの間に既にリレーションシップが存在する場合、マイニング構造の列は入力テーブル内の同じ名前の列に自動的にマップされます。  
  
-   入れ子になったテーブルはケース テーブルを指定しないと選択できません。 さらに、マイニング モデルでケース テーブルと入れ子になったテーブル構造を使用しない限り、入れ子になったテーブルを入力として指定することはできません。  
  
### <a name="use-a-nested-table-as-input-to-an-accuracy-chart"></a>入れ子になったテーブルを精度チャートの入力として使用する  
  
1.  マイニング構造をダブルクリックしてデータ マイニング デザイナーで開きます。  
  
2.  **[マイニング精度チャート]** タブを選択し、次に **[入力の選択]** タブを選択します。  
  
3.  **[精度チャートに使用するデータセットの選択]**で、 **[別のデータセットを指定する]**を選択します。  
  
4.  参照ボタン **([...])** をクリックして、現在のサーバーのデータ ソース ビューの一覧から外部データセットを選択します。  
  
5.  **[ケース テーブルの選択]**をクリックします。 **[テーブルの選択]** ダイアログ ボックスで、ケース データが含まれているテーブルをデータ ソース ビューから選択し、 **[OK]**をクリックします。  
  
6.  **[入れ子になったテーブルの選択]**をクリックします。 **[テーブルの選択]** ダイアログ ボックスで、入れ子になったデータが含まれているテーブルを選択し、 **[OK]**をクリックします。  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     入れ子になったテーブルとケース テーブル間のリレーションシップを変更する必要がある場合は、 **[結合の変更]** をクリックして **[リレーションシップの作成]** ダイアログ ボックスを開きます。  
  
## <a name="see-also"></a>参照  
 [モデルのテスト データの選択およびマップ](../../analysis-services/data-mining/choose-and-map-model-testing-data.md)   
 [モデルのテスト データへのフィルターの適用](../../analysis-services/data-mining/apply-filters-to-model-testing-data.md)  
  
  

