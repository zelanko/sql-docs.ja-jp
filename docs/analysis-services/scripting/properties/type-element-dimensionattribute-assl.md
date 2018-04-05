---
title: Type 要素 (DimensionAttribute) (ASSL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Type Element (DimensionAttribute)
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: 64fce1f5-39b7-4d0a-ae60-21203a03bd0d
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 9cd0db2e914ffba09e7e2e3831b5815be8288e10
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="type-element-dimensionattribute-assl"></a>Type 要素 (DimensionAttribute) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]属性の型が含まれています。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DimensionAttribute>  
      ...  
   <Type>...</Type>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*通常*|  
|基数|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|Description|  
|-----------|-----------------|  
|*アカウント*|勘定科目の名前を表す属性です。|  
|*AccountNumber*|勘定科目の番号を表す属性です。|  
|*AccountType*|勘定科目の種類を表す属性です。|  
|*Address*|住所を表す属性です。|  
|*AddressBuilding*|住所のビル名を表す属性です。|  
|*AddressCity*|住所の市区町村を表す属性です。|  
|*AddressCountry*|住所の国または地域を表す属性です。|  
|*AddressFax*|FAX 番号を表す属性です。|  
|*AddressFloor*|住所の階数を表す属性です。|  
|*AddressHouse*|住所の棟番号を表す属性です。|  
|*AddressPhone*|電話番号を表す属性です。|  
|*AddressQuarter*|住所の地区を表す属性です。|  
|*AddressRoom*|住所の部屋番号を表す属性です。|  
|*AddressStateOrProvince*|住所の都道府県を表す属性です。|  
|*AddressStreet*|住所の番地を表す属性です。|  
|*AddressZip*|住所の郵便番号を表す属性です。|  
|*BOMResource*|部品表 (BOM) のリソースを表す属性です。|  
|*キャプション*|キャプションを表す属性です。|  
|*CaptionAbbreviation*|省略形を表す属性です。|  
|*CaptionDescription*|説明を表す属性です。|  
|*Channel*|チャネルを表す属性です。|  
|*市区町村*|市区町村を表す属性です。|  
|*会社*|会社を表す属性です。|  
|*大陸*|大陸を表す属性です。|  
|*国*|国または地域を表す属性です。|  
|*郡*|郡を表す属性です。|  
|*CurrencyDestination*|通貨換算の換算先通貨を表す属性です。|  
|*CurrencyISOcode*|通貨の ISO コードを表す属性です。|  
|*CurrencName*|通貨の名前を表す属性です。|  
|*CurrencySource*|通貨換算の換算元通貨を表す属性です。|  
|*CustomerGroup*|顧客のグループを表す属性です。|  
|*CustomerHousehold*|顧客の世帯を表す属性です。|  
|*顧客*|顧客を表す属性です。|  
|*日付*|日付を表す属性です。|  
|*DateCanceled*|キャンセル日を表す属性です。|  
|*DateDuration*|期間を表す属性です。|  
|*DateEnded*|終了日を表す属性です。|  
|*最終更新日時*|更新日を表す属性です。|  
|*DateStart*|開始日を表す属性です。|  
|*DayOfHalfYears*|半期の通算日を表す属性です。|  
|*DayOfMonth*|月の通算日を表す属性です。|  
|*DayOfQuarter*|四半期の通算日を表す属性です。|  
|*DayOfTrimester*|三半期の通算日を表す属性です。|  
|*DayOfWeek*|週の通算日を表す属性です。|  
|*DayOfYear*|年の通算日を表す属性です。|  
|*日数*|日を表す属性です。|  
|*DaysOfTenDays*|10 日間の通算日を表す属性です。|  
|*FiscalDay*|会計カレンダーにおける日を表す属性です。|  
|*FiscalDayOfHalfYears*|会計カレンダーにおける半期の通算日を表す属性です。|  
|*FiscalDayOfMonth*|会計カレンダーにおける月の通算日を表す属性です。|  
|*FiscalDayOfQuarter*|会計カレンダーにおける四半期の通算日を表す属性です。|  
|*FiscalDayOfTrimester*|会計カレンダーにおける三半期の通算日を表す属性です。|  
|*FiscalDayOfWeek*|会計カレンダーにおける週の通算日を表す属性です。|  
|*FiscalDayOfYear*|会計カレンダーにおける年の通算日を表す属性です。|  
|*FiscalHalfYears*|会計カレンダーにおける半期を表す属性です。|  
|*FiscalHalfYearsOfYear*|会計カレンダーにおける年の通算の半期を表す属性です。|  
|*FiscalMonth*|会計カレンダーにおける月を表す属性です。|  
|*FiscalMonthOfHalfYears*|会計カレンダーにおける半期の通算月を表す属性です。|  
|*FiscalMonthOfQuarter*|会計カレンダーにおける四半期の通算月を表す属性です。|  
|*FiscalMonthOfTrimester*|会計カレンダーにおける三半期の通算月を表す属性です。|  
|*FiscalMonthOfYear*|会計カレンダーにおける年の通算月を表す属性です。|  
|*FiscalQuarter*|会計カレンダーにおける四半期を表す属性です。|  
|*FiscalQuarterOfHalfYear*|会計カレンダーにおける半期の通算四半期を表す属性です。|  
|*FiscalQuarterOfYear*|会計カレンダーにおける年の通算四半期を表す属性です。|  
|*FiscalTrimester*|会計カレンダーにおける三半期を表す属性です。|  
|*FiscalTrimesterOfYear*|会計カレンダーにおける年の通算三半期を表す属性です。|  
|*FiscalWeek*|会計カレンダーにおける週を表す属性です。|  
|*FiscalWeekOfHalfYears*|会計カレンダーにおける半期の通算週を表す属性です。|  
|*FiscalWeekOfMonth*|会計カレンダーにおける月の通算週を表す属性です。|  
|*FiscalWeekOfQuarter*|会計カレンダーにおける四半期の通算週を表す属性です。|  
|*FiscalWeekOfTrimester*|会計カレンダーにおける三半期の通算週を表す属性です。|  
|*FiscalWeekOfYear*|会計カレンダーにおける年の通算週を表す属性です。|  
|*FiscalYear*|会計カレンダーにおける年を表す属性です。|  
|*FormattingColor*|書式設定で使用される色を表す属性です。|  
|*FormattingFont*|書式設定で使用されるフォントを表す属性です。|  
|*FormattingFontEffects*|書式設定で使用されるフォントの文字飾りを表す属性です。|  
|*FormattingFontSize*|書式設定で使用されるフォント サイズを表す属性です。|  
|*FormattingOrder*|書式設定で使用される並べ替え順序を表す属性です。|  
|*FormattingSubtotal*|小計を表す属性です。|  
|*GeoBoundaryBottom*|地理的境界の最下面の値を表す属性です。|  
|*GeoBoundaryFront*|地理的境界の最前面の値を表す属性です。|  
|*GeoBoundaryLeft*|地理的境界の最左面の値を表す属性です。|  
|*GeoBoundaryPolygon*|地理的境界の多角形定義を表す属性です。|  
|*GeoBoundaryRear*|地理的境界の最後面の値を表す属性です。|  
|*GeoBoundaryRight*|地理的境界の最右面の値を表す属性です。|  
|*GeoBoundaryTop*|地理的境界の最上面の値を表す属性です。|  
|*GeoCentroidX*|地理的領域の X 軸重心を表す属性です。|  
|*GeoCentroidY*|地理的領域の Y 軸重心を表す属性です。|  
|*GeoCentroidZ*|地理的領域の Z 軸重心を表す属性です。|  
|*HalfYears*|半期を表す属性です。|  
|*HalfYearsOfYear*|年の通算の半期を表す属性です。|  
|*時間*|時を表す属性です。|  
|*Id*|識別子またはキーを表す属性です。|  
|*IsHoliday*|祝日かどうかを表す属性です。|  
|*ISO8601DayOfWeek*|ISO 8601 カレンダーにおける週の通算日を表す属性です。|  
|*ISO8601DayOfYear*|ISO 8601 カレンダーにおける年の通算日を表す属性です。|  
|*ISO8601Days*|ISO 8601 カレンダーにおける日を表す属性です。|  
|*ISO8601Week*|ISO 8601 カレンダーにおける週を表す属性です。|  
|*ISO8601WeekOfYear*|ISO 8601 カレンダーにおける年の通算週を表す属性です。|  
|*ISO8601Year*|ISO 8601 カレンダーにおける年を表す属性です。|  
|*IsWeekDay*|平日かどうかを表す属性です。|  
|*IsWorkingDay*|営業日かどうかを表す属性です。|  
|*ManufacturingDay*|製造カレンダーにおける日を表す属性です。|  
|*ManufacturingDayOfHalfYears*|製造カレンダーにおける半期の通算日を表す属性です。|  
|*ManufacturingDayOfMonth*|製造カレンダーにおける月の通算日を表す属性です。|  
|*ManufacturingDayOfQuarter*|製造カレンダーにおける四半期の通算日を表す属性です。|  
|*ManufacturingDayOfTrimester*|製造カレンダーにおける三半期の通算日を表す属性です。|  
|*ManufacturingDayOfWeek*|製造カレンダーにおける週の通算日を表す属性です。|  
|*ManufacturingDayOfYear*|製造カレンダーにおける年の通算日を表す属性です。|  
|*ManufacturingHalfYears*|製造カレンダーにおける半期を表す属性です。|  
|*ManufacturingHalfYearsOfYear*|製造カレンダーにおける年の通算の半期を表す属性です。|  
|*ManufacturingMonth*|製造カレンダーにおける月を表す属性です。|  
|*ManufacturingMonthOfHalfYears*|製造カレンダーにおける半期の通算月を表す属性です。|  
|*ManufacturingMonthOfQuarter*|製造カレンダーにおける四半期の通算月を表す属性です。|  
|*ManufacturingMonthOfTrimester*|製造カレンダーにおける三半期の通算月を表す属性です。|  
|*ManufacturingMonthOfYear*|製造カレンダーにおける年の通算月を表す属性です。|  
|*ManufacturingQuarter*|製造カレンダーにおける四半期を表す属性です。|  
|*ManufacturingQuarterOfHalfYear*|製造カレンダーにおける半期の通算四半期を表す属性です。|  
|*ManufacturingQuarterOfYear*|製造カレンダーにおける年の通算四半期を表す属性です。|  
|*ManufacturingTrimester*|製造カレンダーにおける三半期を表す属性です。|  
|*ManufacturingTrimesterOfYear*|製造カレンダーにおける年の通算三半期を表す属性です。|  
|*ManufacturingWeek*|製造カレンダーにおける週を表す属性です。|  
|*ManufacturingWeekOfHalfYears*|製造カレンダーにおける半期の通算週を表す属性です。|  
|*ManufacturingWeekOfMonth*|製造カレンダーにおける月の通算週を表す属性です。|  
|*ManufacturingWeekOfQuarter*|製造カレンダーにおける四半期の通算週を表す属性です。|  
|*ManufacturingWeekOfTrimester*|製造カレンダーにおける三半期の通算週を表す属性です。|  
|*ManufacturingWeekOfYear*|製造カレンダーにおける年の通算週を表す属性です。|  
|*ManufacturingYear*|製造カレンダーにおける年を表す属性です。|  
|*Minutes*|分を表す属性です。|  
|*MonthOfHalfYears*|半期の通算月を表す属性です。|  
|*MonthOfQuarter*|四半期の通算月を表す属性です。|  
|*MonthOfTrimester*|三半期の通算月を表す属性です。|  
|*MonthOfYear*|年の通算月を表す属性です。|  
|*か月間*|月を表す属性です。|  
|*OrganizationalUnit*|組織単位を表す属性です。|  
|*OrgTitle*|組織の肩書きを表す属性です。|  
|*PercentOwnership*|所有権の比率を表す属性です。|  
|*PercentVoteRight*|投票権の比率を表す属性です。|  
|*担当者*|人物を表す属性です。|  
|*PersonContact*|人物の連絡先情報を表す属性です。|  
|*PersonDemographic*|人物の人口統計情報を表す属性です。|  
|*PersonFirstName*|人物の名を表す属性です。|  
|*PersonFullName*|人物の氏名を表す属性です。|  
|*PersonLastName*|人物の姓を表す属性です。|  
|*PersonMiddleName*|人物のミドル ネームを表す属性です。|  
|*PhysicalColor*|色を表す属性です。|  
|*PhysicalDensity*|密度を表す属性です。|  
|*PhysicalDepth*|奥行を表す属性です。|  
|*PhysicalHeight*|高さを表す属性です。|  
|*PhysicalSize*|サイズを表す属性です。|  
|*PhysicalVolume*|容積を表す属性です。|  
|*PhysicalWeight*|重量を表す属性です。|  
|*PhysicalWidth*|幅を表す属性です。|  
|*Point*|ポイントを表す属性です。|  
|*[郵便番号]*|郵便番号を表す属性です。|  
|*Product*|製品を表す属性です。|  
|*ProductBrand*|製品ブランドを表す属性です。|  
|*ProductCategory*|製品カテゴリを表す属性です。|  
|*ProductGroup*|製品グループを表す属性です。|  
|*ProductSKU*|製品 SKU (Stock Keeping Unit) を表す属性です。|  
|*ProjectCode*|プロジェクト コードを表す属性です。|  
|*Projectcompletion*|プロジェクトの完了状態を表す属性です。|  
|*ProjectEnddate*|プロジェクト終了日を表す属性です。|  
|*プロジェクト名*|プロジェクト名を表す属性です。|  
|*ProjectStartDate*|プロジェクト開始日を表す属性です。|  
|*プロモーション*|プロモーションを表す属性です。|  
|*QtyRangeHigh*|数量範囲の上限値を表す属性です。|  
|*QtyRangeLow*|数量範囲の下限値を表す属性です。|  
|*定量的*|数量属性を表す属性です。|  
|*QuarterOfHalfYear*|半期の通算四半期を表す属性です。|  
|*"Quarterofyear"*|年の通算四半期を表す属性です。|  
|*四半期*|四半期を表す属性です。|  
|*レート*|レートを表す属性です。|  
|*RateType*|レートの種類を表す属性です。|  
|*Region*|顧客によって定義された領域を表す属性です。|  
|*通常*|標準属性を表す属性です。|  
|*RelationToParent*|親へのリレーションを表す属性です。|  
|*ReportingDay*|レポート カレンダーにおける日を表す属性です。|  
|*ReportingDayOfHalfYears*|レポート カレンダーにおける半期の通算日を表す属性です。|  
|*ReportingDayOfMonth*|レポート カレンダーにおける月の通算日を表す属性です。|  
|*ReportingDayOfQuarter*|レポート カレンダーにおける四半期の通算日を表す属性です。|  
|*ReportingDayOfTrimester*|レポート カレンダーにおける三半期の通算日を表す属性です。|  
|*ReportingDayOfWeek*|レポート カレンダーにおける週の通算日を表す属性です。|  
|*ReportingDayOfYear*|レポート カレンダーにおける年の通算日を表す属性です。|  
|*ReportingHalfYears*|レポート カレンダーにおける半期を表す属性です。|  
|*ReportingHalfYearsOfYear*|レポート カレンダーにおける年の通算の半期を表す属性です。|  
|*ReportingMonth*|レポート カレンダーにおける月を表す属性です。|  
|*ReportingMonthOfHalfYears*|レポート カレンダーにおける半期の通算月を表す属性です。|  
|*ReportingMonthOfQuarter*|レポート カレンダーにおける四半期の通算月を表す属性です。|  
|*ReportingMonthOfTrimester*|レポート カレンダーにおける三半期の通算月を表す属性です。|  
|*ReportingMonthOfYear*|レポート カレンダーにおける年の通算月を表す属性です。|  
|*ReportingQuarter*|レポート カレンダーにおける四半期を表す属性です。|  
|*ReportingQuarterOfHalfYear*|レポート カレンダーにおける半期の通算四半期を表す属性です。|  
|*ReportingQuarterOfYear*|レポート カレンダーにおける年の通算四半期を表す属性です。|  
|*ReportingTrimester*|レポート カレンダーにおける三半期を表す属性です。|  
|*ReportingTrimesterOfYear*|レポート カレンダーにおける年の通算三半期を表す属性です。|  
|*ReportingWeek*|レポート カレンダーにおける週を表す属性です。|  
|*ReportingWeekOfHalfYears*|レポート カレンダーにおける半期の通算週を表す属性です。|  
|*ReportingWeekOfMonth*|レポート カレンダーにおける月の通算週を表す属性です。|  
|*ReportingWeekOfQuarter*|レポート カレンダーにおける四半期の通算週を表す属性です。|  
|*ReportingWeekOfTrimester*|レポート カレンダーにおける三半期の通算週を表す属性です。|  
|*ReportingWeekOfYear*|レポート カレンダーにおける年の通算週を表す属性です。|  
|*ReportingYear*|レポート カレンダーにおける年を表す属性です。|  
|*担当者*|代表者を表す属性です。|  
|*シナリオ*|シナリオを表す属性です。|  
|*Seconds*|秒を表す属性です。|  
|*Sequence*|シーケンス属性を表す属性です。|  
|*ShortCaption*|短いキャプションを表す属性です。|  
|*StateOrProvince*|都道府県を表す属性です。|  
|*TenDayOfHalfYears*|半期の通算の旬を表す属性です。|  
|*TenDayOfQuarter*|四半期の通算の旬を表す属性です。|  
|*TenDayOfTrimester*|三半期の通算の旬を表す属性です。|  
|*TenDayOfYear*|年の通算の旬を表す属性です。|  
|*TenDays*|旬 (10 日間) を表す属性です。|  
|*TenDaysOfMonth*|月の通算の旬を表す属性です。|  
|*三半期*|三半期を表す属性です。|  
|*TrimesterOfYear*|年の通算三半期を表す属性です。|  
|*UndefinedTime*|未定義の期間を表す属性です。|  
|*Utility*|ユーティリティを表す属性です。|  
|*バージョン*|バージョンを表す属性です。|  
|*WebHtml*|HTML コンテンツを表す属性です。|  
|*WebMailAlias*|電子メールの別名を表す属性です。|  
|*WebUrl*|URL アドレスを表す属性です。|  
|*WebXmlOrXsl*|XML または XSL コンテンツを表す属性です。|  
|*WeekOfHalfYears*|半期の通算週を表す属性です。|  
|*WeekOfMonth*|月の通算週を表す属性です。|  
|*WeekOfQuarter*|四半期の通算週を表す属性です。|  
|*WeekOfTrimester*|三半期の通算週を表す属性です。|  
|*WeekOfYear*|年の通算週を表す属性です。|  
|*週*|週を表す属性です。|  
|*年*|年を表す属性です。|  
  
 許可される値に対応する列挙**型**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.AttributeType>します。  
  
 親に対応する要素**型**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.DimensionAttribute>します。  
  
## <a name="see-also"></a>参照  
 [Attributes 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/collections/attributes-element-assl.md)   
 [Dimension 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/dimension-element-assl.md)   
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
