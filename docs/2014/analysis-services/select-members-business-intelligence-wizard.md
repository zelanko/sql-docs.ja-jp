---
title: メンバー (ビジネス インテリジェンス ウィザード) の選択 |Microsoft ドキュメント
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
- sql12.asvs.biwizard.currencyconversion.memberconversion.f1
ms.assetid: 1a147461-d594-41e7-a41d-09d2d003e1e0
caps.latest.revision: 25
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 75cd6c2aeca77d55b4ec66baa3dccb4c77f4a66e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36165916"
---
# <a name="select-members-business-intelligence-wizard"></a>[メンバーの選択] (ビジネス インテリジェンス ウィザード)
  **[メンバーの選択]** ページを使用すると、ビジネス インテリジェンス ウィザードの **[通貨換算オプションの設定]** ページで指定された通貨換算機能を適用するメンバーを指定できます。  
  
> [!NOTE]  
>  ビジネス インテリジェンス ウィザードをディメンション デザイナーから起動した場合や、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]のソリューション エクスプローラーでディメンションを右クリックして起動した場合、このページは表示されません。  
  
## <a name="options"></a>および  
 **メジャー ディメンション**  
 選択すると、キューブ内の 1 つ以上のメジャーに通貨換算機能を適用します。  
  
 このオプションを選択すると、次の表に示すオプションがグリッドに表示されます。  
  
|オプション|説明|  
|------------|-----------------|  
|**ビルトイン メジャーの種類**|選択すると、指定したメジャーに通貨換算機能を含めます。|  
|**メジャー**|レート メジャー グループから、 **[ビルトイン メジャーの種類]** で選択したメジャーを変換するときに使用する、換算レートを含むメジャーを選択します。|  
  
 **勘定科目の階層**  
 選択すると、キューブに含まれている勘定科目ディメンションの、勘定科目の階層のメンバーに通貨換算機能を適用します。 勘定科目の階層は、アカウント内の階層がディメンションの`Type`プロパティに設定されている*アカウント*です。  
  
 このオプションを選択すると、次の表に示すオプションがグリッドに表示されます。  
  
|オプション|説明|  
|------------|-----------------|  
|**勘定科目メンバー**|選択すると、勘定科目の階層の指定したメンバーに通貨換算機能を含めます。|  
|**メジャー**|レート メジャー グループから、 **[勘定科目メンバー]** で選択したメンバーのメジャーを変換するときに使用する、換算レートを含むメジャーを選択します。|  
  
 **型に基づいた勘定科目の階層**  
 勘定科目の階層で属性を選択するすべてのメンバーに通貨換算機能を適用`Type`プロパティが指定されたアカウントの種類に設定します。  
  
 このオプションを選択すると、次の表に示すオプションがグリッドに表示されます。  
  
|オプション|説明|  
|------------|-----------------|  
|**勘定科目の種類**|選択すると、指定した種類の勘定科目に通貨換算機能を含めます。|  
|**メジャー**|レート メジャー グループから、 **[勘定科目の種類]** で選択した種類の勘定科目を使用して、属性のメンバーのメジャーを変換するときに使用する、換算レートを含むメジャーを選択します。|  
  
## <a name="see-also"></a>参照  
 [ビジネス インテリジェンス ウィザードの F1 ヘルプ](business-intelligence-wizard-f1-help.md)   
 [キューブ デザイナー &#40;Analysis Services - 多次元データ&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [ディメンション デザイナー &#40;Analysis Services - 多次元データ&#41;](dimension-designer-analysis-services-multidimensional-data.md)  
  
  