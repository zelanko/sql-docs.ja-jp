---
title: マイニング モデルのコピーを作成 |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 23770ec59e31a51b7aca7badf5b827baa6181155
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="make-a-copy-of-a-mining-model"></a>マイニング モデルのコピーの作成
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  マイニング モデルのコピーの作成は、同じデータに基づいて複数のマイニング モデルをすばやく作成する場合に便利です。 モデルをコピーした後で、パラメーターを変更したり、フィルターを追加したりすることで、新しいコピーを編集できます。  
  
 たとえば、購入記録のテーブルにリンクされた Customers テーブルがある場合、コピーを作成して、年齢や地域などの属性でフィルター選択した顧客の統計区分ごとに別々のマイニング モデルを生成できます。  
  
 モデルのコンテンツ (グラフィカル表示やモデル パターンなど) をクリップボードにコピーして他のプログラムで使用する方法については、「 [マイニング モデルの表示のコピー](../../analysis-services/data-mining/copy-a-view-of-a-mining-model.md)」を参照してください。  
  
### <a name="to-create-a-related-mining-model"></a>関連マイニング モデルを作成するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のソリューション エクスプローラーで、マイニング モデルを含むマイニング構造をクリックします。  
  
2.  **[マイニング モデル]** タブをクリックします。  
  
3.  モデルを選択し、右クリックしてショートカット メニューを開きます。  
  
     または  
  
     モデルを選択します。 **[マイニング モデル]** メニューの **[新しいマイニング モデル]** をクリックします。  
  
4.  新しいマイニング モデルの名前を入力し、アルゴリズムを選択します。 [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-edit-the-filter-on-the-copied-mining-model"></a>コピーされたマイニング モデルのフィルターを編集するには  
  
1.  マイニング モデルを選択します。  
  
2.  **[プロパティ]** ウィンドウで **[フィルター]** プロパティのテキスト ボックスをクリックし、作成ボタン ( **[...]** ) をクリックします。  
  
3.  フィルター条件を変更します。  
  
     フィルター エディターのダイアログ ボックスの使用方法の詳細については、「 [マイニング モデルへのフィルターの適用](../../analysis-services/data-mining/apply-a-filter-to-a-mining-model.md)」を参照してください。  
  
4.  必要に応じて、 **[プロパティ]** ウィンドウの **[AlgorithmParameters]** ボックスで **[アルゴリズム パラメーターの設定]** をクリックし、アルゴリズム パラメーターを変更します。  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>参照  
 [フィルターをマイニング モデルと #40 です。Analysis Services - データ マイニング & #41;](../../analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)   
 [マイニング モデル タスクと操作方法](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [マイニング モデルからフィルターを削除します。](../../analysis-services/data-mining/delete-a-filter-from-a-mining-model.md)  
  
  
