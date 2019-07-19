---
title: Analysis Services 表形式モデルのオブジェクト レベルのセキュリティ |Microsoft Docs
ms.date: 03/08/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: d354aa64e8b6a1e98941011c30550a056f4c01c9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68162788"
---
# <a name="object-level-security"></a>オブジェクト レベルのセキュリティ
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
データ モデルのセキュリティを効果的に実装すると開始[ロール](../../analysis-services/tabular-models/roles-ssas-tabular.md)と行レベル フィルターのデータ モデル オブジェクトおよびデータにユーザーのアクセス許可を定義します。 以降表形式 1400 モデルでは、定義することも、テーブル レベルのセキュリティとの列レベルのセキュリティを含むオブジェクト レベルのセキュリティ、[ロール オブジェクト](https://docs.microsoft.com/bi-reference/tmsl/roles-object-tmsl)します。

## <a name="table-level-security"></a>テーブルレベルのセキュリティ

テーブル レベルのセキュリティできましていないのみアクセスを制限するテーブルのデータも悪意のあるユーザーがテーブルを検出するを防ぐため、機密性の高いテーブル名が存在します。 

 テーブル レベルのセキュリティは、Model.bim で JSON ベースのメタデータで設定[Tabular Model Scripting Language (TMSL)](https://docs.microsoft.com/bi-reference/tmsl/tabular-model-scripting-language-tmsl-reference)、または[表形式オブジェクト モデル (TOM)](https://docs.microsoft.com/bi-reference/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo)します。 設定、 **metadataPermission**のプロパティ、**テーブル アクセス許可**クラス、[ロール オブジェクト](https://docs.microsoft.com/bi-reference/tmsl/roles-object-tmsl)に**none**します。

この例での Product テーブルのテーブル アクセス許可クラスの metadataPermission プロパティが none に設定します。

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

列レベルのセキュリティと、テーブル レベルのセキュリティのようなことができますされませんのみアクセスを制限する列のデータも機密性の高い列の名前、悪意のあるユーザーが列を検出しないように支援します。

 列レベルのセキュリティは、Model.bim で JSON ベースのメタデータで設定[Tabular Model Scripting Language (TMSL)](https://docs.microsoft.com/bi-reference/tmsl/tabular-model-scripting-language-tmsl-reference)、または[表形式オブジェクト モデル (TOM)](https://docs.microsoft.com/bi-reference/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo)します。 設定、 **metadataPermission**のプロパティ、 **columnPermissions**クラス、[ロール オブジェクト](https://docs.microsoft.com/bi-reference/tmsl/roles-object-tmsl)に**none**します。

この例での Employees テーブルの基本料金列 columnPermissions クラスの metadataPermission プロパティが none に設定します。

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

*  リレーションシップ チェーンが中断している場合、モデルのテーブル レベルのセキュリティを設定できません。 デザイン時にエラーが生成されます。
 たとえば、テーブル A と B、および B および C の間のリレーションシップがある場合は、テーブル B を保護できません。テーブルに対するクエリ テーブル B のセキュリティ保護されている場合は、テーブル A と B、および B および C. 間のリレーションシップを移行できません。ここでは、別のリレーションシップはテーブル A と B. 間構成でした。

    ![テーブルレベルのセキュリティ](../../analysis-services/tabular-models/media/ssas-ols.png)  


*  セキュリティで保護されたデータに意図しないアクセスが入り込む可能性があるために、行レベルのセキュリティとオブジェクト レベルのセキュリティがさまざまなロールから組み合わせることはできません。 このような組み合わせは、ロールのメンバーであるユーザーのクエリ時にエラーが生成されます。

*  動的な計算 (メジャー、Kpi、DetailRows) は、セキュリティで保護されたテーブルまたは列を参照する場合に自動的に制限されます。 メジャーを明示的にセキュリティで保護するためのメカニズムはありませんは、暗黙的にセキュリティで保護されたテーブルまたは列を参照する式を更新することで、メジャーをセキュリティで保護できます。

*  セキュリティで保護された列を参照するリレーションシップは、列はテーブルが保護されていない限り機能します。




## <a name="see-also"></a>関連項目  
[Roles](../../analysis-services/tabular-models/roles-ssas-tabular.md)  
[Roles オブジェクト (TMSL)](https://docs.microsoft.com/bi-reference/tmsl/roles-object-tmsl)  
[テーブル モデルのスクリプト言語 (TMSL)](https://docs.microsoft.com/bi-reference/tmsl/tabular-model-scripting-language-tmsl-reference)  
[表形式オブジェクト モデル (TOM)](https://docs.microsoft.com/bi-reference/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo)します。

  
