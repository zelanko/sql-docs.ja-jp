---
title: 計算メンバー ビルダー ダイアログ ボックス (Analysis Services - 多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.calculatedmemberbuilderdialog.f1
ms.assetid: 73b89a9f-f403-4ab8-99f7-e3ceb870c260
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c11d690ce6e240d9054da37ff9b85632b0d831ac
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48077272"
---
# <a name="calculated-member-builder-dialog-box-analysis-services---multidimensional-data"></a>[計算されるメンバー ビルダー] ダイアログ ボックス (Analysis Services - 多次元データ)
  **の** [計算されるメンバー ビルダー] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ダイアログ ボックスを使用して、計算されるメンバーを作成します。  
  
## <a name="options"></a>および  
  
|項目|定義|  
|----------|----------------|  
|**名前**|計算されるメンバーの名前を入力します。|  
|**親階層**|計算されるメンバーを作成する階層を選択します。|  
|**親メンバー**|親階層を選択した場合、このオプションが有効になっている (他にも、`Measures`ディメンション) を持つ 1 つ以上のレベル。 省略記号 (**[...]**) ボタンをクリックして親メンバーを選択します。 親メンバーによって、ディメンション構造内における計算されるメンバーの位置が決まります。|  
|**[式]**|使用する MDX 式を入力します。|  
|**[確認]**|**[式]** で定義された MDX 式をテストするには、 **[確認]** をクリックします。|  
|**メタデータ**|[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] [式] **で定義された MDX 式に含めることができる現在の**オブジェクトのメタデータを表示します。<br /><br /> 選択されたアイテムの MDX 構文をコピーするには、アイテムを右クリックし、 **[コピー]** を選択するか、選択したアイテムを **[式]** にドラッグします。|  
|**関数**|現在の [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスで使用可能な MDX 関数を表示します。 一覧表示されたアイテムは、MDSCHEMA_FUNCTIONS スキーマ行セットから取得されます。<br /><br /> 選択されたアイテムの MDX 構文をコピーするには、アイテムを右クリックし、 **[コピー]** を選択するか、選択したアイテムを **[式]** にドラッグします。|  
  
## <a name="see-also"></a>参照  
 [多次元式&#40;MDX&#41;リファレンス](/sql/mdx/multidimensional-expressions-mdx-reference)  
  
  
