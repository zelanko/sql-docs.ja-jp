---
title: "DBSCHEMA_PROVIDER_TYPES 行セット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DBSCHEMA_PROVIDER_TYPES
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DBSCHEMA_PROVIDER_TYPES rowset
ms.assetid: 255e01ba-53a9-478d-9b86-45faba76710e
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c6ab9f234c182e7d3e1cc6040799154babe87108
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="dbschemaprovidertypes-rowset"></a>DBSCHEMA_PROVIDER_TYPES 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]データ プロバイダーでサポートされている (基本) データ型を識別します。  
  
## <a name="rowset-columns"></a>行セットの列  
 **DBSCHEMA_PROVIDER_TYPES**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|Description|  
|-----------------|--------------------|-----------------|  
|**TYPE_NAME**|**DBTYPE_WSTR**|プロバイダー固有のデータ型名。|  
|**DATA_TYPE**|**DBTYPE_UI2**|データ型のインジケーター。|  
|**COLUMN_SIZE**|**DBTYPE_UI4**|プロバイダーによってこの型に対して定義された最大値または長さのいずれかを表す非数値の列またはパラメーターの長さ。 文字データの場合、これは最大値または定義済みの長さを文字数で表したものです。 DateTime 型の場合、これは文字列の長さです (秒部分に許容される最大有効桁数を想定)。<br /><br /> データ型が Numeric の場合、これはデータ型の有効桁数の上限値です。|  
|**LITERAL_PREFIX**|**DBTYPE_WSTR**|テキスト コマンドでこの型のリテラルのプレフィックスとして使用する文字または文字列。|  
|**LITERAL_SUFFIX**|**DBTYPE_WSTR**|テキスト コマンドでこの型のリテラルのサフィックスとして使用する文字または文字列。|  
|**CREATE_PARAMS**|**DBTYPE_WSTR**|このデータ型の列の作成時にコンシューマーによって指定された作成パラメーター。 SQL データ型など、 **10 進数、** precision と scale が必要です。 この場合、作成パラメーターには文字列 "precision,scale" を使用できます。 作成するテキスト コマンドで、 **DECIMAL** 10 の有効桁数と小数点以下桁数は 2 の値を列、 **TYPE_NAME**列があります**DECIMAL()**と完全な型仕様がなります**DECIMAL(10,2)**です。<br /><br /> 作成パラメーターは、値をコンマで区切った一覧として表示されます。値は指定された順に表示され、かっこで囲まれません。 作成パラメーターが length、maximum length、precision、scale、seed、または increment の場合は、それぞれ "length"、"max length"、"precision"、"scale"、"seed"、および "increment" を使用します。 作成パラメーターがその他の値の場合は、作成パラメーターの記述に使用するテキストはプロバイダーによって決定されます。<br /><br /> データ型に作成パラメーターが必要な場合は、型名に "()" が含まれます。 これは、作成パラメーターを挿入する位置を示します。 型名に "()" が含まれない場合、作成パラメーターはかっこで囲まれ、データ型名に追加されます。|  
|**によって IS_NULLABLE**|**DBTYPE_BOOL**|データ型で NULL 値が許容されるかどうかを示すブール値。<br /><br /> **VARIANT_TRUE**データ型が null 許容であることを示します。<br /><br /> **VARIANT_FALSE**データ型が null 許容でないことを示します。<br /><br /> **NULL**— ことかが不明のデータ型が null 許容かどうかを示します。|  
|**CASE_SENSITIVE**|**DBTYPE_BOOL**|データ型が文字型で、大文字と小文字が区別されるかどうかを示すブール値。<br /><br /> **VARIANT_TRUE**データ型が文字型であり、大文字小文字を区別ことを示します。<br /><br /> **VARIANT_FALSE**データ型が文字型ではないか、小文字は区別されないことを示します。|  
|**検索可能**|**DBTYPE_UI4**|データ型できますで使用する方法の検索プロバイダーをサポートしている場合を示す整数**ICommandText**、それ以外の**NULL**です。 この列は、次の値をとります。<br /><br /> **DB_UNSEARCHABLE**でデータ型を使用できないことを示す、**場所**句。<br /><br /> **DB_LIKE_ONLY**でデータ型を使用できることを示す、**場所**句でのみ、**と同様に**述語。<br /><br /> **DB_ALL_EXCEPT_LIKE**でデータ型を使用できることを示す、**場所**を除くすべての比較演算子を含む句**と同様に**です。<br /><br /> **DB_SEARCHABLE**でデータ型を使用できることを示す、**場所**任意の比較演算子を含む句。|  
|**UNSIGNED_ATTRIBUTE**|**DBTYPE_BOOL**|データ型が符号なしかどうかを示すブール値。<br /><br /> **VARIANT_TRUE**データ型が符号付きであることを示します。<br /><br /> **VARIANT_FALSE**データ型が署名されていることを示します。<br /><br /> **NULL**データ型に適用ではないことを示します。|  
|**FIXED_PREC_SCALE**|**DBTYPE_BOOL**|データ型の有効桁数と小数点以下桁数が固定しているかどうかを示すブール値。<br /><br /> **VARIANT_TRUE**固定有効桁数と小数点以下桁数のデータ型があることを示します。<br /><br /> **VARIANT_FALSE**固定有効桁数と小数点以下桁数に、データ型がないことを示します。|  
|**AUTO_UNIQUE_VALUE**|**DBTYPE_BOOL**|データ型が自動増分かどうかを示すブール値。<br /><br /> **VARIANT_TRUE**この型の値が自動増分できることを示します。<br /><br /> **VARIANT_FALSE**この型の値が自動増分できないことを示します。<br /><br /> この値が場合**VARIANT_TRUE**この型の列は、常に、プロバイダーの異なります自動増分されるかどうか、 **DBPROP_COL_AUTOINCREMENT**列のプロパティです。 場合、 **DBPROP_COL_AUTOINCREMENT**プロパティは、読み取り/書き込み、この型の列は、の設定に依存する自動増分されるかどうか、 **DBPROP_COL_AUTOINCREMENT**プロパティです。 場合**DBPROP_COL_AUTOINCREMENT**読み取り専用のプロパティは、いずれかまたはすべてのこの型の列が自動インクリメントします。|  
|**LOCAL_TYPE_NAME**|**DBTYPE_WSTR**|ローカライズ版**TYPE_NAME**です。 **NULL**かどうか、ローカライズされた名前は、データ プロバイダーではサポートされませんが返されます。|  
|**MINIMUM_SCALE**|**DBTYPE_I2**|型インジケーターが場合**DBTYPE_VARNUMERIC**、 **DBTYPE_DECIMAL**、または**DBTYPE_NUMERIC**小数点の右側に許容される最小桁数。 それ以外の場合、 **NULL**です。|  
|**MAXIMUM_SCALE**|**DBTYPE_I2**|型インジケーターがある場合は、小数点の右側に許可する最大桁数**DBTYPE_VARNUMERIC**、 **DBTYPE_DECIMAL**、または**DBTYPE_NUMERIC**以外の場合、N**U**LL です。|  
|**GUID**|**DBTYPE_GUID 型**|(将来使用するためのもの)**GUID**型がタイプ ライブラリに記述されている場合は、型のです。 それ以外の場合、 **NULL**です。|  
|**タイプ ライブラリ**|**DBTYPE_WSTR**|(将来使用する予定) 型がタイプ ライブラリに記述されている場合は、型の記述を含んでいるタイプ ライブラリ。 それ以外の場合は、NULL。|  
|**VERSION**|**DBTYPE_WSTR**|(将来使用する予定) 型定義のバージョン。 プロバイダーは、型定義をバージョン管理できます。 プロバイダーによって、タイムスタンプや番号 (整数または浮動小数点数) などの異なるバージョン管理スキームが使用されます。 **NULL**サポートされていない場合。|  
|**IS_LONG**|**DBTYPE_BOOL**|データ型がバイナリ ラージ オブジェクト (BLOB) で、非常に長いデータを持つかどうかを示すブール値。<br /><br /> **VARIANT_TRUE**データの種類があることを示します、 **BLOB**非常に長いデータを格納している以外の非常に長いデータの定義は、プロバイダーに固有です。<br /><br /> **VARIANT_FALSE**データの種類があることを示します、 **BLOB**を非常に長いデータを含まないかが、 **BLOB**です。<br /><br /> この値の設定を決定する、 **DBCOLUMNFLAGS_ISLONG**によって返されたフラグ**GetColumnInfo**で**IColumnsInfo**と**GetParameterInfo**で**ICommandWithParameters**です。|  
|**BEST_MATCH**|**DBTYPE_BOOL**|最も一致するデータ型かどうかを示すブール値。<br /><br /> **VARIANT_TRUE**データ型がデータ ストア内のすべてのデータ型との値によって示される OLE DB データ型間の最適な一致であることを示します、 **DATA_TYPE**列です。<br /><br /> **VARIANT_FALSE**データ型が最適な一致でないことを示します。<br /><br /> ある行のセットごとの値、 **DATA_TYPE**列は、同じ、 **、BEST_MATCH**に列が設定されている**VARIANT_TRUE** 1 行のみにします。|  
|**IS_FIXEDLENGTH**|**DBTYPE_BOOL**|列が固定長かどうかを示すブール値。<br /><br /> **VARIANT_TRUE**固定長データ定義言語 (DDL) によって作成されたこの型の列があることを意味します。<br /><br /> **VARIANT_FALSE** DDL で作成されたこの型の列が可変長のことを示します。<br /><br /> フィールドがある場合**NULL**プロバイダーが固定長または可変長列を持つこのフィールドをマップするかどうかが不明です。|  
  
 行セットが並べ替えられて**DATA_TYPE**です。  
  
## <a name="restriction-columns"></a>制限の列  
 **DBSCHEMA_PROVIDER_TYPES**行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|  
|-----------------|--------------------|  
|**DATA_TYPE**|**DBTYPE_UI2**|  
|**BEST_MATCH**|**DBTYPE_BOOL**|  
  
## <a name="see-also"></a>参照  
 [OLE DB Schema 行セット](../../../analysis-services/schema-rowsets/ole-db/ole-db-schema-rowsets.md)  
  
  
