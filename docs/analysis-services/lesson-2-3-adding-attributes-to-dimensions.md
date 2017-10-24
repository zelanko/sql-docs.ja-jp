---
title: "ディメンションの属性の追加 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 80551dad-97ac-40d0-90af-b810780321ce
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0642ac7688f86ce5fb23f1af50e9ced776993216
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="lesson-2-3---adding-attributes-to-dimensions"></a>レッスン 2 ~ 3-ディメンションの属性の追加
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
  
6.  [ファイル] メニューの **[すべてを保存]**をクリックします。  
  
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
  
    -   **サイズ**  
  
    -   **SizeRange**  
  
    -   **Weight**  
  
    -   **DaysToManufacture**  
  
    -   **ProductLine**  
  
    -   **DealerPrice**  
  
    -   **クラス**  
  
    -   **スタイル**  
  
    -   **ModelName**  
  
    -   **StartDate**  
  
    -   **EndDate**  
  
    -   **[状態]**  
  
5.  [ファイル] メニューの **[すべてを保存]**をクリックします。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[キューブとディメンションのプロパティの確認](../analysis-services/lesson-2-4-reviewing-cube-and-dimension-properties.md)  
  
## <a name="see-also"></a>参照  
[ディメンションの属性のプロパティの参照](../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)  
  
  
  

