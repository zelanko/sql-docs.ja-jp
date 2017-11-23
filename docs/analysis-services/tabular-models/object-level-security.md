---
title: "表形式モデル オブジェクト レベルのセキュリティ |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/20/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: 
ms.assetid: 
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: bc44742d56d744e9d0d4c1f1697d0bcd4e40488c
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="object-level-security"></a>オブジェクト レベルのセキュリティ

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

データ モデルのセキュリティを効果的に実装するための開始[ロール](../../analysis-services/tabular-models/roles-ssas-tabular.md)および行レベル フィルターのデータ モデル オブジェクトとデータに対するユーザーのアクセス許可を定義します。 以降 1400 の表形式モデルでは、定義することも、テーブル レベルのセキュリティおよび列レベルのセキュリティを含むオブジェクト レベルのセキュリティ、[ロール オブジェクト](../../analysis-services/tabular-models-scripting-language-objects/roles-object-tmsl.md)です。

## <a name="table-level-security"></a>テーブルレベルのセキュリティ

テーブル レベルのセキュリティできましていないのみアクセスを制限するテーブルのデータが悪意のあるユーザーがテーブルの場合を検出するを防ぐことができ、機密性の高いテーブル名が存在しても。 

 テーブル レベルのセキュリティは、Model.bim の JSON ベースのメタデータで設定[Tabular Model Scripting Language (TMSL)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)、または[表形式オブジェクト モデル (TOM)](../../analysis-services/tabular-model-programming-compatibility-level-1200/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo.md)です。 設定、 **metadataPermission**のプロパティ、**テーブル アクセス許可**クラス内で、[ロール オブジェクト](../../analysis-services/tabular-models-scripting-language-objects/roles-object-tmsl.md)に**none**です。

この例では、Product テーブルに関するテーブル アクセス許可クラスの metadataPermission プロパティが none に設定します。

```
"roles": [
  {
    "name": "Users",
    "description": "All allowed users to query the model",
    "modelPermission": "read",
    "tablePermissions": [
      {
        "name": "Product",
        "metadataPermission": "none"
      }
    ]
  }
```

## <a name="column-level-security"></a>列レベルのセキュリティ

列レベルのセキュリティと、テーブル レベルのセキュリティに似ていますいないのみアクセスを制限できますに列のデータも機密性の高い列の名前、悪意のあるユーザーが列を検出しないように支援します。

 列レベルのセキュリティは、Model.bim の JSON ベースのメタデータで設定[Tabular Model Scripting Language (TMSL)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)、または[表形式オブジェクト モデル (TOM)](../../analysis-services/tabular-model-programming-compatibility-level-1200/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo.md)です。 設定、 **metadataPermission**のプロパティ、 **columnPermissions**クラス内で、[ロール オブジェクト](../../analysis-services/tabular-models-scripting-language-objects/roles-object-tmsl.md)に**none**です。

この例では従業員テーブル内の基本率列に対して columnPermissions クラスの metadataPermission プロパティが none に設定します。

```
"roles": [
  {
    "name": "Users",
    "description": "All allowed users to query the model",
    "modelPermission": "read",
    "tablePermissions": [
      {
        "name": "Employee",
        "columnPermissions": [
          {
            "name": "Base Rate",
            "metadataPermission": "none"
          }
        ]
      }
    ]
  }
```

## <a name="restrictions"></a>制限

*  リレーションシップ チェーンが壊れた場合、モデルのテーブル レベルのセキュリティを設定できません。 デザイン時にエラーが生成されます。
 たとえば、テーブル A と B、および B および C の間のリレーションシップがある場合は、テーブル B を保護できません。テーブルに対するクエリがテーブル A と B、および B および C. 間のリレーションシップを通過できないテーブル B のセキュリティ保護されている場合この例では、個別の関係するようにテーブル A と B. 間

    ![テーブルレベルのセキュリティ](../../analysis-services/tabular-models/media/ssas-ols.png)  


*  セキュリティで保護されたデータへの意図しないアクセスに起こる可能性がありますので行レベルのセキュリティとオブジェクト レベルのセキュリティの異なるロール組み合わせることはできません。 このような組み合わせのロールのメンバーであるユーザーのクエリ時にエラーが生成されます。

*  動的な計算 (メジャー、Kpi、DetailRows) は、セキュリティで保護されたテーブルまたは列を参照する場合に自動的に制限されます。 メジャーを明示的にセキュリティで保護するためのメカニズムはありませんが、可能であれば暗黙的にセキュリティで保護されたテーブルまたは列を参照する式を更新することで、メジャーをセキュリティで保護します。

*  セキュリティで保護された列を参照するリレーションシップは、保護されていない列はテーブルが提供された作業します。




## <a name="see-also"></a>参照  
[Roles](../../analysis-services/tabular-models/roles-ssas-tabular.md)  
[Roles オブジェクト (TMSL)](../../analysis-services/tabular-models-scripting-language-objects/roles-object-tmsl.md)  
[テーブル モデルのスクリプト言語 (TMSL)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
[表形式オブジェクト モデル (TOM)](../../analysis-services/tabular-model-programming-compatibility-level-1200/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo.md)です。

  
