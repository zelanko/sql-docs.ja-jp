---
title: "データ型のシノニム (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 7/23/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- data types [SQL Server], synonyms
- alternate names [SQL Server]
- synonyms [SQL Server], data types
ms.assetid: 390eef67-1a49-4185-a971-e07765be9717
caps.latest.revision: 18
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1d9b1da2bdc7084268740cd7de2580e64ee9698b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="data-type-synonyms-transact-sql"></a>データ型のシノニム (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

データ型のシノニムに含まれる[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ISO の互換性のためです。 次の表に、シノニム、およびシノニムがマップされる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のシステム データ型を一覧表示します。
  
|シノニム|SQL Server システム データ型|  
|---|---|
|**バイナリのさまざまな**|**varbinary**|  
|**char のさまざまな**|**varchar**|  
|**文字**|**char**|  
|**文字**|**char (1)**|  
|**文字 (**  *n*  **)**|**char(n)**|  
|**文字がさまざまな (**  *n*  **)**|**varchar(n)**|  
|**年 12 月**|**decimal**|  
|**倍精度**|**float**|  
|**float**[**(***n***)**] の *n*  1. ~ 7. を =|**real**|  
|**float**[**(***n***)**] の *n*  8 ~ 15 を =|**float**|  
|**整数 (integer)**|**int**|  
|**各国語文字 (**  *n*  **)**|**nchar (n)**|  
|**national char (**  *n*  **)**|**nchar (n)**|  
|**各国語文字 varying (**  *n*  **)**|**nvarchar (n)**|  
|**varying、national char (**  *n*  **)**|**nvarchar (n)**|  
|**national テキスト**|**ntext**|  
|**timestamp**|rowversion|  
  
データ型のシノニムまたは CREATE TABLE、CREATE PROCEDURE などのデータ定義言語 (DDL) ステートメントに対応する基本データ型名の代わりに使用できますが、宣言 *@variable*です。 ただし、オブジェクトの作成後は、シノニムを確認できなくなります。 オブジェクトが作成されると、オブジェクトにはシノニムに関連付けられている基本データ型が割り当てられます。 オブジェクトを作成したステートメントでシノニムが指定された記録はありません。
  
結果セット列や式など、元のオブジェクトから派生したオブジェクトにはすべて基本データ型が割り当てられます。 それ以降のすべてのメタデータ関数は元のオブジェクトで実行され、派生オブジェクトはシノニムではなく基本データ型を報告します。 この動作はなど、メタデータ操作の発生**sp_help**し、その他のシステム ストアド プロシージャ、情報スキーマ ビュー、またはテーブルまたは結果セットのデータ型を報告するさまざまなデータ アクセス API メタデータ操作列です。
  
指定して、テーブルを作成するなど、 `national character varying`:
  
```sql
CREATE TABLE ExampleTable (PriKey int PRIMARY KEY, VarCharCol national character varying(10))  
```  
  
`VarCharCol`実際に割り当てられて、 **nvarchar (10)**データ型、すべての後続のメタデータ関数は、列を報告し、 **nvarchar (10)**列です。 メタデータ関数は報告されませんとして、**各国語文字 varying (10)**列です。
  
## <a name="see-also"></a>参照
[データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)
  
  

