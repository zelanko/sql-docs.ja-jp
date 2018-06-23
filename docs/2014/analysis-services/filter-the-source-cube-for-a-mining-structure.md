---
title: マイニング構造のソース キューブをフィルター選択 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- slice cubes [Analysis Services]
- mining structures [Analysis Services], filtering source cube
- cubes [Analysis Services], slicing
- filtering data [Analysis Services]
ms.assetid: 05dce7e1-2fe5-4500-bacf-c1a8a76e1424
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: ed1ff70d4bb0f0ebd20da468c91f2603318ec217
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36165129"
---
# <a name="filter-the-source-cube-for-a-mining-structure"></a>マイニング構造のソース キューブのフィルター選択
  多次元モデル (OLAP キューブ) 内のデータに基づいているマイニング構造を作成するときに実行できます*スライス*キューブ、マイニング構造の基になっています。 スライスを行うことにより、マイニング モデルのトレーニングに使用するデータに対するフィルターの種類として、データのサブセットを作成できます。  
  
### <a name="to-slice-a-cube"></a>キューブをスライスするには  
  
1.  データ マイニング デザイナーで[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]、select、**マイニング構造の** タブまたは**マイニング モデル** タブ。  
  
2.  **マイニング モデルの**メニューの **マイニング構造キューブ スライスの定義**です。  
  
     **キューブのスライス** ダイアログ ボックスが表示されます。  
  
3.  **ディメンション**の列、**キューブのスライス** ダイアログ ボックスで、フィルターを適用するディメンションを選択します。  
  
4.  リストを使用して、階層のレベルを選択して、**階層**列です。  
  
5.  一覧から演算子を選択、**演算子**列、フィルター条件の作成に使用します。  
  
6.  ボックスをクリックして、**フィルター**列です。  
  
     指定した階層レベルのメンバーをすべて含むダイアログ ボックスが表示されます。  
  
7.  フィルター選択する 1 つまたは複数のメンバーを選択します。  
  
8.  をクリックして**OK** [メンバー] ダイアログ ボックス。  
  
9. をクリックして**OK**で、**キューブのスライス** ダイアログ ボックス。  
  
     キューブ スライスの定義に従って、ソース キューブがフィルター選択されます。  
  
## <a name="see-also"></a>参照  
 [マイニング構造のタスクと操作方法](data-mining/mining-structure-tasks-and-how-tos.md)   
 [新規の OLAP マイニング構造の作成](data-mining/create-a-new-olap-mining-structure.md)  
  
  