---
title: "親子型ディメンションの財務アカウントを作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dimensions [Analysis Services], account
- account dimensions [Analysis Services]
- adding account intelligence
- account intelligence [Analysis Services]
ms.assetid: 2ba74e81-5b4b-407e-acdf-deb2f6accf0a
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1f4006934f9c92e492a984b02de9e585ec8ee84b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="database-dimensions---finance-account-of-parent-child-type"></a>データベース ディメンションの親と子の型の財務アカウント
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]での勘定科目ディメンションとは、財務報告用の勘定科目一覧表を表す属性を持つディメンションを指します。  
  
 勘定科目ディメンションを使用すると、勘定科目における集計動作の推移を選択的に管理できます。 また、財務データを取り扱うビジネス インテリジェンス ソリューションで一般的に発生する標準外の集計上の問題を、標準メカニズムを使用して解決できるようにもなります。 標準メカニズムがない場合、このような標準外の集計上の問題は、カスタム ロールアップ数式、計算されたメンバー、多次元式 (MDX) スクリプトなどがなければ解決できません。  
  
 ディメンションを勘定科目ディメンションとして指定するには、ディメンションの **Type** プロパティを **Accounts**に設定します。  
  
## <a name="dimension-structure"></a>[ディメンション構造]  
 勘定科目ディメンションには、少なくとも次の 2 つの属性が含まれています。  
  
-   キー属性 - 勘定科目ディメンションのディメンション テーブルで個々の勘定科目を識別する属性です。  
  
-   勘定科目属性 - 勘定科目ディメンションにおける勘定科目の階層構造を記述した親属性です。  
  
     属性を勘定科目属性として指定するには、属性の **Type** プロパティを **Account** に設定し、 **Usage** プロパティを **Parent**に設定します。  
  
 勘定科目ディメンションには、次の属性をオプションで含めることもできます。  
  
-   勘定科目の種類の属性 - ディメンションの各勘定科目の種類を定義する属性です。 勘定科目の種類の属性のメンバー名は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のデータベースまたはプロジェクトに対して定義された勘定科目の種類にマップされ、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によってこれらの勘定科目に対して使用される集計関数を示します。 単項演算子またはカスタム ロールアップ数式を使用しても、勘定科目属性の集計動作を指定することができますが、勘定科目の種類を使用すると、基になるリレーショナル データベースを変更しなくても一貫性のある動作を勘定科目一覧表に簡単に適用できるようになります。  
  
     勘定科目の種類の属性を指定するには、属性の **Type** プロパティを **AccountType**に設定します。  
  
-   勘定科目名属性 - レポートのために使用される属性です。 勘定科目番号属性を指定するには、属性の **Type** プロパティを **AccountName**に設定します。  
  
-   勘定科目番号属性 - レポートのために使用される属性です。 勘定科目番号属性を指定するには、属性の **Type** プロパティを **AccountNumber**に設定します。  
  
 属性の種類の詳細については、「 [属性の種類の構成](../../analysis-services/multidimensional-models/attribute-properties-configure-attribute-types.md)」を参照してください。  
  
## <a name="adding-account-intelligence-with-the-business-intelligence-wizard"></a>ビジネス インテリジェンス ウィザードを使用した勘定科目インテリジェンスの追加  
 勘定科目ディメンションを定義し、定義したディメンションをキューブに追加したら、ビジネス インテリジェンス ウィザードを使用して、勘定科目の種類の特定とマップなどの勘定科目インテリジェンス機能をディメンションに追加することができます。 詳細については、「 [ディメンションへの勘定科目インテリジェンスの追加](../../analysis-services/multidimensional-models/bi-wizard-add-account-intelligence-to-a-dimension.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [属性と属性階層](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [ビジネス インテリジェンス ウィザードの F1 ヘルプ](http://msdn.microsoft.com/library/155ac80c-63ae-47aa-9e86-9396e3d920eb)   
 [ディメンションの種類](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md)  
  
  

