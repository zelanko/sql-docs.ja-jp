---
title: DMSCHEMA_MINING_COLUMNS 行セット |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DMSCHEMA_MINING_COLUMNS
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_COLUMNS rowset
ms.assetid: ae35ccde-4438-46f4-8611-40b2b1a42fce
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: d53285b088b471ad7a5fca87536cc897db8126d9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36165933"
---
# <a name="dmschemaminingcolumns-rowset"></a>DMSCHEMA_MINING_COLUMNS 行セット
  すべてのデータ マイニング モデルの個々 の列について説明します[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。 この行セットは、現在のカタログに制限されます。  
  
## <a name="rowset-columns"></a>行セットの列  
 `DMSCHEMA_MINING_COLUMNS`行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|説明|  
|-----------------|--------------------|------------|-----------------|  
|`MODEL_CATALOG`|`DBTYPE_WSTR`||カタログ名。 モデルがメンバーとして含まれているデータベースの名前を使用して設定されます。|  
|`MODEL_SCHEMA`|`DBTYPE_WSTR`||修飾されていないスキーマ名。 この列は [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] でサポートされていないため、常に `NULL` が格納されます。|  
|`MODEL_NAME`|`DBTYPE_WSTR`||マイニング モデル名。 この列には、列が関連付けられているマイニング モデルの名前が格納され、空になることはありません。|  
|`COLUMN_NAME`|`DBTYPE_WSTR`||列の名前です。|  
|`COLUMN_GUID`|`DBTYPE_GUID`||列の GUID。 この列は [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] でサポートされていないため、常に `NULL` が格納されます。|  
|`COLUMN_PROPID`|`DBTYPE_UI4`||列のプロパティ ID。 この列は [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] でサポートされていないため、常に `NULL` が格納されます。|  
|`ORDINAL_POSITION`|`DBTYPE_UI4`||列の位置を表す序数。 列には 1 から始まる連番が付けられます。 列に安定した序数が付けられていない場合、この列には `NULL` が格納されます。|  
|`COLUMN_HAS_DEFAULT`|`DBTYPE_BOOL`||列に既定値があるかどうかを示すブール値。<br /><br /> 列に既定値がある場合は `TRUE`、それ以外の場合は `FALSE` になります。|  
|`COLUMN_DEFAULT`|`DBTYPE_WSTR`||列の既定値です。<br /><br /> 既定値が `NULL` 値である場合、`COLUMN_HASDEFAULT` には `TRUE` が格納され、この列には `NULL` が格納されます。|  
|`COLUMN_FLAGS`|`DBTYPE_UI4`||列の特性を記述するビットマスク。 `DBCOLUMNFLAGS` の列挙型は、ビットマスク内のビットを指定します。 この列が空になることはありません。|  
|`IS_NULLABLE`|`DBTYPE_BOOL`||列で NULL 値が許容されるかどうかを示すブール値。<br /><br /> 列で NULL 値が許容されないことがわかっている場合は `FALSE`、それ以外の場合は `TRUE` になります。|  
|`DATA_TYPE`|`DBTYPE_UI2`||列のデータ型のインジケーターです。 次の一覧に、返されるインジケーターの種類の例を示します。<br /><br /> "`TABLE`" は `DBTYPE_HCHAPTER` を返します。<br /><br /> "`TEXT`" は `DBTYPE_WCHAR` を返します。<br /><br /> "`LONG`" は `DBTYPE_I8` を返します。<br /><br /> "`DOUBLE`" は `DBTYPE_R8` を返します。<br /><br /> "`DATE`" は `DBTYPE_DATE` を返します。|  
|`TYPE_GUID`|`DBTYPE_GUID`||列のデータ型の GUID。 この列は [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] でサポートされていないため、常に `VT_NULL` が格納されます。|  
|`CHARACTER_MAXIMUM_LENGTH`|`DBTYPE_UI4`||列に格納できる値の最大の長さ。 文字、バイナリ、またはビットの列の場合、これは次のいずれかになります。<br /><br /> 文字、バイト、またはビット単位の長さが定義されている場合、型の列にそれぞれの列の最大長。 たとえば、SQL テーブルの `CHAR(5)` 列は、最大の長さが 5 になります。<br />文字、バイト、またはビット列の長さが定義されていない場合、型の列にそれぞれのデータ型の最大長。<br />-ゼロ (0) 場合は、列でも、データ型がある定義されている最大長。<br />-   `NULL` その他のすべての型の列|  
|`CHARACTER_OCTET_LENGTH`|`DBTYPE_UI4`||列の型が文字またはバイナリである場合は、列の最大の長さ (単位はオクテット (バイト))。 ゼロ (0) の値は、列に最大の長さがないことを意味します。 その他の種類の列の場合、この列には `NULL` が格納されます。|  
|`NUMERIC_PRECISION`|`DBTYPE_UI2`||列のデータ型が `VARNUMERIC` 以外の数値データ型である場合は、列の最大有効桁数。<br /><br /> 列のデータ型が数値でないか、`NULL` である場合は、`VARNUMERIC` になります。<br /><br /> データ型が `DBTYPE_DECIMAL` または `DBTYPE_NUMERIC` である列の有効桁数は、列の定義によって異なります。|  
|`NUMERIC_SCALE`|`DBTYPE_I2`||列の型インジケーターが `DBTYPE_DECIMAL`、`DBTYPE_NUMERIC`、または `DBTYPE_VARNUMERIC` である場合は、小数点以下の桁数になります。 それ以外の場合、この列には `VT_NULL` が格納されます。|  
|`DATETIME_PRECISION`|`DBTYPE_UI4`||列のデータ型が DateTime 型または interval 型である場合は、列の日付/時刻の有効桁数 (秒部分の桁数)。それ以外の場合は `NULL` になります。|  
|`CHARACTER_SET_CATALOG`|`DBTYPE_WSTR`||文字セットが定義されているカタログ名。 この列は [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] でサポートされていないため、常に `NULL` が格納されます。|  
|`CHARACTER_SET_SCHEMA`|`DBTYPE_WSTR`||文字セットが定義されている非修飾スキーマ名。 この列は [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] でサポートされていないため、常に `NULL` が格納されます。|  
|`CHARACTER_SET_NAME`|`DBTYPE_WSTR`||文字セット名。 この列は [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] でサポートされていないため、常に `NULL` が格納されます。|  
|`COLLATION_CATALOG`|`DBTYPE_WSTR`||照合順序が定義されているカタログ名。 この列は [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] でサポートされていないため、常に `NULL` が格納されます。|  
|`COLLATION_SCHEMA`|`DBTYPE_WSTR`||照合順序が定義されている非修飾スキーマ名。 この列は [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] でサポートされていないため、常に `NULL` が格納されます。|  
|`COLLATION_NAME`|`DBTYPE_WSTR`||照合順序名。 この列は [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] でサポートされていないため、常に `NULL` が格納されます。|  
|`DOMAIN_CATALOG`|`DBTYPE_WSTR`||ドメインが定義されているカタログ名。 この列は [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] でサポートされていないため、常に `NULL` が格納されます。|  
|`DOMAIN_SCHEMA`|`DBTYPE_WSTR`||ドメインが定義されている非修飾スキーマ名。 この列は [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] でサポートされていないため、常に `NULL` が格納されます。|  
|`DOMAIN_NAME`|`DBTYPE_WSTR`||ドメイン名。 この列は [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] でサポートされていないため、常に `NULL` が格納されます。|  
|`DESCRIPTION`|`DBTYPE_WSTR`||列についてのわかりやすい説明。この列は [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] でサポートされていないため、常に `NULL` が格納されます。|  
|`DISTRIBUTION_FLAG`|`DBTYPE_WSTR`||列の統計分布の記述。 この列の値は次のいずれかになります。<br /><br /> -   "`NORMAL`"<br />-   "`LOG_NORMAL`"<br />-   "`UNIFORM`"|  
|`CONTENT_TYPE`|`DBTYPE_WSTR`||列のコンテンツの記述。 この列の値は次のいずれかになります。<br /><br /> -   "`KEY`"<br />-   "`DISCRETE`"<br />-   "`CONTINUOUS`"<br />-"`DISCRETIZED(`[引数]`)`"<br />-   "`ORDERED`"<br />-   "`KEY TIME`"<br />-   "`CYCLICAL`"<br />-   "`PROBABILITY`"<br />-   "`VARIANCE`"<br />-   "`STDEV`"<br />-   "`SUPPORT`"<br />-   "`PROBABILITY_VARIANCE`"<br />-   "`PROBABILITY_STDEV`"<br />-   `"KEY SEQUENCE`"|  
|`MODELING_FLAG`|`DBTYPE_WSTR`||フラグのコンマ区切りの一覧。 定義済みフラグには次のものがあります。<br /><br /> -   "`MODEL_EXISTENCE_ONLY`"<br />-   "`REGRESSOR`"<br /><br /> アルゴリズムに固有のモデリング フラグがこの列に格納されることもあります。|  
|`IS_RELATED_TO_KEY`|`DBTYPE_BOOL`||列がキーに関連するかどうかを示すブール値。<br /><br /> この列がキーに関連している場合は `TRUE` になります。 キーが 1 つの列である場合、必要に応じてその列名を `RELATED_ATTRIBUTE` フィールドに格納することができます。|  
|`RELATED_ATTRIBUTE`|`DBTYPE_WSTR`||対象の列を現在の列が関連するかが特殊なプロパティの名前。|  
|`IS_INPUT`|`DBTYPE_BOOL`||列が入力列であるかどうかを示すブール値。<br /><br /> これが入力列である場合は `VARIANT_TRUE` になります。|  
|`IS_PREDICTABLE`|`DBTYPE_BOOL`||列が予測可能列であるかどうかを示すブール値。<br /><br /> 列が予測可能である場合は `TRUE` になります。|  
|`CONTAINING_COLUMN`|`DBTYPE_WSTR`||この列を格納する `TABLE` 列の名前。 この列が別の列に格納されない場合、この列には `NULL` が格納されます。|  
|`PREDICTION_SCALAR_FUNCTIONS`|`DBTYPE_WSTR`||列で実行できるスカラー関数のコンマ区切りの一覧。|  
|`PREDICTION_TABLE_FUNCTIONS`|`DBTYPE_WSTR`||列に適用できる関数のコンマ区切りの一覧。 これらの関数はテーブルを返します。 一覧の形式は次のとおりです。<br /><br /> `<function name>(<column1> [, <column2>], ...)`<br /><br /> この形式により、クライアント アプリケーションでそれぞれの関数のシグネチャ (パラメーターの一覧) を判断することができます。|  
|`IS_POPULATED`|`DBTYPE_BOOL`||この列が一連の可能な値でトレーニングされているかどうかを示すブール値。<br /><br /> 列が一連の可能な値でトレーニングされている場合は `TRUE` になります。<br /><br /> 列に値が設定されていない場合は `FALSE` が格納されます。|  
|`PREDICTION_SCORE`|`DBTYPE_R8`||列の予測におけるモデルのスコア。 スコアはモデルの精度を測定するために使用されます。|  
|`SOURCE_COLUMN`|`DBTYPE_WSTR`||現在のマイニング列のソース マイニング構造列の名前。|  
  
## <a name="restriction-columns"></a>制限の列  
 `DMSCHEMA_MINING_COLUMNS`行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|`MODEL_CATALOG`|`DBTYPE_WSTR`|任意。|  
|`MODEL_SCHEMA`|`DBTYPE_WSTR`|任意。|  
|`MODEL_NAME`|`DBTYPE_WSTR`|任意。|  
|`COLUMN_NAME`|`DBTYPE_WSTR`|任意。|  
  
## <a name="see-also"></a>参照  
 [データ マイニング スキーマ行セット](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  