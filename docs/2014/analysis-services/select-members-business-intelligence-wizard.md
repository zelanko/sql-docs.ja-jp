---
title: メンバー (ビジネス インテリジェンス ウィザード) を選択します |。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.currencyconversion.memberconversion.f1
ms.assetid: 1a147461-d594-41e7-a41d-09d2d003e1e0
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2d15a32302aa5d7a4ee3ca087944effc017ce8c1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48105148"
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
 選択すると、キューブに含まれている勘定科目ディメンションの、勘定科目の階層のメンバーに通貨換算機能を適用します。 勘定科目の階層は、アカウント内の階層がディメンションの`Type`プロパティに設定されて*アカウント*します。  
  
 このオプションを選択すると、次の表に示すオプションがグリッドに表示されます。  
  
|オプション|説明|  
|------------|-----------------|  
|**勘定科目メンバー**|選択すると、勘定科目の階層の指定したメンバーに通貨換算機能を含めます。|  
|**メジャー**|レート メジャー グループから、 **[勘定科目メンバー]** で選択したメンバーのメジャーを変換するときに使用する、換算レートを含むメジャーを選択します。|  
  
 **勘定科目の階層の種類に基づく**  
 すべてのメンバーに通貨換算機能を適用する選択が持つ勘定科目の階層で属性`Type`プロパティが指定されたアカウントの種類に設定します。  
  
 このオプションを選択すると、次の表に示すオプションがグリッドに表示されます。  
  
|オプション|説明|  
|------------|-----------------|  
|**アカウントの種類**|選択すると、指定した種類の勘定科目に通貨換算機能を含めます。|  
|**メジャー**|レート メジャー グループから、 **[勘定科目の種類]** で選択した種類の勘定科目を使用して、属性のメンバーのメジャーを変換するときに使用する、換算レートを含むメジャーを選択します。|  
  
## <a name="see-also"></a>参照  
 [ビジネス インテリジェンス ウィザードの F1 ヘルプ](business-intelligence-wizard-f1-help.md)   
 [キューブ デザイナー &#40;Analysis Services - 多次元データ&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [ディメンション デザイナー &#40;Analysis Services - 多次元データ&#41;](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
