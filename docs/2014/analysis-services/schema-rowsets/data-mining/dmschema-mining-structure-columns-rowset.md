---
title: DMSCHEMA_MINING_STRUCTURE_COLUMNS 行セット |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DMSCHEMA_MINING_STRUCTURE_COLUMNS
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_STRUCTURE_COLUMNS rowset
ms.assetid: 81f25502-ac90-42f1-8ddf-7b0f9752ebfd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c012515df76b1f19712c5bf1ba828dafdc787ef7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48088372"
---
# <a name="dmschemaminingstructurecolumns-rowset"></a>DMSCHEMA_MINING_STRUCTURE_COLUMNS 行セット
  実行しているサーバーに展開されているすべてのマイニング構造の個々 の列について説明します[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]します。  
  
## <a name="rowset-columns"></a>行セットの列  
 `DMSCHEMA_MINING_STRUCTURE_COLUMNS`行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|説明|  
|-----------------|--------------------|------------|-----------------|  
|`STRUCTURE_CATALOG`|`DBTYPE_WSTR`||カタログ名。|  
|`STRUCTURE_SCHEMA`|`DBTYPE_WSTR`||修飾されていないスキーマ名。 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] はスキーマをサポートしていないため、この列は常に `NULL` になります。|  
|`STRUCTURE_NAME`|`DBTYPE_WSTR`||構造名。 この列を含めることはできません、`NULL`します。|  
|`COLUMN_NAME`|`DBTYPE_WSTR`||列の名前です。 同じパターンを共有する列間でのみ、一意性が保証されます。 たとえば、入れ子になった 2 つの列が、同じ構造内の入れ子になった 2 つの異なるテーブルに属する場合、それらの列は同じ名前を持つことがあります。|  
|`COLUMN_GUID`|`DBTYPE_GUID`||列の GUID。 GUID を使用して列を識別しないプロバイダーは、この列に `NULL` を返します。|  
|`COLUMN_PROPID`|`DBTYPE_UI4`||列のプロパティ ID。 プロパティ ID を列に関連付けないプロバイダーは、この列に `NULL` を返します。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 返します`NULL`この列にします。|  
|`ORDINAL_POSITION`|`DBTYPE_UI4`||列の序数です。 列には 1 から始まる連番が付けられます。 `NULL` 列の序数値がない場合。|  
|`COLUMN_HASDEFAULT`|`DBTYPE_BOOL`||この列に既定値があるかどうかを示すブール値。<br /><br /> 列に既定値がある場合は、`TRUE` になります。<br /><br /> 列に既定値がないか、列に既定値があるかどうかが不明の場合は、`FALSE` になります。|  
|`COLUMN_DEFAULT`|`DBTYPE_WSTR`||列の既定値です。 プロバイダーは `DBCOLUMN_DEFAULTVALUE` を公開できますが、`DBCOLUMN_HASDEFAULT` によって返される行セットの `IColumnsRowset::GetColumnsRowset` (ISO テーブル用) は公開できません。<br /><br /> 既定値が `NULL` の場合は、`COLUMN_HASDEFAULT` が `TRUE` で、`COLUMN_DEFAULT` 列が `NULL` の値になります。|  
|`COLUMN_FLAGS`|`DBTYPE_UI4`||-列の特性を記述するビットマスク。 `DBCOLUMNFLAGS` の列挙型は、ビットマスク内のビットを指定します。 この列に `NULL` 値を含めることはできません。 有効な値は次のとおりです。<br />-   **DBCOLUMNFLAGS_ISNULLABLE** (`0x20`)<br />-   **DBCOLUMNFLAGS_MAYBENULL** (`0x40`)<br />-   **DBCOLUMNFLAGS_ISLONG** (`0x80`)|  
|`IS_NULLABLE`|`DBTYPE_BOOL`||この列に既定値があるかどうかを示すブール値。<br /><br /> 列に `TRUE` を含めることができる場合は `NULL`、それ以外の場合は `FALSE` になります。|  
|`DATA_TYPE`|`DBTYPE_UI2`||列のデータ型のインジケーターです。 以下に例を示します。<br /><br /> -   "`TABLE`" = `DBTYPE_HCHAPTER`<br />-   "`TEXT`" = `DBTYPE_WCHAR`<br />-   "`LONG`" = `DBTYPE_I8`<br />-   "`DOUBLE`" = `DBTYPE_R8`<br />-   "`DATE`" = `DBTYPE_DATE`|  
|`TYPE_GUID`|`DBTYPE_GUID`||列のデータ型の GUID。 GUID を使用してデータ型を識別しないプロバイダーは、この列に `NULL` を返します。|  
|`CHARACTER_MAXIMUM_LENGTH`|`DBTYPE_UI4`||列に格納できる値の最大の長さ。 文字、バイナリ、またはビットの列の場合、これは次のいずれかになります。<br /><br /> -内の列の最大長の文字、またはビット数 (バイト単位)、それぞれ、長さが定義されている場合。 たとえば、SQL テーブルの `CHAR(5)` 列は、最大の長さが 5 になります。<br />-列の長さが定義されていない場合、、データの最大長はそれぞれ、文字、バイト、またはビット単位で入力します。<br />ゼロ (0) がある定義されている最大長の列も、データ型でもない場合。<br />-   `NULL` その他の型の列。|  
|`CHARACTER_OCTET_LENGTH`|`DBTYPE_UI4`||列の型が文字またはバイナリである場合は、列の最大の長さ (単位はオクテット (バイト))。 ゼロ (0) の値は、列に最大の長さがないことを意味します。 その他すべての型の列の場合は `NULL`。|  
|`NUMERIC_PRECISION`|`DBTYPE_UI2`||列のデータ型が `VARNUMERIC` 以外の数値データ型である場合は、列の最大有効桁数。列のデータ型が数値でないか、`NULL` である場合は、`VARNUMERIC` になります。<br /><br /> データ型を持つ列の有効桁数`DBTYPE_DECIMAL`または`DBTYPE_NUM`ERIC は、列の定義によって異なります。|  
|`NUMERIC_SCALE`|`DBTYPE_I2`||列の型インジケーターが `DBTYPE_DECIMAL`、`DBTYPE_NUMERIC`、または `DBTYPE_VARNUMERIC` である場合は、小数点以下の桁数になります。 それ以外の場合は `NULL` になります。|  
|`DATETIME_PRECISION`|`DBTYPE_UI4`||列が datetime 型または interval 型である場合は、列の DateTime の有効桁数 (秒部分の桁数)。 列のデータ型が datetime でない場合、これは `NULL` になります。|  
|`CHARACTER_SET_CATALOG`|`DBTYPE_WSTR`||文字セットが定義されているカタログ名。 プロバイダーでカタログまたは各種文字セットがサポートされていない場合は、`NULL` になります。|  
|`CHARACTER_SET_SCHEMA`|`DBTYPE_WSTR`||文字セットが定義されている、修飾されていないスキーマ名。 プロバイダーでスキーマまたは各種文字セットがサポートされていない場合は、`NULL` になります。|  
|`CHARACTER_SET_NAME`|`DBTYPE_WSTR`||文字セット名。 プロバイダーで各種文字セットがサポートされていない場合は、`NULL` になります。|  
|`COLLATION_CATALOG`|`DBTYPE_WSTR`||照合順序が定義されているカタログ名。 プロバイダーでカタログまたは各種照合順序がサポートされていない場合は、`NULL` になります。|  
|`COLLATION_SCHEMA`|`DBTYPE_WSTR`||照合順序が定義されている、修飾されていないスキーマ名。 プロバイダーでスキーマまたは各種照合順序がサポートされていない場合は、`NULL` になります。|  
|`COLLATION_NAME`|`DBTYPE_WSTR`||照合順序名。 プロバイダーで照合順序がサポートされていない場合は、`NULL` になります。|  
|`DOMAIN_CATALOG`|`DBTYPE_WSTR`||ドメインが定義されているカタログ名。 プロバイダーでカタログまたはドメインがサポートされていない場合は、`NULL` になります。|  
|`DOMAIN_SCHEMA`|`DBTYPE_WSTR`||ドメインが定義されている非修飾スキーマ名。 プロバイダーでスキーマまたはドメインがサポートされていない場合は、`NULL` になります。|  
|`DOMAIN_NAME`|`DBTYPE_WSTR`||ドメイン名。 プロバイダーでドメインがサポートされていない場合は、`NULL` になります。|  
|`DESCRIPTION`|`DBTYPE_WSTR`||列に関して人が認識できる説明。 列に説明が関連付けられていない場合は、`NULL` になります。|  
|`DISTRIBUTION_FLAG`|`DBTYPE_WSTR`||マイニング構造列の分布。<br /><br /> -   "`NORMAL`"<br />-"`LOG_NORM`AL"<br />-   "`UNIFORM`"|  
|`CONTENT_TYPE`|`DBTYPE_WSTR`||マイニング構造列のコンテンツの種類。<br /><br /> -   "`KEY`"<br />-   "`DISCRETE`"<br />-   "`CONTINUOUS`"<br />-"`DISCRETIZED(`[引数]`)`"<br />-   "`ORDERED`"<br />-   "`SEQUENCE_TIME`"<br />-   "`CYCLICAL`"<br />-   "`PROBABILITY`"<br />-   "`VARIANCE`"<br />-   "`STDEV`"<br />-   "`SUPPORT`"<br />-   "`PROBABILITY_VARIANCE`"<br />-   "`PROBABILITY_STDEV`"|  
|`MODELING_FLAG`|`DBTYPE_WSTR`||モデリング フラグのコンマ区切りの一覧。 構造列で唯一サポートされているフラグは "`NOT NULL`" です。|  
|`IS_RELATED_TO_KEY`|`DBTYPE_BOOL`||この列がキーに関連しているかどうかを示すブール値。<br /><br /> この列がキーに関連している場合は `VARIANT_TRUE`、それ以外の場合は `VARIANT_FALSE` になります。 キーが 1 つの列の場合、`RELATED_ATTRIBUTE` フィールドにはオプションでその列名を含めることができます。|  
|`RELATED_ATTRIBUTE`|`DBTYPE_WSTR`||現在の列が関連している対象列の名前、または現在の列が特殊なプロパティである対象列の名前。|  
|`CONTAINING_COLUMN`|`DBTYPE_WSTR`||この列を含んでいる `TABLE` 列の名前。 テーブルに列が含まれていない場合は、`NULL` になります。|  
|`IS_POPULATED`|`DBTYPE_BOOL`||この列に一連の可能な値があるかどうかを示すブール値。<br /><br /> 列に一連の可能な値がある場合は `TRUE`、それ以外の場合は `FALSE` になります。|  
  
## <a name="restriction-columns"></a>制限の列  
 `DMSCHEMA_MINING_STRUCTURE_COLUMNS`行セットは、次の表の列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|`STRUCTURE_CATALOG`|`DBTYPE_WSTR`|任意。|  
|`STRUCTURE_SCHEMA`|`DBTYPE_WSTR`|任意。|  
|`STRUCTURE_NAME`|`DBTYPE_WSTR`|任意。|  
|`COLUMN_NAME`|`DBTYPE_WSTR`|任意。|  
  
## <a name="see-also"></a>参照  
 [データ マイニング スキーマ行セット](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  
