---
title: sp_addtype (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_addtype
- sp_addtype_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addtype
ms.assetid: ed72cd8e-5ff7-4084-8458-2d8ed279d817
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 764241bcd61b407b46e87c796c8a02997d9ff9ad
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43023859"
---
# <a name="spaddtype-transact-sql"></a>sp_addtype (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  別名データ型を作成します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 使用[CREATE TYPE](../../t-sql/statements/create-type-transact-sql.md)代わりにします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_addtype [ @typename = ] type,   
    [ @phystype = ] system_data_type   
    [ , [ @nulltype = ] 'null_type' ] ;  
```  
  
## <a name="arguments"></a>引数  
 [  **@typename=** ]*型*  
 別名データ型の名前を指定します。 データ型の名前がの規則に従う必要がありますエイリアス[識別子](../../relational-databases/databases/database-identifiers.md)し、各データベース内で一意である必要があります。 *型*は**sysname**、既定値はありません。  
  
 [  **@phystype=**] *system_data_type*  
 物理または[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]別名データ型の基になるデータ型を指定します *。system_data_type*は**sysname**, で、既定値はありませんはこれらの値のいずれかを指定します。  
  
||||  
|-|-|-|  
|**bigint**|**binary(n)**|**bit**|  
|**char(n)**|**datetime**|**decimal**|  
|**float**|**image**|**int**|  
|**money**|**nchar(n)**|**ntext**|  
|**numeric**|**nvarchar(n)**|**real**|  
|**smalldatetime**|**smallint**|**smallmoney**|  
|**sql_variant**|**text**|**tinyint**|  
|**uniqueidentifier**|**varbinary(n)**|**varchar(n)**|  
  
 空白または区切り記号を含むパラメーターはすべて、引用符で囲む必要があります。 使用可能なデータの種類の詳細については、次を参照してください。[データ型&#40;TRANSACT-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)します。  
  
 *n*  
 選択したデータ型の長さを示す、負以外の整数を指定します。  
  
 *P*  
 小数点の左側と右側に格納できる 10 進数の最大合計桁数を示す、負以外の整数を指定します。 詳細については、次を参照してください[decimal and numeric &#40;Transact-SQL&#41;](../../t-sql/data-types/decimal-and-numeric-transact-sql.md).  
  
 *s*  
 小数点の右側に格納できる 10 進数の最大桁数を示す、負以外の整数を指定します。有効桁数以下であることが必要です。 詳細については、次を参照してください[decimal and numeric &#40;Transact-SQL&#41;](../../t-sql/data-types/decimal-and-numeric-transact-sql.md).  
  
 [  **@nulltype =** ] **'***null_type***'**  
 別名データ型で NULL 値をどのように処理するかを指定します。 *null_type*は**varchar (** 8 **)** NULL の場合、既定値と、単一の引用符 ('NULL'、'NOT NULL' または 'NONULL') で囲む必要があります。 場合*null_type*によって明示的に定義されていない**sp_addtype**、現在の既定の null 値に設定されます。 既定の NULL 値の許容属性を確認するには、GETANSINULL システム関数を使用します。 この設定は、SET ステートメントまたは ALTER DATABASE を使用して変更できます。 NULL 値の許容属性は、明示的に定義してください。 場合**@phystype**は**ビット**、および**@nulltype**が指定されていない、既定値は NULL。  
  
> [!NOTE]  
>  *Null_type*パラメーターには、このデータ型の既定の null 値のみを定義します。 ただし別名データ型を使用してテーブルを作成する際に NULL 値の許容属性を明示的に定義した場合は、このパラメーターで定義した NULL 値の許容属性よりも優先されます。 詳細については、次を参照してください。 [ALTER TABLE &#40;TRANSACT-SQL&#41; ](../../t-sql/statements/alter-table-transact-sql.md)と[CREATE TABLE &#40;TRANSACT-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>コメント  
 別名データ型の名前は、データベース内で一意であることが必要ですが、異なる名前の別名データ型で同じ定義を使用することは可能です。  
  
 実行**sp_addtype**に表示される別名データ型を作成、 **sys.types**カタログ ビューを特定のデータベース。 別名データ型は、すべての新しいユーザー定義データベースで使用できる必要がある場合に、追加**モデル**します。 作成した別名データ型は、CREATE TABLE または ALTER TABLE で使用できます。別名データ型にデフォルトやルールをバインドすることもできます。 すべてのスカラー別名データ型を使用して作成される**sp_addtype**に含まれる、 **dbo**スキーマ。  
  
 別名データ型は、データベースの既定の照合順序を継承します。 列の照合順序と別名型の変数がで定義されている、 [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TABLE、ALTER TABLE、DECLARE @*local_variable*ステートメント。 データベースの既定の照合順序を変更すると、該当するデータ型の新しい列と変数にだけ新しい照合順序が適用されます。既存の列と変数の照合順序は変更されません。  
  
> [!IMPORTANT]  
>  旧バージョンとの互換性のため、**パブリック**データベース ロールには、使用して作成した別名データ型に対する REFERENCES 権限が自動的に付与**sp_addtype**します。 代わりに CREATE TYPE ステートメントを使用して別名データ型を作成するときに注意してください。 **sp_addtype**、自動的に権限がありません。  
  
 使用して別名データ型を定義することはできません、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **タイムスタンプ**、**テーブル**、 **xml**、 **varchar (max)**、 **nvarchar (max)** または**varbinary (max)** データ型。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーシップが必要です、 **db_owner**または**db_ddladmin**固定データベース ロール。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-creating-an-alias-data-type-that-does-not-allow-for-null-values"></a>A. NULL 値を許容しない別名データ型を作成する  
 次の例は、という別名データ型を作成します。 `ssn` (社会保障番号) に基づく、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-指定された**varchar**データ型。 `ssn` 型は、11 桁の社会保障番号 (999-99-9999) を格納する列で使用されます。 この列で NULL 値は許容されません。  
  
 `varchar(11)` には区切り記号 (かっこ) が含まれているため、単一引用符で囲みます。  
  
```  
USE master;  
GO  
EXEC sp_addtype ssn, 'varchar(11)', 'NOT NULL';  
GO  
```  
  
### <a name="b-creating-an-alias-data-type-that-allows-for-null-values"></a>B. NULL 値を許容する別名データ型を作成する  
 次の例では、NULL 値を許容する、`datetime` 型に基づく `birthday` という別名データ型を作成します。  
  
```  
USE master;  
GO  
EXEC sp_addtype birthday, datetime, 'NULL';  
```  
  
### <a name="c-creating-additional-alias-data-types"></a>C. 追加の別名データ型を作成する  
 次の例では、2 つの追加の別名データ型を作成する`telephone`と`fax`、国内および海外の電話と fax 番号。  
  
```  
USE master;  
GO  
EXEC sp_addtype telephone, 'varchar(24)', 'NOT NULL';  
GO  
EXEC sp_addtype fax, 'varchar(24)', 'NULL';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [データベース エンジン ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [CREATE TYPE &#40;Transact-SQL&#41;](../../t-sql/statements/create-type-transact-sql.md)   
 [CREATE DEFAULT &#40;Transact-SQL&#41;](../../t-sql/statements/create-default-transact-sql.md)   
 [CREATE RULE &#40;Transact-SQL&#41;](../../t-sql/statements/create-rule-transact-sql.md)   
 [sp_bindefault &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-bindefault-transact-sql.md)   
 [sp_bindrule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-bindrule-transact-sql.md)   
 [sp_droptype &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droptype-transact-sql.md)   
 [sp_rename &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md)   
 [sp_unbindefault &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unbindefault-transact-sql.md)   
 [sp_unbindrule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unbindrule-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
