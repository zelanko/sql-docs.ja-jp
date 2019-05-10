---
title: ディメンションの属性の追加 |Microsoft Docs
ms.date: 05/06/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 54402868b05ff001fbe00cdd9d914ebd1686271b
ms.sourcegitcommit: 54c8420b62269f6a9e648378b15127b5b5f979c1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65403774"
---
# <a name="lesson-2-3---adding-attributes-to-dimensions"></a>レッスン 2-3-ディメンションへの属性の追加
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]

ディメンションを定義したので、ディメンションの各データ要素を表す属性をディメンションに読み込めるようになりました。 属性は、通常、データ ソース ビューのフィールドに基づいています。 ディメンションに属性を追加するときに、データ ソース ビュー内の任意のテーブルのフィールドを含めることができます。  
  
この実習では、ディメンション デザイナーを使用して、属性を Customer ディメンションと Product ディメンションに追加します。 Customer ディメンションには、Customer テーブルと Geography テーブルの両方のフィールドに基づく属性が含まれます。  
  
## <a name="adding-attributes-to-the-customer-dimension"></a>Customer ディメンションへの属性の追加  
  
#### <a name="to-add-attributes"></a>属性を追加するには  
  
1.  Customer ディメンションのディメンション デザイナーを開きます。 これを行うには、ソリューション エクスプローラーの **[ディメンション]** ノードで **[Customer]** ディメンションをダブルクリックします。  
  
2.  **[属性]** ペインに、キューブ ウィザードによって作成された Customer Key 属性および Geography Key 属性が表示されます。  
  
3.  **[ディメンション構造]** タブのツール バーで、 **[データ ソース ビュー]** ペイン内のテーブルを表示するための [ズーム] アイコンが 100% に設定されていることを確認します。  
  
4.  次の列を、 **[データ ソース ビュー]** ペインの **Customer** テーブルから **[属性]** ペインにドラッグします。  
  
    -   **BirthDate**  
  
    -   **MaritalStatus**  
  
    -   **Gender**  
  
    -   **EmailAddress**  
  
    -   **YearlyIncome**  
  
    -   **TotalChildren**  
  
    -   **NumberChildrenAtHome**  
  
    -   **EnglishEducation**  
  
    -   **EnglishOccupation**  
  
    -   **HouseOwnerFlag**  
  
    -   **NumberCarsOwned**  
  
    -   **Phone**  
  
    -   **DateFirstPurchase**  
  
    -   **CommuteDistance**  
  
5.  次の列を、 **[データ ソース ビュー]** ペインの **Geography** テーブルから **[属性]** ペインにドラッグします。  
  
    -   **City**  
  
    -   **StateProvinceName**  
  
    -   **EnglishCountryRegionName**  
  
    -   **PostalCode**  
  
6.  [ファイル] メニューの **[すべてを保存]** をクリックします。  
  
## <a name="adding-attributes-to-the-product-dimension"></a>Product ディメンションへの属性の追加  
  
#### <a name="to-add-attributes"></a>属性を追加するには  
  
1.  Product ディメンションのディメンション デザイナーを開きます。 ソリューション エクスプローラーで、 **Product** ディメンションをダブルクリックします。  
  
2.  **[属性]** ペインに、キューブ ウィザードによって作成された Product Key 属性が表示されます。  
  
3.  **[ディメンション構造]** タブのツール バーで、 **[データ ソース ビュー]** ペイン内のテーブルを表示するための [ズーム] アイコンが 100% に設定されていることを確認します。  
  
4.  次の列を、 **[データ ソース ビュー]** ペインの **Product** テーブルから **[属性]** ペインにドラッグします。  
  
    -   **StandardCost**  
  
    -   **色**  
  
    -   **SafetyStockLevel**  
  
    -   **ReorderPoint**  
  
    -   **ListPrice**  
  
    -   **Size**  
  
    -   **SizeRange**  
  
    -   **Weight**  
  
    -   **DaysToManufacture**  
  
    -   **ProductLine**  
  
    -   **DealerPrice**  
  
    -   **Class**  
  
    -   **スタイル**  
  
    -   **ModelName**  
  
    -   **StartDate**  
  
    -   **EndDate**  
  
    -   **ステータス**  
  
5.  [ファイル] メニューの **[すべてを保存]** をクリックします。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[キューブとディメンションのプロパティの確認](lesson-2-4-reviewing-cube-and-dimension-properties.md)  
  
## <a name="see-also"></a>参照  
[ディメンションの属性のプロパティの参照](../multidimensional-models/dimension-attribute-properties-reference.md)  
  
  
  
