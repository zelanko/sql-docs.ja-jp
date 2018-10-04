---
title: DBSCHEMA_PROVIDER_TYPES 行セット |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DBSCHEMA_PROVIDER_TYPES
topic_type:
- apiref
helpviewer_keywords:
- DBSCHEMA_PROVIDER_TYPES rowset
ms.assetid: 255e01ba-53a9-478d-9b86-45faba76710e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2840e67e8ddb1b412164bacc6c26ff9ac0c90e10
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48049190"
---
# <a name="dbschemaprovidertypes-rowset"></a>DBSCHEMA_PROVIDER_TYPES 行セット
  データ プロバイダーによってサポートされている (基本) データ型を識別します。  
  
## <a name="rowset-columns"></a>行セットの列  
 `DBSCHEMA_PROVIDER_TYPES`行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|説明|  
|-----------------|--------------------|------------|-----------------|  
|`TYPE_NAME`|`DBTYPE_WSTR`||プロバイダー固有のデータ型名。|  
|`DATA_TYPE`|`DBTYPE_UI2`||データ型のインジケーター。|  
|`COLUMN_SIZE`|`DBTYPE_UI4`||プロバイダーによってこの型に対して定義された最大値または長さのいずれかを表す非数値の列またはパラメーターの長さ。 文字データの場合、これは最大値または定義済みの長さを文字数で表したものです。 DateTime 型の場合、これは文字列の長さです (秒部分に許容される最大有効桁数を想定)。<br /><br /> データ型が Numeric の場合、これはデータ型の有効桁数の上限値です。|  
|`LITERAL_PREFIX`|`DBTYPE_WSTR`||テキスト コマンドでこの型のリテラルのプレフィックスとして使用する文字または文字列。|  
|`LITERAL_SUFFIX`|`DBTYPE_WSTR`||テキスト コマンドでこの型のリテラルのサフィックスとして使用する文字または文字列。|  
|`CREATE_PARAMS`|`DBTYPE_WSTR`||このデータ型の列の作成時にコンシューマーによって指定された作成パラメーター。 たとえば、SQL データ型 `DECIMAL,` には、有効桁数と小数点以下桁数が必要です。 この場合、作成パラメーターには文字列 "precision,scale" を使用できます。 有効桁数が 10 で、小数点以下桁数が 2 である `DECIMAL` 列を作成するテキスト コマンドでは、`TYPE_NAME` 列の値は `DECIMAL()` になり、完全な型指定は `DECIMAL(10,2)` になります。<br /><br /> 作成パラメーターは、値をコンマで区切った一覧として表示されます。値は指定された順に表示され、かっこで囲まれません。 作成パラメーターが length、maximum length、precision、scale、seed、または increment の場合は、それぞれ "length"、"max length"、"precision"、"scale"、"seed"、および "increment" を使用します。 作成パラメーターがその他の値の場合は、作成パラメーターの記述に使用するテキストはプロバイダーによって決定されます。<br /><br /> データ型に作成パラメーターが必要な場合は、型名に "()" が含まれます。 これは、作成パラメーターを挿入する位置を示します。 型名に "()" が含まれない場合、作成パラメーターはかっこで囲まれ、データ型名に追加されます。|  
|`IS_NULLABLE`|`DBTYPE_BOOL`||データ型で NULL 値が許容されるかどうかを示すブール値。<br /><br /> `VARIANT_TRUE` は、データ型で NULL 値が許容されることを意味します。<br /><br /> `VARIANT_FALSE` データ型が null 許容ではないことを示します。<br /><br /> `NULL` は、データ型で NULL 値が許容されるかどうかが不明であることを意味します。|  
|`CASE_SENSITIVE`|`DBTYPE_BOOL`||データ型が文字型で、大文字と小文字が区別されるかどうかを示すブール値。<br /><br /> `VARIANT_TRUE` は、データ型が文字型であり、大文字と小文字が区別されることを意味します。<br /><br /> `VARIANT_FALSE` は、データ型が文字型ではなく、大文字と小文字が区別されないことを意味します。|  
|`SEARCHABLE`|`DBTYPE_UI4`||プロバイダーで `ICommandText` がサポートされている場合、検索でのデータ型の使用方法を示す整数。それ以外の場合は、`NULL` です。<br /><br /> この列は、次の値をとります。<br /><br /> -   `DB_UNSEARCHABLE` データ型を使用できないことを示します、`WHERE`句。<br />-   `DB_LIKE_ONLY` データ型を使用できることを示します、`WHERE`句でのみ、`LIKE`述語。<br />-   `DB_ALL_EXCEPT_LIKE` データ型を使用できることを示します、`WHERE`を除くすべての比較演算子を含む句`LIKE`します。<br />-   `DB_SEARCHABLE` データ型を使用できることを示します、`WHERE`任意の比較演算子を含む句。|  
|`UNSIGNED_ATTRIBUTE`|`DBTYPE_BOOL`||データ型が符号なしかどうかを示すブール値。<br /><br /> `VARIANT_TRUE` は、データ型が符号なしであることを意味します。<br /><br /> `VARIANT_FALSE` は、データ型が符号付きであることを意味します。<br /><br /> `NULL` は、この列がデータ型に適用されないことを意味します。|  
|`FIXED_PREC_SCALE`|`DBTYPE_BOOL`||データ型の有効桁数と小数点以下桁数が固定しているかどうかを示すブール値。<br /><br /> `VARIANT_TRUE` は、データ型の有効桁数と小数点以下桁数が固定していることを意味します。<br /><br /> `VARIANT_FALSE` は、データ型の有効桁数と小数点以下桁数が固定していないことを意味します。|  
|`AUTO_UNIQUE_VALUE`|`DBTYPE_BOOL`||データ型が自動増分かどうかを示すブール値。<br /><br /> `VARIANT_TRUE` は、この型の値が自動増分できることを意味します。<br /><br /> `VARIANT_FALSE` は、この型の値が自動増分できないことを意味します。<br /><br /> この値が `VARIANT_TRUE` である場合、この型の列が常に自動増分されるかどうかは、プロバイダーの `DBPROP_COL_AUTOINCREMENT` 列プロパティによって決まります。 `DBPROP_COL_AUTOINCREMENT` プロパティが読み取り/書き込み可能である場合、この型の列が自動増分されるかどうかは、`DBPROP_COL_AUTOINCREMENT` プロパティの設定によって決まります。 `DBPROP_COL_AUTOINCREMENT` が読み取り専用プロパティである場合は、この型のすべての列が自動増分されるか、どの列も自動増分されません。|  
|`LOCAL_TYPE_NAME`|`DBTYPE_WSTR`||`TYPE_NAME` のローカライズされたバージョン。 ローカライズされた名前がデータ プロバイダーによってサポートされていない場合は、`NULL` が返されます。|  
|`MINIMUM_SCALE`|`DBTYPE_I2`||型インジケーターが `DBTYPE_VARNUMERIC`、`DBTYPE_DECIMAL`、`DBTYPE_NUMERIC` のいずれかである場合、小数点以下で許容される最小桁数。 それ以外の場合、`NULL`します。|  
|`MAXIMUM_SCALE`|`DBTYPE_I2`||型インジケーターが `DBTYPE_VARNUMERIC`、`DBTYPE_DECIMAL`、または `DBTYPE_NUMERIC` のいずれかである場合、小数点以下で許容される最大桁数。それ以外の場合は、`U` です。|  
|`GUID`|`DBTYPE_GUID`||(将来使用する予定) 型がタイプ ライブラリに記述されている場合は、型の `GUID`。 それ以外の場合、`NULL`します。|  
|`TYPELIB`|`DBTYPE_WSTR`||(将来使用する予定) 型がタイプ ライブラリに記述されている場合は、型の記述を含んでいるタイプ ライブラリ。 それ以外の場合は、NULL。|  
|`VERSION`|`DBTYPE_WSTR`||(将来使用する予定) 型定義のバージョン。 プロバイダーは、型定義をバージョン管理できます。 プロバイダーによって、タイムスタンプや番号 (整数または浮動小数点数) などの異なるバージョン管理スキームが使用されます。 サポートされない場合は、`NULL` です。|  
|`IS_LONG`|`DBTYPE_BOOL`||データ型がバイナリ ラージ オブジェクト (BLOB) で、非常に長いデータを持つかどうかを示すブール値。<br /><br /> `VARIANT_TRUE` は、データ型が非常に長いデータを含んでいる `BLOB` であることを意味します。非常に長いデータの定義は、プロバイダーによって異なります。<br /><br /> `VARIANT_FALSE` は、データ型が非常に長いデータを含んでいない `BLOB` であるか、`BLOB` でないことを意味します。<br /><br /> この値によって、`DBCOLUMNFLAGS_ISLONG` の `GetColumnInfo` および `IColumnsInfo` の `GetParameterInfo` によって返される `ICommandWithParameters` フラグの設定が決まります。|  
|`BEST_MATCH`|`DBTYPE_BOOL`||最も一致するデータ型かどうかを示すブール値。<br /><br /> `VARIANT_TRUE` は、データ ストア内のすべてのデータ型と `DATA_TYPE` 列の値で示される OLE DB データ型の間で最も一致するデータ型であることを意味します。<br /><br /> `VARIANT_FALSE` は、最も一致するデータ型でないことを意味します。<br /><br /> `DATA_TYPE` 列が `BEST_MATCH` に設定されるのは、`VARIANT_TRUE` 列の値が同じである行のセットごとに 1 行のみです。|  
|`IS_FIXEDLENGTH`|`DBTYPE_BOOL`||列が固定長かどうかを示すブール値。<br /><br /> `VARIANT_TRUE` は、データ定義言語 (DDL) で作成されたこの型の列が固定長であることを意味します。<br /><br /> `VARIANT_FALSE` は、DDL で作成されたこの型の列が可変長であることを意味します。<br /><br /> フィールドが `NULL` の場合、プロバイダーがこのフィールドを固定長の列でマップするか可変長の列でマップするかは不明です。|  
  
 行セットは、`DATA_TYPE` を基準に並べ替えることができます。  
  
## <a name="restriction-columns"></a>制限の列  
 `DBSCHEMA_PROVIDER_TYPES`行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|`DATA_TYPE`|`DBTYPE_UI2`||  
|`BEST_MATCH`|`DBTYPE_BOOL`||  
  
## <a name="see-also"></a>参照  
 [OLE DB Schema 行セット](ole-db-schema-rowsets.md)  
  
  
