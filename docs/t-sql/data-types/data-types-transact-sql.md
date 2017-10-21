---
title: "データ型 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 9/13/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- system data types [SQL Server]
- data types [SQL Server]
- data types [SQL Server], about data types
ms.assetid: a54f7373-b247-4d61-8fb8-7f2ec7a8d0a4
caps.latest.revision: 45
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: d9a995f7d29fe91e14affa9266a9bce73acc9010
ms.openlocfilehash: 75efc7b5a58b3739a196e36b2c80d4ee37a92003
ms.contentlocale: ja-jp
ms.lasthandoff: 09/27/2017

---

# <a name="data-types-transact-sql"></a>データ型 (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、列、ローカル変数、式、パラメーターのそれぞれに、関連するデータ型があります。 データ型は、整数データ、文字データ、通貨データ、日時データ、バイナリ文字列など、オブジェクトが保持できるデータの種類を示す属性です。
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、システム データ型のセットが用意されており、ここに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で使用可能なデータ型がすべて定義されています。 独自のデータ型を定義することもできます。[!INCLUDE[tsql](../../includes/tsql-md.md)]または[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]です。 別名データ型は、システムが提供するデータ型に基づいています。 別名データ型の詳細については、次を参照してください。[の種類の作成 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-type-transact-sql.md). ユーザー定義型の特性は、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] でサポートされるプログラミング言語の 1 つを使用して作成するクラスのメソッドと演算子によって決まります。
  
データ型、照合順序、有効桁数、小数点以下桁数、または長さが異なる 2 つの式を演算子で結合する場合、結果の特性は次のように決まります。
-   結果のデータ型は、入力式のデータ型のうち優先順位が高いほうになります。 詳細については、「[データ型の優先順位 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md)」を参照してください。  
-   結果の照合順序は、結果のデータ型が、照合順序の優先順位の規則によって決まります**char**、 **varchar**、**テキスト**、 **nchar**、 **nvarchar**、または**ntext**です。 詳細については、次を参照してください。[照合の優先順位 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/collation-precedence-transact-sql.md).  
-   結果の有効桁数、小数点以下桁数、長さは、入力式の精度、桁数、長さによって決まります。 詳しくは、「[有効桁数、小数点以下桁数、および長さ &#40;Transact-SQL&#41;](../../t-sql/data-types/precision-scale-and-length-transact-sql.md)」をご覧ください。  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ISO の互換性のためには、データ型のシノニムを提供します。 詳細については、次を参照してください。[データ型のシノニムと #40 です。TRANSACT-SQL と #41 です。](../../t-sql/data-types/data-type-synonyms-transact-sql.md).
  
## <a name="data-type-categories"></a>データ型カテゴリ
データ型[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、次のカテゴリに編成されます。
  
|||  
|-|-|  
|真数|Unicode 文字の文字列|  
|概数|バイナリ文字列|  
|日付と時刻|他のデータ型|  
|文字の文字列||  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では一部のデータ型は、格納の特性に基づいて次のグループに分けられます。
-   大きな値データ型: **varchar (max)**、および**nvarchar (max)**  
-   ラージ オブジェクト データ型:**テキスト**、 **ntext**、**イメージ**、 **varbinary (max)**、および**xml**  
  
    > [!NOTE]  
    >  sp_help は、大きな値の長さとして-1 を返しますと**xml**データ型。  
  
### <a name="exact-numerics"></a>真数
  
|||  
|-|-|  
|[bigint](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)|[numeric](../../t-sql/data-types/decimal-and-numeric-transact-sql.md)|  
|[bit](../../t-sql/data-types/bit-transact-sql.md)|[smallint](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)|  
|[decimal](../../t-sql/data-types/decimal-and-numeric-transact-sql.md)|[smallmoney](../../t-sql/data-types/money-and-smallmoney-transact-sql.md)|  
|[int](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)|[tinyint](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)|  
|[money](../../t-sql/data-types/money-and-smallmoney-transact-sql.md)||  
  
### <a name="approximate-numerics"></a>概数
  
|||  
|-|-|  
|[float](../../t-sql/data-types/float-and-real-transact-sql.md)|[real](../../t-sql/data-types/float-and-real-transact-sql.md)|  
  
### <a name="date-and-time"></a>日付と時刻
  
|||  
|-|-|  
|[date](../../t-sql/data-types/date-transact-sql.md)|[datetimeoffset](../../t-sql/data-types/datetimeoffset-transact-sql.md)|  
|[datetime2](../../t-sql/data-types/datetime2-transact-sql.md)|[smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md)|  
|[datetime](../../t-sql/data-types/datetime-transact-sql.md)|[time](../../t-sql/data-types/time-transact-sql.md)|  
  
### <a name="character-strings"></a>文字の文字列
  
|||  
|-|-|  
|[char](../../t-sql/data-types/char-and-varchar-transact-sql.md)|[varchar](../../t-sql/data-types/char-and-varchar-transact-sql.md)|  
|[text](../../t-sql/data-types/ntext-text-and-image-transact-sql.md)||  
  
### <a name="unicode-character-strings"></a>Unicode 文字の文字列
  
|||  
|-|-|  
|[nchar](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md)|[nvarchar](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md)|  
|[ntext](../../t-sql/data-types/ntext-text-and-image-transact-sql.md)||  
  
### <a name="binary-strings"></a>バイナリ文字列
  
|||  
|-|-|  
|[[バイナリ]](../../t-sql/data-types/binary-and-varbinary-transact-sql.md)|[varbinary](../../t-sql/data-types/binary-and-varbinary-transact-sql.md)|  
|[image](../../t-sql/data-types/ntext-text-and-image-transact-sql.md)||  
  
### <a name="other-data-types"></a>他のデータ型
  
|||  
|-|-|  
|[カーソル (cursor)](../../t-sql/data-types/cursor-transact-sql.md)|[rowversion](../../t-sql/data-types/rowversion-transact-sql.md)|  
|[hierarchyid](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)|[uniqueidentifier](../../t-sql/data-types/uniqueidentifier-transact-sql.md)|  
|[sql_variant](../../t-sql/data-types/sql-variant-transact-sql.md)|[xml](../../t-sql/xml/xml-transact-sql.md)|  
|[Geometry 空間型](../../t-sql/spatial-geometry/spatial-types-geometry-transact-sql.md) |[Geography 空間型](../../t-sql/spatial-geography/spatial-types-geography.md)|  
|[テーブル](../../t-sql/data-types/table-transact-sql.md) | |
  
## <a name="see-also"></a>参照
[CREATE PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/create-procedure-transact-sql.md)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[宣言@local_variable& #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/declare-local-variable-transact-sql.md) 
 [EXECUTE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/execute-transact-sql.md)  
[式 &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
[関数と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/functions.md)  
[ような & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/like-transact-sql.md)  
[sp_droptype & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-droptype-transact-sql.md)  
[sp_help & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)  
[sp_rename & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md)
  
  

