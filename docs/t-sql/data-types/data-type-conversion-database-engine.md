---
title: "データ型の変換 (データベース エンジン) |Microsoft ドキュメント"
ms.custom: 
ms.date: 7/23/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
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
- CAST function
- converting data types [SQL Server]
- CONVERT function
- data types [SQL Server], converting
- implicit data type conversions
- explicit data type conversions [SQL Server]
- converting data types [SQL Server], about converting data types
ms.assetid: ffacf45e-a488-48d0-9bb0-dcc7fd365299
caps.latest.revision: 37
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c0ed7f8e0e681de9f962e3eb963c0af315a0c25c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="data-type-conversion-database-engine"></a>データ型の変換 (データベース エンジン)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

データ型は、以下のシナリオで変換される場合があります。
-   あるオブジェクトのデータを他のオブジェクトのデータに移動、比較、または結合する場合は、あるオブジェクトのデータ型から他のオブジェクトのデータ型への変換が必要な場合があります。  
-   ときにデータを[!INCLUDE[tsql](../../includes/tsql-md.md)]結果列、リターン コード、または出力パラメーターがプログラム変数に移動からデータを変換する必要があります、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]システム データ型の変数のデータ型にします。  
  
アプリケーション変数間で変換する際に、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]結果セットの列、リターン コード、パラメーター、またはパラメーター マーカー、サポートされているデータ型の変換は、データベース API によって定義されます。
  
## <a name="implicit-and-explicit-conversion"></a>暗黙的および明示的な変換
データ型は、暗黙的または明示的に変換できます。
  
暗黙的な変換はユーザーが意識する必要はありません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]別に 1 つのデータ型からデータを自動的に変換します。 たとえば、ときに、 **smallint**と比較されます、 **int**、 **smallint**暗黙的に変換されます**int**比較の前に実行します。
  
**GETDATE()** 0 の日付の形式に暗黙的に変換します。 **SYSDATETIME()**に暗黙的に日付形式 21 に変換します。
  
明示的な変換では、CAST 関数または CONVERT 関数を使用します。
  
[CAST および CONVERT](../../t-sql/functions/cast-and-convert-transact-sql.md)関数は、1 つのデータ型から (ローカル変数、列、または別の式) の値を別に変換します。 たとえば、次`CAST`関数の数値を変換する`$157.27`の文字の文字列に`'157.27'`:
  
```sql
CAST ( $157.27 AS VARCHAR(10) )  
```  
  
場合は、CONVERT ではなく CAST を使用[!INCLUDE[tsql](../../includes/tsql-md.md)]プログラム コードを ISO に準拠します。 CONVERT のスタイル機能を利用する場合は、CAST ではなく CONVERT を使用します。
  
次の図は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システムで提供されるデータ型に許可されている、すべての明示的および暗黙的なデータ型変換です。 これらを含める**xml**、 **bigint**、および**sql_variant**です。 暗黙の変換からの割り当てではありません、 **sql_variant**データ型への暗黙的な変換が**sql_variant**です。
  
![データ型変換テーブル](../../t-sql/data-types/media/lrdatahd.png "データ型変換テーブル")
  
## <a name="data-type-conversion-behaviors"></a>データ型変換の動作
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクト間のデータ型の変換を行う場合、暗黙的または明示的なデータ型変換がサポートされない場合があります。 たとえば、 **nchar**値に変換できない、**イメージ**値。 **Nchar**にのみ変換できます**バイナリ**暗黙的な変換を明示的な変換を使用して、**バイナリ**はサポートされていません。 ただし、 **nchar**明示的または暗黙的に変換できる**nvarchar**です。
  
