---
title: '[アルゴリズムパラメーター] ダイアログボックス (マイニングモデルビュー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.models.algorithmparameters.f1
helpviewer_keywords:
- Algorithm Parameters dialog box
ms.assetid: 57f9f6f8-8ca4-4a6e-8f18-85f0571b7060
author: minewiskan
ms.author: owend
ms.openlocfilehash: b942210e653bc3e0a7309a98a4e75e84c5f82168
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84528138"
---
# <a name="algorithm-parameters-dialog-box-mining-models-view"></a>[アルゴリズム パラメーター] ダイアログ ボックス ([マイニング モデル] ビュー)
  **[アルゴリズム パラメーター]** ダイアログ ボックスを使用すると、選択したモデルに固有のアルゴリズム パラメーターを調整できます。 アルゴリズム パラメーターを変更する場合、通常マイニング モデルの結果を変更します。 各パラメーターが結果にどのような影響を与えるかは、使用しているアルゴリズムおよびデータによって異なります。 詳細については、「 [マイニング モデルとマイニング構造のカスタマイズ](data-mining/customize-mining-models-and-structure.md)」をご覧ください。  
  
## <a name="options"></a>オプション  
 **パラメーター**  
 選択されたマイニング モデルに使用できるパラメーターを一覧表示します。  
  
 次の表に、使用可能な列を説明します。  
  
|Column|説明|  
|------------|-----------------|  
|**パラメーター**|パラメーターの名前の一覧を取得します。|  
|**Value**|パラメーターの既定値を変更する場合にのみ値を入力します。|  
|**[Default]**|**[値]** 列に値が指定されていない場合にアルゴリズムが使用するパラメーターの既定値を示します。|  
|**Range**|**[値]** 列に入力できる値の範囲を示します。 範囲には、次のいずれかを指定できます。<br /><br /> 個別のリスト (1、2、3など)<br /><br /> 包括範囲 ([0, 100] など)<br /><br /> (0,...) などの排他的範囲<br /><br /> [0,...) のような組み合わせ|  
  
 **説明**  
 **[パラメーター]** の一覧で選択されたパラメーターを説明します。  
  
 **[追加]**  
 このボタンをクリックして、アルゴリズム固有のその他のパラメーターを一覧に追加します。 パラメーターを追加した後で、正しい名前を **[パラメーター]** 列に入力し、 **[値]** 列に値を入力します。  
  
 **削除**  
 このボタンをクリックして、カスタム パラメーターを一覧から削除します。  
  
 標準の Analysis Services アルゴリズム パラメーターのいずれかを一覧から削除しても、パラメーターはモデルでそのまま使用されますが、そのパラメーターの既定値が使用されます。 パラメーターは完全に削除されず、次にダイアログ ボックスを開いたときに表示されます。  
  
## <a name="see-also"></a>参照  
 [データマイニングアルゴリズム &#40;Analysis Services-データマイニング&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [マイニングモデルビュー &#40;データマイニングモデルデザイナー&#41;](mining-models-view-data-mining-model-designer.md)   
 [データ マイニング オブジェクトの移動](data-mining/moving-data-mining-objects.md)  
  
  
