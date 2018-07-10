---
title: 親子型ディメンションの財務アカウントの作成 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], account
- account dimensions [Analysis Services]
- adding account intelligence
- account intelligence [Analysis Services]
ms.assetid: 2ba74e81-5b4b-407e-acdf-deb2f6accf0a
caps.latest.revision: 15
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 39c5c676cd0a07c76a06fd559b7f40f8cee4cfcb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37259598"
---
# <a name="create-a-finance-account-of-parent-child-type-dimension"></a>親子型ディメンションの財務アカウントの作成
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] での勘定科目ディメンションとは、財務報告用の勘定科目一覧表を表す属性を持つディメンションを指します。  
  
 勘定科目ディメンションを使用すると、勘定科目における集計動作の推移を選択的に管理できます。 また、財務データを取り扱うビジネス インテリジェンス ソリューションで一般的に発生する標準外の集計上の問題を、標準メカニズムを使用して解決できるようにもなります。 標準メカニズムがない場合、このような標準外の集計上の問題は、カスタム ロールアップ数式、計算されたメンバー、多次元式 (MDX) スクリプトなどがなければ解決できません。  
  
 勘定科目ディメンションとしてディメンションを識別するためには、設定、`Type`ディメンションのプロパティ`Accounts`します。  
  
## <a name="dimension-structure"></a>[ディメンション構造]  
 勘定科目ディメンションには、少なくとも次の 2 つの属性が含まれています。  
  
-   キー属性 - 勘定科目ディメンションのディメンション テーブルで個々の勘定科目を識別する属性です。  
  
-   勘定科目属性 - 勘定科目ディメンションにおける勘定科目の階層構造を記述した親属性です。  
  
     勘定科目属性として属性を識別するためには、設定、`Type`する属性のプロパティ`Account`と`Usage`プロパティを`Parent`します。  
  
 勘定科目ディメンションには、次の属性をオプションで含めることもできます。  
  
-   勘定科目の種類の属性 - ディメンションの各勘定科目の種類を定義する属性です。 勘定科目の種類の属性のメンバー名は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のデータベースまたはプロジェクトに対して定義された勘定科目の種類にマップされ、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によってこれらの勘定科目に対して使用される集計関数を示します。 単項演算子またはカスタム ロールアップ数式を使用しても、勘定科目属性の集計動作を指定することができますが、勘定科目の種類を使用すると、基になるリレーショナル データベースを変更しなくても一貫性のある動作を勘定科目一覧表に簡単に適用できるようになります。  
  
     勘定科目の種類の属性を指定するには、属性の `Type` プロパティを `AccountType` に設定します。  
  
-   勘定科目名属性 - レポートのために使用される属性です。 勘定科目名属性を指定するには、属性の `Type` プロパティを `AccountName` に設定します。  
  
-   勘定科目番号属性 - レポートのために使用される属性です。 設定で勘定科目番号属性を識別する、`Type`する属性のプロパティ`AccountNumber`します。  
  
 属性の種類の詳細については、「 [属性の種類の構成](attribute-properties-configure-attribute-types.md)」を参照してください。  
  
## <a name="adding-account-intelligence-with-the-business-intelligence-wizard"></a>ビジネス インテリジェンス ウィザードを使用した勘定科目インテリジェンスの追加  
 勘定科目ディメンションを定義し、定義したディメンションをキューブに追加したら、ビジネス インテリジェンス ウィザードを使用して、勘定科目の種類の特定とマップなどの勘定科目インテリジェンス機能をディメンションに追加することができます。 詳細については、「 [ディメンションへの勘定科目インテリジェンスの追加](bi-wizard-add-account-intelligence-to-a-dimension.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [属性と属性階層](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [ビジネス インテリジェンス ウィザードの F1 ヘルプ](../business-intelligence-wizard-f1-help.md)   
 [ディメンションの種類](../multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md)  
  
  