次のトピックでは、対応するデータ型変換の動作について説明しています。
  
 - [binary と varbinary &#40;Transact-SQL&#41;](../../t-sql/data-types/binary-and-varbinary-transact-sql.md)  
 - [datetime2 &#40;Transact-SQL&#41;](../../t-sql/data-types/datetime2-transact-sql.md)  
 - [money および smallmoney & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/data-types/money-and-smallmoney-transact-sql.md)  
 - [ビット & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/data-types/bit-transact-sql.md)  
 - [datetimeoffset &#40;Transact-SQL&#41;](../../t-sql/data-types/datetimeoffset-transact-sql.md)  
 - [smalldatetime & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/data-types/smalldatetime-transact-sql.md)  
 - [char および varchar &#40;Transact-SQL&#41;](../../t-sql/data-types/char-and-varchar-transact-sql.md)  
 - [decimal および numeric 型 &#40;TRANSACT-SQL と #41 です。](../../t-sql/data-types/decimal-and-numeric-transact-sql.md)  
 - [sql_variant &#40;Transact-SQL&#41;](../../t-sql/data-types/sql-variant-transact-sql.md)  
 - [date &#40;Transact-SQL&#41;](../../t-sql/data-types/date-transact-sql.md)  
 - [float、real および #40 です。TRANSACT-SQL と #41 です。](../../t-sql/data-types/float-and-real-transact-sql.md)  
 - [時間と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/data-types/time-transact-sql.md)  
 - [datetime & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/data-types/datetime-transact-sql.md)  
 - [int、bigint、smallint 型、および tinyint (&) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)  
 - [一意識別子と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/data-types/uniqueidentifier-transact-sql.md)  
  
###  <a name="converting-data-types-by-using-ole-automation-stored-procedures"></a>OLE オートメーション ストアド プロシージャを使用したデータ型の変換  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は [!INCLUDE[tsql](../../includes/tsql-md.md)] のデータ型を使用し、OLE オートメーションは [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] のデータ型を使用するため、OLE オートメーション ストアド プロシージャでは両方の間で渡されるデータの型を変換する必要があります。
  
次の表は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型から [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] データ型への変換を示します。
  
|SQL Server データ型|Visual Basic データ型|  
|--------------------------|----------------------------|  
|**char**、 **varchar**、**テキスト**、 **nvarchar**、 **ntext**|**文字列**|  
|**10 進**、**数値**|**文字列**|  
|**bit**|**ブール値**|  
|**バイナリ**、 **varbinary**、**イメージ**|1 次元**Byte()**配列|  
|**int**|**Long**|  
|**smallint**|**Integer**|  
|**tinyint**|**バイト**|  
|**float**|**Double**|  
|**real**|**単一**|  
|**money**、 **smallmoney**|**Currency**|  
|**datetime**、 **smalldatetime**|**[日付]**|  
|上記以外は NULL に設定|**Variant**を Null に設定|  
  
すべての単一[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]値が 1 つに変換[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]の例外を除いて値**バイナリ**、 **varbinary**、および**イメージ**値。 これらの値は 1 次元に変換されます**Byte()**配列[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]です。 この配列の範囲には、**バイト (**0 を*長さ*1**)**場所*長さ*のバイト数が、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **バイナリ**、 **varbinary**、または**イメージ**値。
  
次の表は、[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] データ型から [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型への変換を示しています。
  
|Visual Basic データ型|SQL Server データ型|  
|----------------------------|--------------------------|  
|**長い**、**整数**、**バイト**、**ブール**、**オブジェクト**|**int**|  
|**二重**、**単一**|**float**|  
|**Currency**|**money**|  
|**[日付]**|**datetime**|  
|**文字列**4,000 文字以下|**varchar**/**nvarchar**|  
|**文字列**複数の 4,000 文字|**テキスト**/**ntext**|  
|1 次元**Byte()**以下 8,000 バイトの配列|**varbinary**|  
|1 次元**Byte()** 8000 バイトを超える配列|**image**|  
  
## <a name="see-also"></a>参照
[OLE オートメーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)  
[CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[COLLATE & #40 です。TRANSACT-SQL と #41 です。](http://msdn.microsoft.com/library/4ba6b7d8-114a-4f4e-bb38-fe5697add4e9)
  
  

