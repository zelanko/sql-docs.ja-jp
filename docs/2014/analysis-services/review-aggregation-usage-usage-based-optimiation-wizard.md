---
title: 集計の使用状況の確認 (使用法に基づく最適化ウィザード) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.storagedesignwizard.reviewaggregationusage.f1
ms.assetid: 49ce2094-c4dc-4e46-8cef-c17c5db084ca
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a58f7f8620924d4f707fe61c45ae87e19737471f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66070170"
---
# <a name="review-aggregation-usage-usage-based-optimiation-wizard"></a>[集計使用法の確認] (使用法に基づく最適化ウィザード)
  
  **[集計使用法の確認]** ページを使用すると、集計使用法の設定を構成できます。  
  
## <a name="options"></a>オプション  
 **標準**  
 属性の集計使用法の設定を Default に設定する場合に選択します。 この設定を使用すると、属性およびディメンションの型に基づいて既定のルールが適用されます。  
  
 **全角**  
 属性の集計使用法の設定を Full に設定する場合に選択します。 この設定を使用した場合、この属性または属性チェーンで下位にある関連属性をキューブの各集計に含める必要があります。 属性に多くのメンバーが含まれる場合は、集計使用法を Full に設定しないでください。 複数の属性または多くのメンバーが含まれる属性に対してこの設定を指定すると、サイズが大きくなりすぎて集計のデザインを行えない可能性があります。  
  
 **なし**  
 属性の集計使用法の設定を None に設定する場合に選択します。 この設定を使用した場合、この属性をキューブの集計に含めることはできません。  
  
 **制限しない**  
 属性の集計使用法の設定を Unrestricted に設定する場合に選択します。 この設定を使用すると、集計デザイナーに対する制限は行われません。 ただし、この設定でも、属性を評価して属性が重要な集計候補であるかどうかを判断する必要があります。  
  
 **[すべて既定値に設定]**  
 すべての属性の集計使用法の設定を Default に設定する場合に選択します。  
  
## <a name="see-also"></a>参照  
 [集計のデザインウィザードの F1 ヘルプ](aggregation-design-wizard-f1-help.md)   
 [Analysis Services のウィザード &#40;多次元データ&#41;](analysis-services-wizards-multidimensional-data.md)  
  
  
