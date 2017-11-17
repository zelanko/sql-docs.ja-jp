---
title: "ALTER シーケンス (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/08/2015
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_SEQUENCE_TSQL
- ALTER SEQUENCE
dev_langs:
- TSQL
helpviewer_keywords:
- sequence number object, altering
- ALTER SEQUENCE statement
ms.assetid: decc0760-029e-4baf-96c9-4a64073df1c2
caps.latest.revision: 24
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: de7fd182be8fd79574c098a499a40a34d38aaf21
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="alter-sequence-transact-sql"></a>ALTER シーケンス (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  既存のシーケンス オブジェクトの引数を変更します。 シーケンスの作成時の**キャッシュ**オプション、順序を変更するには、キャッシュを再作成します。  
  
 シーケンス オブジェクトを使用して作成される、 [CREATE SEQUENCE](../../t-sql/statements/create-sequence-transact-sql.md)ステートメントです。 シーケンスは整数値で、整数を返す任意のデータ型を指定できます。 このデータ型は、ALTER SEQUENCE ステートメントでは変更できません。 データ型を変更するには、シーケンス オブジェクトを削除して再作成します。  
  
 シーケンスはユーザー定義のスキーマ バインド オブジェクトで、仕様に従って数値のシーケンスを生成します。 NEXT VALUE FOR 関数を呼び出すことにより、シーケンスから新しい値が生成されます。 一度に複数のシーケンス番号を取得するには、 **sp_sequence_get_range** を使用します。 詳細および両方の作成のシーケンスを使用するシナリオ**sp_sequence_get_range**、および、NEXT VALUE FOR 関数を参照してください[シーケンス番号](../../relational-databases/sequence-numbers/sequence-numbers.md)です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
ALTER SEQUENCE [schema_name. ] sequence_name  
    [ RESTART [ WITH <constant> ] ]  
    [ INCREMENT BY <constant> ]  
    [ { MINVALUE <constant> } | { NO MINVALUE } ]  
    [ { MAXVALUE <constant> } | { NO MAXVALUE } ]  
    [ CYCLE | { NO CYCLE } ]  
    [ { CACHE [ <constant> ] } | { NO CACHE } ]  
    [ ; ]  
```  
  
## <a name="arguments"></a>引数  
 *sequence_name*  
 データベースに認識されるシーケンスの一意な名前を指定します。 種類は**sysname**です。  
  
 再起動 [WITH\<定数 >]  
 シーケンス オブジェクトによって返される次の値です。 RESTART WITH 値を指定する場合は、シーケンス オブジェクトの最小値以上および最大値以下の整数にする必要があります。 WITH 値を省略した場合は、元の CREATE SEQUENCE オプションに基づいてシーケンスの番号付けが再開されます。  
  
 インクリメントで\<定数 >  
 NEXT VALUE FOR 関数を呼び出すたびに必要なシーケンス オブジェクトの基準値を増分 (負の場合は減少) させるのに使用される値です。 増分値が負の値の場合はシーケンス オブジェクトは降順で、それ以外の場合は昇順です。 増分値を 0 にすることはできません。  
  
 [MINVALUE\<定数 > |ありません MINVALUE]  
 シーケンスのオブジェクトの境界を指定します。 NO MINVALUE を指定すると、シーケンスのデータ型の最小値が使用されます。  
  
 [MAXVALUE\<定数 > |ありません MAXVALUE  
 シーケンスのオブジェクトの境界を指定します。 NO MAXVALUE を指定すると、シーケンスのデータ型の最大値が使用されます。  
  
 [ CYCLE | NO CYCLE ]  
 このプロパティは、最小値または最大値を超過した場合に、シーケンス オブジェクトを最小値 (降順シーケンス オブジェクトの場合は最大値) から再開するか、例外をスローするかを指定します。  
  
> [!NOTE]  
>  循環後の次の値は最小値または最大値で、シーケンスの START VALUE ではありません。  
  
 [キャッシュ [\<定数 >] |キャッシュなし]  
 生成された値をシステム テーブルに保存するのに必要な IO の数を最小限に抑えることで、シーケンス オブジェクトを使用するアプリケーションのパフォーマンスが向上します。  
  
 キャッシュの動作に関する詳細については、次を参照してください。[シーケンスの作成 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-sequence-transact-sql.md).  
  
## <a name="remarks"></a>解説  
 シーケンスの作成方法と、シーケンスのキャッシュを管理する方法については、次を参照してください。[シーケンスの作成 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-sequence-transact-sql.md).  
  
 昇順のシーケンスの MINVALUE と降順のシーケンスの MAXVALUE は、シーケンスの START WITH 値を許可しない値に変更することはできません。 昇順のシーケンスの MINVALUE を START WITH 値より大きい数に変更する、または降順のシーケンスの MAXVALUE を START WITH 値より小さい数に変更するには、RESTART WITH 引数を含めて、最小値と最大値の範囲内にある目的の位置からシーケンスを再開します。  
  
## <a name="metadata"></a>メタデータ  
 シーケンスの詳細については、「 [sys.sequences](../../relational-databases/system-catalog-views/sys-sequences-transact-sql.md)」を参照してください。  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>Permissions  
 必要があります**ALTER** 、シーケンスに対する権限または**ALTER**スキーマに対する権限。 付与する**ALTER**権限を使用して、シーケンスに対する**ALTER ON OBJECT**次の形式で。  
  
```  
GRANT ALTER ON OBJECT::Test.TinySeq TO [AdventureWorks\Larry]  
```  
  
 使用して、シーケンス オブジェクトの所有権を転送することができます、 **ALTER AUTHORIZATION**ステートメントです。  
  
### <a name="audit"></a>監査  
 監査する**ALTER SEQUENCE**、モニター、 **SCHEMA_OBJECT_CHANGE_GROUP**です。  
  
## <a name="examples"></a>使用例  
 両方のシーケンスを作成および使用の例については、 **NEXT VALUE FOR**を参照してください、シーケンス番号を生成する関数[シーケンス番号](../../relational-databases/sequence-numbers/sequence-numbers.md)です。  
  
### <a name="a-altering-a-sequence"></a>A. シーケンスを変更する  
 次の例は、テストをという名前のスキーマと TestSeq を使用してという名前のシーケンスを作成、 **int** 0 ~ 255 の範囲を持つ、データ型。 シーケンスは 125 で始まり、数値が生成されるたびに 25 ずつ増加します。 シーケンスは循環するように設定されているため、値が最大値の 200 を超えると、最小値の 100 で再開します。  
  
```  
CREATE SCHEMA Test ;  
GO  
  
CREATE SEQUENCE Test.TestSeq  
    AS int   
    START WITH 125  
    INCREMENT BY 25  
    MINVALUE 100  
    MAXVALUE 200  
    CYCLE  
    CACHE 3  
;  
GO  
```  
  
 次の例では、0 ～ 255 の範囲を指定して TestSeq シーケンスを変更します。 シーケンスの番号が 100 から再開し、数値が生成されるたびに 50 ずつ増加します。  
  
```  
ALTER SEQUENCE Test. TestSeq  
    RESTART WITH 100  
    INCREMENT BY 50  
    MINVALUE 50  
    MAXVALUE 200  
    NO CYCLE  
    NO CACHE  
;  
GO  
```  
  
 シーケンスが循環しないため、 **NEXT VALUE FOR**関数は、エラー発生 200 を超える場合。  
  
### <a name="b-restarting-a-sequence"></a>B. シーケンスを再開する  
 次の例では、CountBy1 をという名前のシーケンスを作成します。 このシーケンスは既定値を使用します。  
  
```  
CREATE SEQUENCE Test.CountBy1 ;  
```  
  
 シーケンスの値を生成するには、所有者は次のステートメントを実行します。  
  
```  
SELECT NEXT VALUE FOR Test.CountBy1  
```  
  
 -9,223,372,036,854,775,808 の返される値は、最小値、 **bigint**データ型。 彼は、1 から開始するシーケンスが示さない所有者が実現、 **START WITH**句、シーケンスの作成時にします。 このエラーを修正するには、所有者は次のステートメントを実行します。  
  
```  
ALTER SEQUENCE Test.CountBy1 RESTART WITH 1 ;  
```  
  
 その後、次のステートメントを再度実行して、シーケンス番号を生成します。  
  
```  
SELECT NEXT VALUE FOR Test.CountBy1;  
```  
  
 今度は、想定どおりに番号が 1 になります。  
  
 CountBy1 シーケンスは、9,223,372,036,854,775,807 の数を生成すると操作を中止するために、既定値の NO CYCLE を使用して作成されました。 この後にシーケンス オブジェクトを呼び出すと、エラー 11728 が返されます。 次のステートメントは、シーケンス オブジェクトが循環するように変更し、キャッシュを 20 に設定します。  
  
```  
ALTER SEQUENCE Test.CountBy1  
    CYCLE  
    CACHE 20 ;  
  
```  
  
 これにより、シーケンス オブジェクトは 9,223,372,036,854,775,807 に達すると循環し、次の数値はデータ型の最小値である -9,223,372,036,854,775,808 になります。  
  
 いることに気付きました、所有者、 **bigint**を使用するたびに 8 バイトを使用するデータ型。 **Int** 4 バイトを使用するデータ型で十分です。 ただし、シーケンス オブジェクトのデータ型は変更できません。 変更する、 **int**データ型、所有者必要がありますシーケンス オブジェクトを削除して、正しいデータ型を持つオブジェクトを再作成します。  
  
## <a name="see-also"></a>参照  
 [SEQUENCE &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-sequence-transact-sql.md)   
 [DROP SEQUENCE &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-sequence-transact-sql.md)   
 [次の値を & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/next-value-for-transact-sql.md)   
 [シーケンス番号](../../relational-databases/sequence-numbers/sequence-numbers.md)   
 [sp_sequence_get_range & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql.md)  
  
  

