---
title: sp_sequence_get_range (TRANSACT-SQL) |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 08/08/2015
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_sequence_get_range
- sp_sequence_get_range_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sequence number object, sp_sequence_get_range procedure
- sp_sequence_get_range
ms.assetid: 8ca6b0c6-8d9c-4eee-b02f-51ddffab4492
caps.latest.revision: 19
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 0ffae66700ffefe60602ba1e296bae6d903a3baa
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39549162"
---
# <a name="spsequencegetrange-transact-sql"></a>sp_sequence_get_range (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-asdw-xxx-md.md)]

  シーケンス オブジェクトからシーケンス値の範囲を返します。 シーケンス オブジェクトでは、要求された値の数を生成して発行し、その範囲に関連するメタデータをアプリケーションに提供します。  
  
 シーケンス番号の詳細については、次を参照してください。[シーケンス番号](../../relational-databases/sequence-numbers/sequence-numbers.md)します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_sequence_get_range [ @sequence_name = ] N'<sequence>'   
     , [ @range_size = ] range_size  
     , [ @range_first_value = ] range_first_value OUTPUT   
    [, [ @range_last_value = ] range_last_value OUTPUT ]  
    [, [ @range_cycle_count = ] range_cycle_count OUTPUT ]  
    [, [ @sequence_increment = ] sequence_increment OUTPUT ]  
    [, [ @sequence_min_value = ] sequence_min_value OUTPUT ]  
    [, [ @sequence_max_value = ] sequence_max_value OUTPUT ]  
    [ ; ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@sequence_name** =] **N**'*シーケンス*'  
 シーケンス オブジェクトの名前。 スキーマは省略可能です。 *sequence_name*は**nvarchar (776)** します。  
  
 [ **@range_size** = ] *range_size*  
 シーケンスからフェッチする値の数。 **@range_size** **bigint**します。  
  
 [ **@range_first_value** = ] *range_first_value*  
 出力パラメーター。要求された範囲の計算に使用するシーケンス オブジェクトの最初 (最小または最大) の値を返します。 **@range_first_value** **sql_variant**との要求で使用されているシーケンス オブジェクトの同じ基本型。  
  
 [ **@range_last_value** =] *range_last_value*  
 省略可能な出力パラメーター。要求された範囲の最後の値を返します。 **@range_last_value** **sql_variant**との要求で使用されているシーケンス オブジェクトの同じ基本型。  
  
 [ **@range_cycle_count** =] range_cycle_count  
 省略可能な出力パラメーター。要求された範囲を返すためにシーケンス オブジェクトを循環した回数を返します。 **@range_cycle_count** **int**します。  
  
 [ **@sequence_increment** =] *sequence_increment*  
 省略可能な出力パラメーター。要求された範囲の計算に使用するシーケンス オブジェクトの増分を返します。 **@sequence_increment** **sql_variant**との要求で使用されているシーケンス オブジェクトの同じ基本型。  
  
 [ **@sequence_min_value** = ] *sequence_min_value*  
 省略可能な出力パラメーター。シーケンス オブジェクトの最小値を返します。 **@sequence_min_value** **sql_variant**との要求で使用されているシーケンス オブジェクトの同じ基本型。  
  
 [ **@sequence_max_value** = ] *sequence_max_value*  
 省略可能な出力パラメーター。シーケンス オブジェクトの最大値を返します。 **@sequence_max_value** **sql_variant**との要求で使用されているシーケンス オブジェクトの同じ基本型。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>コメント  
 sys sp_sequence_get_rangeis します。 スキーマ sys.sp_sequence_get_range として参照することができます。  
  
### <a name="cycling-sequences"></a>循環するシーケンス  
 必要な場合は、要求された範囲を返すために、シーケンス オブジェクトを適切な回数循環します。 循環した回数は、`@range_cycle_count` パラメーターを通じて、呼び出し元に返されます。  
  
> [!NOTE]  
>  循環する場合、シーケンス オブジェクトは、シーケンス オブジェクトの開始値ではなく、昇順のシーケンスの最小値および降順のシーケンスの最大値から開始されます。  
  
### <a name="non-cycling-sequences"></a>循環しないシーケンス  
 要求された範囲の値の数がシーケンス オブジェクト内の残りの利用可能な値を超える場合、要求された範囲がシーケンス オブジェクトから推論されることはなく、次のエラー 11732 が返されます。  
  
 `The requested range for sequence object '%.*ls' exceeds the maximum or minimum limit. Retry with a smaller range.`  
  
