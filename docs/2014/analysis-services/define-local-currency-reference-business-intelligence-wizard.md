---
title: 現地の通貨参照の定義 (ビジネスインテリジェンスウィザード)Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.currencyconversion.localcurrency.f1
ms.assetid: 74993b0d-dfca-476b-acba-d66c593680a5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 12a32140b2586b440fabcadc8385ab801963280a
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84528848"
---
# <a name="define-local-currency-reference-business-intelligence-wizard"></a>現地の通貨参照の定義 (ビジネス インテリジェンス ウィザード)
  **[現地の通貨参照の定義]** ページを使用すると、 **[換算の種類の選択]** ページで指定された多対多または多対一の変換を実行する通貨の換算機能のための現地通貨を定義できます。 現地通貨とは、 **[メジャーの選択]** ページで選択されたメジャーのトランザクションが保存される通貨です。  
  
> [!NOTE]  
>  ビジネス インテリジェンス ウィザードをディメンション デザイナーから起動した場合や、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]のソリューション エクスプローラーでディメンションを右クリックして起動した場合、このページは表示されません。 また、このページは、 **[換算の種類の選択]** ページで **[一対多]** を選択した場合にも表示されません。  
  
## <a name="options"></a>オプション  
 **[ファクト テーブルの識別子]**  
 選択すると、 **[メジャーの選択]** ページで選択されたメジャーを格納するファクト テーブルから参照される、通貨ディメンションの現地通貨の通貨識別子を表す属性を指定できます ( `Type` プロパティが*currency*に設定されている1つの通貨ディメンション)。  
  
 このオプションは、トランザクションでそのトランザクション自体の現地通貨を決定する場合に使用します。 たとえば、サンプルデータベースの場合、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] Internet Sales メジャーグループには、通貨ディメンションに対する標準のディメンションリレーションシップがあります。 このメジャー グループのファクト テーブルは、このディメンションのディメンション テーブル内の通貨識別子を参照する外部キー列を格納します。  
  
 **[ファクト データによって参照される通貨ディメンションと属性]**  
 通貨ディメンションのメンバーが現地通貨の通貨識別子を表す、その通貨ディメンション内の通貨属性を選択します。 通貨属性とは、 `Type` プロパティが*currency*に設定されている属性です。  
  
> [!NOTE]  
>  **[ファクト テーブルの識別子]** オプションが選択されていない場合は、このオプションを利用できません。  
  
 **[ディメンション テーブルの属性]**  
 選択すると、現地通貨の通貨識別子を格納するメジャー グループに関連したディメンションから属性を指定できます。  
  
 このオプションは、トランザクションと他のビジネス エンティティ (たとえば場所) とのリレーションシップによって、そのトランザクションの現地通貨が決定される場合に使用します。 たとえば、サンプルデータベースの場合、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 財務報告のメジャーグループには、組織ディメンションを介して、通貨ディメンションに対する参照ディメンションリレーションシップがあります。 つまり、[Financial Reporting] メジャー グループのファクト テーブルには、組織ディメンションのディメンション テーブル内のメンバーを参照する外部キー列があります。 さらに、組織ディメンションのディメンション テーブルには、通貨ディメンションのディメンション テーブル内の通貨識別子を参照する外部キー列があります。  
  
 **[通貨を参照するディメンションの属性]**  
 ディメンションのメンバーが現地通貨の通貨識別子を参照する、そのディメンション内の属性を選択します。  
  
> [!NOTE]  
>  **[ディメンション テーブルの属性]** オプションが選択されていない場合は、このオプションを利用できません。  
  
## <a name="see-also"></a>参照  
 [ビジネスインテリジェンスウィザードの F1 ヘルプ](business-intelligence-wizard-f1-help.md)   
 [キューブデザイナー &#40;Analysis Services-多次元データ&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [ディメンションデザイナー &#40;Analysis Services-多次元データ&#41;](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
