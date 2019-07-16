---
title: データ マイニング ディメンションの作成 |Microsoft Docs
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2455ccc283af429cb314aa2e5182f8b2ee58c18e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68184104"
---
# <a name="create-a-data-mining-dimension"></a>データ マイニング ディメンションの作成
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  マイニング構造が OLAP キューブに基づいている場合は、マイニング モデルのコンテンツが含まれているディメンションを作成できます。 作成したディメンションは、ソース キューブに戻すことができます。  
  
 また、ディメンションの参照、ディメンションによるモデルの結果の調査、または MDX によるディメンションに対するクエリを行うこともできます。  
  
### <a name="to-create-a-data-mining-dimension"></a>データ マイニング ディメンションを作成するには  
  
1.  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]のデータ マイニング デザイナーで、 **[マイニング構造]** タブまたは **[マイニング モデル]** タブをクリックします。  
  
2.  **[マイニング モデル]** メニューの **[データ マイニング ディメンションの作成]** をクリックします。  
  
     **[データ マイニング ディメンションの作成]** ダイアログ ボックスが開きます。  
  
3.  **[データ マイニング ディメンションの作成]** ダイアログ ボックスの **[モデル名]** 一覧で、OLAP マイニング モデルを選択します。  
  
4.  **[ディメンション名]** ボックスに、新しいデータ マイニング ディメンションの名前を入力します。  
  
5.  新しいデータ マイニング ディメンションが含まれているキューブを作成するには、 **[キューブを作成する]** を選択します。 **[キューブを作成する]** を選択すると、キューブの新しい名前を入力できるようになります。  
  
6.  **[OK]** をクリックします。  
  
     データ マイニング ディメンションが作成され、ソリューション エクスプローラーの **[ディメンション]** フォルダーに追加されます。 **[キューブを作成する]** を選択した場合は、新しいキューブも作成され、 **[キューブ]** フォルダーに追加されます。  
  
## <a name="see-also"></a>関連項目  
 [マイニング構造のタスクと操作方法](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)  
  
  
