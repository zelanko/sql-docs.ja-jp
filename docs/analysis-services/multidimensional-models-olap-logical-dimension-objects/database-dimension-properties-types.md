---
title: "ディメンションの種類 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- time dimensions [Analysis Services]
- quantitative dimensions [Analysis Services]
- BillOfMaterials dimension [Analysis Services]
- geography dimensions
- utility dimensions [Analysis Services]
- channel dimensions
- dimensions [Analysis Services], types
- products dimensions [Analysis Services]
- account dimensions [Analysis Services]
- organization dimensions
- currency dimensions [Analysis Services]
- rates dimensions
- promotion dimensions
- scenario dimensions [Analysis Services]
- customers dimensions [Analysis Services]
- Type property
ms.assetid: bd3195da-e762-4c98-b643-34c76e842343
caps.latest.revision: "37"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: bab78f642342cd070ecde62a37d65972a17a109f
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="database-dimension-properties---types"></a>データベース ディメンションのプロパティ - 種類
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]**型**プロパティの設定は、サーバーおよびクライアント アプリケーションにディメンションの内容に関する情報を提供します。 場合によっては、**型**設定は、のみクライアント アプリケーションのガイダンスを提供し、省略可能です。 それ以外の場合になど**アカウント**または**時間**ディメンション、**型**ディメンションとその属性のプロパティ設定を特定のサーバーに基づく動作を決定します。キューブ内の特定の動作を実装する必要があります。 たとえば、**型**にディメンションのプロパティを設定できます**アカウント**標準ディメンションに勘定科目属性が含まれているクライアント アプリケーションを指定します。 時間、アカウント、および通貨ディメンションの詳細については、次を参照してください[日付型ディメンションの作成](../../analysis-services/multidimensional-models/database-dimensions-create-a-date-type-dimension.md)、[親子型ディメンションの財務アカウントを作成する](../../analysis-services/multidimensional-models/database-dimensions-finance-account-of-parent-child-type.md)、および[、通貨の作成。ディメンションの入力](../../analysis-services/multidimensional-models/database-dimensions-create-a-currency-type-dimension.md)です。  
  
 ディメンションの種類の既定の設定**正規**ディメンションのコンテンツに関する仮定は行われません。 これは、設定しない限り、最初にディメンションを定義する場合のすべてのディメンションの既定の設定**時間**ディメンション ウィザードを使用してディメンションを定義するときにします。 送信する必要がありますも**正規**ディメンション ウィザードでディメンションの種類の適切な種類が表示されない場合は、ディメンションの種類として。  
  
## <a name="available-dimension-types"></a>使用可能なディメンションの種類  
 次の表に、ディメンションの種類で使用できる[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]です。  
  
|[ディメンションの種類]|Description|  
|--------------------|-----------------|  
|Regular|特定のディメンションの種類に設定されていない種類のディメンションです。|  
|[時刻]|属性が年、半期、四半期、月、日などの時間間隔を表すディメンションです。|  
|Organization|属性が従業員や子会社などの組織情報を表すディメンションです。|  
|Geography|属性が市区町村や郵便番号などの地理情報を表すディメンションです。|  
|BillOfMaterials|属性が製品の部品表などの在庫情報や製造情報を表すディメンションです。|  
|Accounts|財務報告用の勘定科目一覧表を表す属性を持つディメンションです。|  
|Customers|属性が顧客情報や連絡先情報を表すディメンションです。|  
|Products|属性が製品情報を表すディメンションです。|  
|Scenario|属性が計画的または戦略的な分析情報を表すディメンションです。|  
|Quantitative|属性が量的な情報を表すディメンションです。|  
|Utility|属性がその他の情報を表すディメンションです。|  
|Currency|この種類のディメンションには、通貨のデータとメタデータが含まれています。|  
|Rates|属性が通貨レート情報を表すディメンションです。|  
|Channel|属性がチャネル情報を表すディメンションです。|  
|Promotion|属性がマーケティング関連のプロモーション情報を表すディメンションです。|  
  
## <a name="see-also"></a>参照  
 [既存のテーブルを使用して、ディメンションを作成します。](../../analysis-services/multidimensional-models/create-a-dimension-by-using-an-existing-table.md)   
 [ディメンション &#40;Analysis Services - 多次元データ&#41;](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)  
  
  
