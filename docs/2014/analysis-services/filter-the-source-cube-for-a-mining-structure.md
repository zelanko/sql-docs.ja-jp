---
title: マイニング構造のソース キューブをフィルター処理 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
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
ms.openlocfilehash: 5c7d3208729ec225c25d1616e7a2052245e6ed25
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62731344"
---
# <a name="filter-the-source-cube-for-a-mining-structure"></a>マイニング構造のソース キューブのフィルター選択
  多次元モデル (OLAP キューブ) のデータに基づいているマイニング構造を作成するときに*スライス*に基づくマイニング構造キューブ。 スライスを行うことにより、マイニング モデルのトレーニングに使用するデータに対するフィルターの種類として、データのサブセットを作成できます。  
  
### <a name="to-slice-a-cube"></a>キューブをスライスするには  
  
1.  データ マイニング デザイナーで[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]を選択、**マイニング構造の** タブまたは**マイニング モデル**タブ。  
  
2.  **マイニング モデルの**メニューの **マイニング構造キューブ スライスの定義**します。  
  
     **キューブのスライス** ダイアログ ボックスが表示されます。  
  
3.  **ディメンション**の列、**キューブのスライス** ダイアログ ボックスで、フィルターを適用するディメンションを選択します。  
  
4.  リストを使用して、階層のレベルを選択、**階層**列。  
  
5.  一覧から演算子を選択、**演算子**列、フィルター条件の構築に使用します。  
  
6.  ボックスをクリックして、**フィルター**列。  
  
     指定した階層レベルのメンバーをすべて含むダイアログ ボックスが表示されます。  
  
7.  フィルター選択する 1 つまたは複数のメンバーを選択します。  
  
8.  クリックして**OK**  ダイアログ ボックスでメンバー。  
  
9. クリックして**OK**で、**キューブのスライス** ダイアログ ボックス。  
  
     キューブ スライスの定義に従って、ソース キューブがフィルター選択されます。  
  
## <a name="see-also"></a>参照  
 [マイニング構造のタスクと操作方法](data-mining/mining-structure-tasks-and-how-tos.md)   
 [新規の OLAP マイニング構造の作成](data-mining/create-a-new-olap-mining-structure.md)  
  
  
