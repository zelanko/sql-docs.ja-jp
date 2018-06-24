---
title: マイニング モデルのコピーを作成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- mining models [Analysis Services], copying
- mining models [Analysis Services], creating
- mining models [Analysis Services], how-to topics
- copying mining models
ms.assetid: 7975bb02-f188-49a0-b7de-5b9b216254ad
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: da23bba72674c1f9ca4dd80bab01dd9d8e8e35cb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36076331"
---
# <a name="make-a-copy-of-a-mining-model"></a>マイニング モデルのコピーの作成
  マイニング モデルのコピーの作成は、同じデータに基づいて複数のマイニング モデルをすばやく作成する場合に便利です。 モデルをコピーした後で、パラメーターを変更したり、フィルターを追加したりすることで、新しいコピーを編集できます。  
  
 たとえば、購入記録のテーブルにリンクされた Customers テーブルがある場合、コピーを作成して、年齢や地域などの属性でフィルター選択した顧客の統計区分ごとに別々のマイニング モデルを生成できます。  
  
 モデルのコンテンツ (グラフィカル表示やモデル パターンなど) をクリップボードにコピーして他のプログラムで使用する方法については、「 [マイニング モデルの表示のコピー](copy-a-view-of-a-mining-model.md)」を参照してください。  
  
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
  
     フィルター エディターのダイアログ ボックスの使用方法の詳細については、「 [マイニング モデルへのフィルターの適用](apply-a-filter-to-a-mining-model.md)」を参照してください。  
  
4.  **プロパティ**ウィンドウで、`AlgorithmParameters`テキスト ボックスで、をクリックして**Setalgorithm パラメーター**、および必要な場合、アルゴリズム パラメーターを変更します。  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>参照  
 [マイニング モデル フィルターの&#40;Analysis Services - データ マイニング&#41;](mining-models-analysis-services-data-mining.md)   
 [マイニング モデル タスクと操作方法](mining-model-tasks-and-how-tos.md)   
 [マイニング モデルからのフィルターの削除](delete-a-filter-from-a-mining-model.md)  
  
  