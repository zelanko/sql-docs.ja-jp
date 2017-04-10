---
title: "通貨ディメンションの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ディメンション [Analysis Services], 通貨"
  - "通貨 [Analysis Services]"
  - "通貨の変換"
  - "通貨ディメンション [Analysis Services]"
ms.assetid: b1f037d1-ce47-4e47-a1c2-5ec9e781cff6
caps.latest.revision: 16
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# 通貨ディメンションの作成
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、通貨ディメンションとは、通貨を財務報告用に一覧にした属性を持つディメンションを指します。  
  
 通貨ディメンションによって、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のキューブに通貨換算機能を追加できます。 キューブに通貨換算を追加するには、ビジネス インテリジェンス ウィザードを使用して、クライアント アプリケーションのロケールに対応する値に通貨メジャーを変換する多次元式 (MDX) スクリプト コマンドを定義します。 この MDX スクリプトを作成するには、ビジネス インテリジェンス ウィザードで次の情報を指定する必要があります。  
  
-   現地通貨を表す通貨ディメンション  (このディメンションが換算元通貨ディメンションになります)。  
  
-   使用する換算レートを表すメジャー グループ。  
  
 ビジネス インテリジェンス ウィザードは、これらの情報に基づいて、適切な換算先通貨ディメンション (換算先の通貨を表す通貨ディメンション) を指定する通貨換算プロセスをデザインします。 ビジネス インテリジェンス ウィザードでは、使用するビジネス インテリジェンス ソリューションに必要な通貨換算の数に応じて、複数の換算先通貨ディメンションを定義できます。 通貨換算の定義の詳細については、「[通貨換算 &#40;Analysis Services&#41;](../../analysis-services/currency-conversions-analysis-services.md)」を参照してください。  
  
 ディメンションを通貨ディメンションとして指定するには、ディメンションの **Type** プロパティを **Currency** に設定します。  
  
## [ディメンション構造]  
 通貨ディメンションには、少なくとも、その通貨ディメンションのディメンション テーブル内で個々の通貨を識別するキー属性が含まれています。 キー属性の値は、換算元通貨ディメンションと換算先通貨ディメンションで異なります。  
  
-   属性を換算元通貨ディメンションのキー属性として指定するには、属性の **Type** プロパティを **CurrencySource** に設定します。  
  
-   属性を換算先通貨ディメンションとして指定するには、属性の **Type** プロパティを **CurrencyDestination** に設定します。  
  
 必要に応じて次の属性を換算元通貨ディメンションと換算先通貨ディメンションに含めると、レポート作成に使用できます。  
  
-   通貨名を表す属性  
  
     属性を通貨名属性として指定するには、属性の **Type** プロパティを **CurrencyName** に設定します。  
  
-   換算元通貨を表す属性  
  
     属性を換算元通貨の属性として指定するには、属性の **Type** プロパティを **CurrencySource** に設定します。  
  
-   国際標準化機構 (ISO) 通貨コード  
  
     属性を ISO 通貨コード属性として指定するには、属性の **Type** プロパティを **CurrencyIsoCode** に設定します。  
  
 属性の種類の詳細については、「[属性の種類の構成](../../analysis-services/multidimensional-models/configure-attribute-types.md)」を参照してください。  
  
## ビジネス インテリジェンス ウィザードを使用した勘定科目インテリジェンスの定義  
 勘定科目ディメンションを定義し、定義したディメンションをキューブに追加したら、ビジネス インテリジェンス ウィザードを使用して、勘定科目の種類の特定とマップなどの勘定科目インテリジェンス機能をディメンションに追加することができます。 詳細については、「[ディメンションへの勘定科目インテリジェンスの追加](../../analysis-services/multidimensional-models/add-account-intelligence-to-a-dimension.md)」を参照してください。  
  
## 参照  
 [属性と属性階層](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [ビジネス インテリジェンス ウィザードの F1 ヘルプ](../Topic/Business%20Intelligence%20Wizard%20F1%20Help.md)   
 [ディメンションの種類](../Topic/Dimension%20Types.md)  
  
  