## <a name="permissions"></a>アクセス許可  
 シーケンス オブジェクトまたはシーケンス オブジェクトのスキーマに対する UPDATE 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、Test.RangeSeq をという名前のシーケンス オブジェクトを使用します。 Test.RangeSeq シーケンスを作成するのにには、次のステートメントを使用します。  
  
```  
CREATE SCHEMA Test ;  
GO  
  
CREATE SEQUENCE Test.RangeSeq  
    AS int   
    START WITH 1  
    INCREMENT BY 1  
    MINVALUE 1  
    MAXVALUE 25  
    CYCLE  
    CACHE 10  
;  
```  
  
### <a name="a-retrieving-a-range-of-sequence-values"></a>A. シーケンス値の範囲を取得する  
 次のステートメントでは、Test.RangeSeq シーケンス オブジェクトから 4 つのシーケンス番号を取得し、ユーザーに最初の番号を返します。  
  
```  
DECLARE @range_first_value sql_variant ,   
        @range_first_value_output sql_variant ;  
  
EXEC sp_sequence_get_range  
@sequence_name = N'Test.RangeSeq'  
, @range_size = 4  
, @range_first_value = @range_first_value_output OUTPUT ;  
  
SELECT @range_first_value_output AS FirstNumber ;  
  
```  
  
### <a name="b-returning-all-output-parameters"></a>B. すべての出力パラメーターを返す  
 次の例では、sp_sequence_get_range プロシージャからすべての出力値を返します。  
  
```  
DECLARE    
  @FirstSeqNum sql_variant  
, @LastSeqNum sql_variant  
, @CycleCount int  
, @SeqIncr sql_variant  
, @SeqMinVal sql_variant  
, @SeqMaxVal sql_variant ;  
  
EXEC sys.sp_sequence_get_range  
@sequence_name = N'Test.RangeSeq'  
, @range_size = 5  
, @range_first_value = @FirstSeqNum OUTPUT   
, @range_last_value = @LastSeqNum OUTPUT   
, @range_cycle_count = @CycleCount OUTPUT  
, @sequence_increment = @SeqIncr OUTPUT  
, @sequence_min_value = @SeqMinVal OUTPUT  
, @sequence_max_value = @SeqMaxVal OUTPUT ;  
  
-- The following statement returns the output values  
SELECT  
  @FirstSeqNum AS FirstVal  
, @LastSeqNum AS LastVal  
, @CycleCount AS CycleCount  
, @SeqIncr AS SeqIncrement  
, @SeqMinVal AS MinSeq  
, @SeqMaxVal AS MaxSeq ;  
  
```  
  
 引数 `@range_size` を 75 などの大きな数に変更すると、シーケンス オブジェクトを循環します。 シーケンス オブジェクトを循環したかどうか、およびその回数を調べるには、引数 `@range_cycle_count` をチェックします。  
  
### <a name="c-example-using-adonet"></a>C. ADO.NET を使用する例  
 次の例では、ADO.NET を使用して、Test.RangeSeq から範囲を取得します。  
  
```  
SqlCommand cmd = new SqlCommand();  
cmd.Connection = conn;  
cmd.CommandType = CommandType.StoredProcedure;  
cmd.CommandText = "sys.sp_sequence_get_range";  
cmd.Parameters.AddWithValue("@sequence_name", "Test.RangeSeq");  
cmd.Parameters.AddWithValue("@range_size", 10);  
  
// Specify an output parameter to retreive the first value of the generated range.  
SqlParameter firstValueInRange = new SqlParameter("@range_first_value", SqlDbType.Variant);  
firstValueInRange.Direction = ParameterDirection.Output;  
cmd.Parameters.Add(firstValueInRange);  
  
conn.Open();  
cmd.ExecuteNonQuery();  
  
// Output the first value of the generated range.  
Console.WriteLine(firstValueInRange.Value);  
  
```  
  
## <a name="see-also"></a>参照  
 [CREATE SEQUENCE &#40;Transact-SQL&#41;](../../t-sql/statements/create-sequence-transact-sql.md)   
 [ALTER SEQUENCE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-sequence-transact-sql.md)   
 [DROP SEQUENCE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-sequence-transact-sql.md)   
 [NEXT VALUE FOR &#40;Transact-SQL&#41;](../../t-sql/functions/next-value-for-transact-sql.md)   
 [シーケンス番号](../../relational-databases/sequence-numbers/sequence-numbers.md)  
  
  
