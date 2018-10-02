---
title: データ型のシノニム (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 7/23/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- data types [SQL Server], synonyms
- alternate names [SQL Server]
- synonyms [SQL Server], data types
ms.assetid: 390eef67-1a49-4185-a971-e07765be9717
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 482177b87fb4d62cbebb64361e0b26ed9a681c1f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47816560"
---
# <a name="data-type-synonyms-transact-sql"></a>データ型のシノニム (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

ISO との互換性を保つために、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にはデータ型のシノニムが用意されています。 次の表に、シノニム、およびシノニムがマップされる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のシステム データ型を一覧表示します。
  
|シノニム|SQL Server システム データ型|  
|---|---|
|**Binary varying**|**varbinary**|  
|**char varying**|**varchar**|  
|**character**|**char**|  
|**character**|**char(1)**|  
|**character(** *n* **)**|**char(n)**|  
|**character varying(** *n* **)**|**varchar(n)**|  
|**dec**|**decimal**|  
|**DOUBLE PRECISION**|**float**|  
|**float**[**(***n***)**] for *n* = 1-7|**real**|  
|**float**[**(***n***)**] for *n* = 8-15|**float**|  
|**整数 (integer)**|**int**|  
|**national character(** *n* **)**|**nchar(n)**|  
|**national char(** *n* **)**|**nchar(n)**|  
|**national character varying(** *n* **)**|**nvarchar(n)**|  
|**national char varying(** *n* **)**|**nvarchar(n)**|  
|**national text**|**ntext**|  
|**timestamp**|rowversion|  
  
データ型のシノニムは、CREATE TABLE、CREATE PROCEDURE、または DECLARE *@variable* などのデータ定義言語 (DDL) ステートメントで、対応する基本データ型の名前の代わりに使用できます。 ただし、オブジェクトの作成後は、シノニムを確認できなくなります。 オブジェクトが作成されると、オブジェクトにはシノニムに関連付けられている基本データ型が割り当てられます。 オブジェクトを作成したステートメントでシノニムが指定された記録はありません。
  
結果セット列や式など、元のオブジェクトから派生したオブジェクトにはすべて基本データ型が割り当てられます。 それ以降のすべてのメタデータ関数は元のオブジェクトで実行され、派生オブジェクトはシノニムではなく基本データ型を報告します。 この動作は、**sp_help** およびその他のシステム ストアド プロシージャ、情報スキーマ ビュー、またはテーブルや結果セット列のデータ型を報告するさまざまなデータ アクセス API メタデータ操作などのメタデータ操作と共に発生します。
  
たとえば、`national character varying` を指定して、テーブルを作成できます。
  
```sql
CREATE TABLE ExampleTable (PriKey int PRIMARY KEY, VarCharCol national character varying(10))  
```  
  
`VarCharCol` が **nvarchar(10)** データ型に実際に割り当てられ、すべての後続のメタデータ関数は、列を **nvarchar(10)** 列として報告します。 メタデータ関数は報告されませんとして、 **各国語文字 varying (10)** 列です。
  
## <a name="see-also"></a>参照
[データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)
  
  
