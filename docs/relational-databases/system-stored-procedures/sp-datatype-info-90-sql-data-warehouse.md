---
description: sp_datatype_info_90 (Azure Synapse Analytics)
title: sp_datatype_info_90 (Azure Synapse Analytics)
ms.custom: ''
ms.date: 03/13/2017
ms.service: sql-data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 1d043964-dc6e-4c3e-ab61-bc444d5e25ae
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest'
ms.openlocfilehash: 8a859571ef9f4682c4c8556038247dc21d47eb50
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/14/2020
ms.locfileid: "97474613"
---
# <a name="sp_datatype_info_90-azure-synapse-analytics"></a>sp_datatype_info_90 (Azure Synapse Analytics)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  現在の環境でサポートされているデータ型に関する情報を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則 (Transact-SQL)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```syntaxsql  
-- Syntax for Azure Synapse Analytics and Parallel Data Warehouse  
  
sp_datatype_info_90 [ [ @data_type = ] data_type ]   
     [ , [ @ODBCVer = ] odbc_version ]   
```  

[!INCLUDE[synapse-analytics-od-unsupported-syntax](../../includes/synapse-analytics-od-unsupported-syntax.md)]
  
## <a name="arguments"></a>引数  
`[ @data_type = ] data_type` 指定されたデータ型のコード番号です。 すべてのデータ型の一覧を表示するには、このパラメーターを省略します。 *data_type* は **int**,、既定値は0です。  
  
`[ @ODBCVer = ] odbc_version` 使用する ODBC のバージョンを示します。 *odbc_version* は **tinyint**,、既定値は2です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 なし  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|TYPE_NAME|**sysname**|DBMS に依存するデータ型です。|  
|DATA_TYPE|**smallint**|このデータ型のすべての列がマップされる ODBC 型のコードです。|  
|PRECISION|**int**|データ ソースでのデータ型の最大有効桁数です。 有効桁数が適用されないデータ型に対しては NULL が返されます。 PRECISION 列の戻り値は 10 進表記です。|  
|LITERAL_PREFIX|**varchar (** 32 **)**|定数の前に使用された文字。 たとえば、文字型には単一引用符 (**'**)、バイナリには0x を使用します。|  
|LITERAL_SUFFIX|**varchar (** 32 **)**|定数を終了するために使用される1つ以上の文字。 たとえば、文字型には単一引用符 (**'**)、バイナリには引用符は使用しません。|  
|CREATE_PARAMS|**varchar (** 32 **)**|このデータ型の作成パラメーターの説明です。 たとえば、 **decimal** は "precision, scale"、 **float** は NULL、 **varchar** は "max_length" です。|  
|NULLABLE|**smallint**|Null 値の許容属性を指定します。<br /><br /> 1 = null 値を許容します。<br /><br /> 0 = null 値は許可されません。|  
|CASE_SENSITIVE|**smallint**|大文字と小文字を区別するかどうかを示します。<br /><br /> 1 = この型のすべての列では、大文字と小文字を区別します (照合の場合)。<br /><br /> 0 = この型のすべての列では、大文字と小文字が区別されません。|  
|検索可能|**smallint**|列の型の検索機能を示します。<br /><br /> 1 = 検索できません。<br /><br /> 2 = LIKE で検索できます。<br /><br /> 3 = WHERE で検索できます。<br /><br /> 4 = WHERE または LIKE で検索できます。|  
|UNSIGNED_ATTRIBUTE|**smallint**|データ型の符号を示します。<br /><br /> 1 = 符号なしのデータ型。<br /><br /> 0 = 符号付きデータ型。|  
|MONEY|**smallint**|**Money** データ型を指定します。<br /><br /> 1 = **money** データ型。<br /><br /> 0 = **money** データ型ではありません。|  
|AUTO_INCREMENT|**smallint**|自動増分を指定します。<br /><br /> 1 = 自動増分。<br /><br /> 0 = Not 自動増分。<br /><br /> NULL = この属性は適用できません。<br /><br /> アプリケーションは、この属性を持つ列に値を挿入することはできますが、その列の値を更新することはできません。 **Bit** データ型を除き、AUTO_INCREMENT は、真数データ型および概数データ型のカテゴリに属するデータ型に対してのみ有効です。|  
|LOCAL_TYPE_NAME|**sysname**|データソースに依存するデータ型のローカライズされたバージョン。 たとえば、DECIMAL はフランス語で DECIMALE になります。 ローカライズされた名前がそのデータ ソースによってサポートされない場合は NULL が返されます。|  
|MINIMUM_SCALE|**smallint**|データ ソースでのデータ型の最小小数点以下桁数です。 データ型の小数点以下桁数が固定されている場合は、MINIMUM_SCALE 列および MAXIMUM_SCALE 列の両方にこの値が入ります。 小数点以下桁数が適用されない場合は NULL が返されます。|  
|MAXIMUM_SCALE|**smallint**|データ ソースでのデータ型の最大小数点以下桁数です。 最大小数点以下桁数がデータソースで個別に定義されておらず、最大有効桁数と同じになるように定義されている場合、この列には PRECISION 列と同じ値が格納されます。|  
|SQL_DATA_TYPE|**smallint**|記述子の TYPE フィールドでの SQL データ型の値です。 この列は、 **datetime** および ANSI **interval** データ型を除き、DATA_TYPE 列と同じです。 このフィールドは常に値を返します。|  
|SQL_DATETIME_SUB|**smallint**|SQL_DATA_TYPE の値が SQL_DATETIME または SQL_INTERVAL の場合は、 **datetime** または ANSI **interval** サブコード。 **Datetime** および ANSI **interval** 以外のデータ型の場合、このフィールドは NULL になります。|  
|NUM_PREC_RADIX|**int**|列が保持できる最大数を計算するビット数または桁数。 データ型が概数型である場合、この列に含まれる値は 2 で、複数のビットを示します。 真数型の場合、この列には10進数を示す値10が含まれます。 その他の場合、この列は NULL になります。 アプリケーションは、基数と精度を組み合わせて、その列が保持できる最大数を計算できます。|  
|INTERVAL_PRECISION|**smallint**|*Data_type* が **interval** の場合の間隔の先頭の有効桁数の値。それ以外の場合は NULL。|  
|USERTYPE|**smallint**|systypes テーブルの **usertype** 値。|  
  
## <a name="remarks"></a>解説  
 sp_datatype_info は、ODBC の SQLGetTypeInfo に相当します。 結果は、まず DATA_TYPE の順序で、次にデータ型が対応する ODBC SQL データ型にどれだけ正確にマップされているのかに基づいて返されます。  
  
## <a name="permissions"></a>アクセス許可  
 public ロールのメンバーシップが必要です。  
  
## <a name="examples-sssdwfull-and-sspdw"></a>例: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例では、 *data_type* の値を指定して、 **sysname** および **nvarchar** データ型の情報を取得 `-9` します。  
  
```sql  
USE master;  
GO  
EXEC sp_datatype_info_90 -9;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [Azure Synapse Analytics ストアドプロシージャ](../../relational-databases/system-stored-procedures/sql-data-warehouse-stored-procedures.md)   
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
  
  

