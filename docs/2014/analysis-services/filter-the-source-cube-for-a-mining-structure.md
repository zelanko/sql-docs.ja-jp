---
title: マイニング構造のソースキューブのフィルター処理 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- slice cubes [Analysis Services]
- mining structures [Analysis Services], filtering source cube
- cubes [Analysis Services], slicing
- filtering data [Analysis Services]
ms.assetid: 05dce7e1-2fe5-4500-bacf-c1a8a76e1424
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 74220f2385e27484c5cc511c84be5625290a28db
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66081147"
---
# <a name="filter-the-source-cube-for-a-mining-structure"></a>マイニング構造のソース キューブのフィルター選択
  多次元モデル (OLAP キューブ) のデータに基づくマイニング構造を作成する場合は、マイニング構造の基になっているキューブを*スライス*することができます。 スライスを行うことにより、マイニング モデルのトレーニングに使用するデータに対するフィルターの種類として、データのサブセットを作成できます。  
  
### <a name="to-slice-a-cube"></a>キューブをスライスするには  
  
1.  のデータマイニングデザイナー [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で、[**マイニング構造**] タブまたは [**マイニングモデル**] タブを選択します。  
  
2.  [**マイニングモデル**] メニューの [**マイニング構造キューブスライスの定義**] をクリックします。  
  
     [**キューブのスライス**] ダイアログボックスが表示されます。  
  
3.  [**キューブのスライス**] ダイアログボックスの [**ディメンション**] 列で、フィルター処理するディメンションを選択します。  
  
4.  [**階層**] 列の一覧を使用して、階層のレベルを選択します。  
  
5.  フィルター条件の作成に使用する演算子を [**演算子**] 列の一覧から選択します。  
  
6.  [**フィルター** ] 列のボックスをクリックします。  
  
     指定した階層レベルのメンバーをすべて含むダイアログ ボックスが表示されます。  
  
7.  フィルター選択する 1 つまたは複数のメンバーを選択します。  
  
8.  [メンバー] ダイアログボックスで [ **OK** ] をクリックします。  
  
9. [**キューブのスライス**] ダイアログボックスで [ **OK]** をクリックします。  
  
     キューブ スライスの定義に従って、ソース キューブがフィルター選択されます。  
  
## <a name="see-also"></a>参照  
 [マイニング構造のタスクと操作方法](data-mining/mining-structure-tasks-and-how-tos.md)   
 [新規の OLAP マイニング構造の作成](data-mining/create-a-new-olap-mining-structure.md)  
  
  
