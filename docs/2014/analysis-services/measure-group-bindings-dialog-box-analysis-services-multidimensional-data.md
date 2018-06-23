---
title: メジャー グループのバインド ダイアログ ボックス (Analysis Services - 多次元データ) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.cubeeditor.dimensionusage.definerelationship.measuregroupbindings.f1
helpviewer_keywords:
- Measure Group Bindings dialog box
ms.assetid: ed642780-5350-438e-af73-b9ceab3f876d
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 1508624a9d0e5a9f36c8ec7c15093f56b37977ea
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36176291"
---
# <a name="measure-group-bindings-dialog-box-analysis-services---multidimensional-data"></a>[メジャー グループのバインド] ダイアログ ボックス (Analysis Services - 多次元データ)
  **[リレーションシップの定義]** ダイアログ ボックスから **[メジャー グループのバインド]** ダイアログ ボックスを使用すると、通常のディメンション リレーションシップのキューブ ディメンションの非粒度属性とメジャー グループ内の列との間で、直接リレーションシップを作成したり変更したりできます。また、キューブ ディメンションの属性に NULL 処理オプションを指定できます。  
  
## <a name="options"></a>および  
 **メジャー グループ テーブル**  
 選択したメジャー グループに対するファクト テーブルの名前を表示します。  
  
 **Attributes**  
 属性とディメンション テーブルのグリッドを表示します。 属性を選択し、 **[リレーションシップ]** でプロパティを作成、変更します。 このグリッドには次の列が含まれています。  
  
|オプション|定義|  
|------------|----------------|  
|**属性名**|属性の名前を表示します。|  
|**ディメンション テーブル**|属性が基づくディメンション テーブルの名前が表示されます。|  
  
 **リレーションシップ**  
 選択した属性に対するディメンション テーブルの列と、選択したメジャー グループに対するファクト テーブルの列との間のリレーションシップのグリッド、およびリレーションシップの NULL 処理オプションを表示します。 このグリッドには次の列が含まれています。  
  
|オプション|定義|  
|------------|----------------|  
|**[ディメンション列]**|**[属性]** で選択した属性が基づくディメンション テーブルの列を表示します。|  
|**メジャー グループ列**|**[ディメンションから継承しました]** を選択してディメンションから継承されたメジャー グループのリレーションシップを使用するか、メジャー グループが基づくファクト テーブルの列を選択してリレーションシップを明示的に定義します。|  
|**Null の処理**|属性に対する NULL 処理オプションを選択します。 NULL 処理オプションの詳細については、「[NullProcessing 要素 &#40;ASSL&#41;](scripting/properties/nullprocessing-element-assl.md)」を参照してください。|  
  
## <a name="see-also"></a>参照  
 [リレーションシップの定義 ダイアログ ボックス&#40;Analysis Services - 多次元データ&#41;](define-relationship-dialog-box-analysis-services-multidimensional-data.md)   
 [Analysis Services のデザイナーおよびダイアログ ボックス&#40;多次元データ&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  