---
title: "レッスン 3: 列名の変更 | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 5fc8ba1a-2b30-4775-9b3b-c09dee711b3e
caps.latest.revision: 22
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
robots: noindex,nofollow
---
# レッスン 3: 列名の変更
このレッスンでは、インポートした各テーブル内の多くの列の名前を変更します。 名前を変更することで、列がより識別しやすくなり、モデル デザイナー内でも、またクライアント アプリケーションでユーザーがフィールドを選択する際にも、移動が行いやすくなります。 詳細については、「[テーブルまたは列名の変更 (SSAS テーブル)](../analysis-services/tabular-models/rename-a-table-or-column-ssas-tabular.md)」を参照してください。  
  
> [!IMPORTANT]  
> 列名の変更は、このチュートリアルを完了するために必ずしも必要ではありませんが、残りのレッスン (リレーションシップを作成するレッスンと、DAX 数式を使用して計算列とメジャーを作成するレッスン) では、このレッスンに記載されているわかりやすい列名が使用されます。 列名を変更しない場合は、レッスン 5、6、および 7 を行う際に、このレッスンで示す元のソース列名を使用するように DAX 数式を編集してください。  
  
このレッスンの推定所要時間: **20 分**  
  
## 前提条件  
このトピックはテーブル モデリング チュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンの実習を行う前に、前のレッスン「[レッスン 2: データの追加](../analysis-services/lesson-2-add-data.md)」を完了している必要があります。  
  
## 列名の変更  
  
#### 列名を変更するには  
  
1.  モデル デザイナーで、**Customer** テーブル (タブ) をクリックします。  
  
    タブをクリックすると、そのテーブルがモデル デザイナー ウィンドウでアクティブになります。  
  
2.  **CustomerKey** という列名をダブルクリックし、「**Customer  Id**」と入力してから Enter キーを押します。  
  
    > [!TIP]  
    > 列名は、列の **[プロパティ]** ウィンドウの **Column Name** プロパティか、またはダイアグラム ビューで変更することもできます。  
  
3.  **Customer** テーブル内の残りの列と、その他のテーブル内の列についても、ソース名を次の表示名に置き換えて名前変更します。  
  
    **Customer テーブル**  
  
    |ソース名|表示名|  
    |---------------|-----------------|  
    |GeographyKey|Geography Id|  
    |CustomerAlternateKey|Customer Alternate Id|  
    |FirstName|First Name|  
    |MiddleName|Middle Name|  
    |LastName|Last Name|  
    |NameStyle|Name Style|  
    |BirthDate|Birth Date|  
    |MaritalStatus|Marital Status|  
    |EmailAddress|Email Address|  
    |YearlyIncome|Yearly Income|  
    |TotalChildren|Total Children|  
    |NumberChildrenAtHome|Number of Children At Home|  
    |EnglishEducation|Education|  
    |EnglishOccupation|Occupation|  
    |HouseOwnerFlag|Owns House|  
    |NumberCarsOwned|Number of Cars Owned|  
    |AddressLine1|Address Line 1|  
    |AddressLine2|Address Line 2|  
    |Phone|Phone Number|  
    |DateFirstPurchase|Date of First Purchase|  
    |CommuteDistance|Commute Distance|  
  
    **日付**  
  
    |ソース名|表示名|  
    |---------------|-----------------|  
    |FullDateAlternateKey|日付|  
    |DayNumberOfWeek|Day Number of Week|  
    |EnglishDayNameOfWeek|Day Name|  
    |DayNumberOfMonth|Day of Month|  
    |DayNumberOfYear|Day of Year|  
    |WeekNumberOfYear|Week Number of Year|  
    |EnglishMonthName|Month Name|  
    |MonthNumberOfYear|Month|  
    |CalendarQuarter|Calendar Quarter|  
    |CalendarYear|Calendar Year|  
    |CalendarSemester|Calendar Semester|  
    |FiscalQuarter|Fiscal Quarter|  
    |FiscalYear|Fiscal Year|  
    |FiscalSemester|Fiscal Semester|  
  
    **Geography**  
  
    |ソース名|表示名|  
    |---------------|-----------------|  
    |GeographyKey|Geography Id|  
    |StateProvinceCode|State Province Code|  
    |StateProvinceName|State Province Name|  
    |CountryRegionCode|Country Region Code|  
    |EnglishCountryRegionName|Country Region Name|  
    |PostalCode|Postal Code|  
    |SalesTerritoryKey|Sales Territory Id|  
  
    **Product**  
  
    |ソース名|表示名|  
    |---------------|-----------------|  
    |ProductKey|Product Id|  
    |ProductAlternateKey|Product Alternate Id|  
    |ProductSubcategoryKey|Product Subcategory Id|  
    |WeightUnitMeasureCode|Weight Unit Code|  
    |SizeUnitMeasureCode|Size Unit Code|  
    |EnglishProductName|製品名|  
    |StandardCost|Standard Cost|  
    |FinishedGoodsFlag|Is Finished Product|  
    |SafetyStockLevel|Safety Stock Level|  
    |ReorderPoint|Reorder Point|  
    |ListPrice|List Price|  
    |SizeRange|Size Range|  
    |DaysToManufacture|Days to Manufacture|  
    |ProductLine|Product Line|  
    |Dealer Price|Dealer Price|  
    |ModelName|Model Name|  
    |LargePhoto|Large Photo|  
    |EnglishDescription|Description|  
    |StartDate|Product Start Date|  
    |EndDate|Product End Date|  
    |[状態]|Product Status|  
  
    **Product Category**  
  
    |ソース名|表示名|  
    |---------------|-----------------|  
    |ProductCategoryKey|Product Category Id|  
    |ProductCategoryAlternateKey|Product Category Alternate Id|  
    |EnglishProductCategoryName|Product Category Name|  
  
    **Product Subcategory**  
  
    |ソース名|表示名|  
    |---------------|-----------------|  
    |ProductSubcategoryKey|Product Subcategory Id|  
    |ProductSubcategoryAlternateKey|Product Subcategory Alternate Id|  
    |EnglishProductSubcategoryName|Product Subcategory Name|  
    |ProductCategoryKey|Product Category Id|  
  
    **Internet Sales**  
  
    |ソース名|表示名|  
    |---------------|-----------------|  
    |ProductKey|Product Id|  
    |CustomerKey|Customer Id|  
    |PromotionKey|Promotion Id|  
    |CurrencyKey|Currency Id|  
    |SalesTerritoryKey|Sales Territory Id|  
    |SalesOrderNumber|Sales Order Number|  
    |SalesOrderLineNumber|Sales Order Line Number|  
    |RevisionNumber|Revision Number|  
    |OrderQuantity|Order Quantity|  
    |UnitPrice|Unit Price|  
    |ExtendedAmount|Extended Amount|  
    |UnitPriceDiscountPct|Unit Price Discount Pct|  
    |DiscountAmount|Discount Amount|  
    |ProductStandardCost|Product Standard Cost|  
    |TotalProductCost|Total Product Cost|  
    |SalesAmount|Sales Amount|  
    |TaxAmt|Tax Amt|  
    |CarrierTrackingNumber|Carrier Tracking Number|  
    |CustomerPONumber|Customer PO Number|  
    |OrderDate|Order Date|  
    |DueDate|Due Date|  
    |ShipDate|Ship Date|  
  
## 次の手順  
このチュートリアルを続行するには、次のレッスン「[レッスン 4: 日付テーブルとしてマーク](../analysis-services/lesson-4-mark-as-date-table.md)」に進んでください。  
  
  
  
