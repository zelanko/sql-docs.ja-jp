---
title: "データ マイニング ディメンションを作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/13/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: mining structures [Analysis Services], dimensions
ms.assetid: 9f0c39e5-3516-43ab-b203-f3f6dbcff89a
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e4b9351e6ef83e1fbfea89ffd1130db2879d7559
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="create-a-data-mining-dimension"></a>データ マイニング ディメンションの作成
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]マイニング構造は OLAP キューブに基づいている場合は、マイニング モデルのコンテンツを含むディメンションを作成できます。 作成したディメンションは、ソース キューブに戻すことができます。  
  
 また、ディメンションの参照、ディメンションによるモデルの結果の調査、または MDX によるディメンションに対するクエリを行うこともできます。  
  
### <a name="to-create-a-data-mining-dimension"></a>データ マイニング ディメンションを作成するには  
  
1.  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]のデータ マイニング デザイナーで、 **[マイニング構造]** タブまたは **[マイニング モデル]** タブをクリックします。  
  
2.  **[マイニング モデル]** メニューの **[データ マイニング ディメンションの作成]**をクリックします。  
  
     **[データ マイニング ディメンションの作成]** ダイアログ ボックスが開きます。  
  
3.  **[データ マイニング ディメンションの作成]** ダイアログ ボックスの **[モデル名]** 一覧で、OLAP マイニング モデルを選択します。  
  
4.  **[ディメンション名]** ボックスに、新しいデータ マイニング ディメンションの名前を入力します。  
  
5.  新しいデータ マイニング ディメンションが含まれているキューブを作成するには、 **[キューブを作成する]**を選択します。 **[キューブを作成する]**を選択すると、キューブの新しい名前を入力できるようになります。  
  
6.  **[OK]**をクリックします。  
  
     データ マイニング ディメンションが作成され、ソリューション エクスプローラーの **[ディメンション]** フォルダーに追加されます。 **[キューブを作成する]**を選択した場合は、新しいキューブも作成され、 **[キューブ]** フォルダーに追加されます。  
  
## <a name="see-also"></a>参照  
 [マイニング構造のタスクと操作方法](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)  
  
  
