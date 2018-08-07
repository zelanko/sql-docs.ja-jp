---
title: データ型の変換 (データベース エンジン) | Microsoft Docs
ms.custom: ''
ms.date: 7/23/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: eb22a3686b026382da88fede58cb613834254b96
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/02/2018
ms.locfileid: "39456876"
---
# <a name="data-type-conversion-database-engine"></a>データ型の変換 (データベース エンジン)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

データ型は、以下のシナリオで変換される場合があります。
-   あるオブジェクトのデータを他のオブジェクトのデータに移動、比較、または結合する場合は、あるオブジェクトのデータ型から他のオブジェクトのデータ型への変換が必要な場合があります。  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] 結果列、リターン コード、または出力パラメーターのデータをプログラム変数に移動する場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のシステム データ型から変数のデータ型にデータを変換する必要があります。  
  
アプリケーション変数と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の結果セット列、リターン コード、パラメーター、またはパラメーター マーカーの間でデータ型を変換する場合、サポートされるデータ型変換はデータベース API によって決まります。
  
## <a name="implicit-and-explicit-conversion"></a>暗黙的な変換と明示的な変換
データ型は、暗黙的または明示的に変換できます。
  
暗黙的な変換はユーザーが意識する必要はありません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がデータのデータ型を自動的に変換します。 たとえば、**smallint** 型を **int** 型と比較する場合、比較を実行する前に、**smallint** 型から **int** 型に暗黙的に変換されます。
  
**GETDATE()** は、暗黙的に日付スタイル 0 に変換します。 **SYSDATETIME()** は、暗黙的に日付スタイル 21 に変換します。
  
明示的な変換では、CAST 関数または CONVERT 関数を使用します。
  
[CAST と CONVERT](../../t-sql/functions/cast-and-convert-transact-sql.md) の各関数は、値 (ローカル変数、列、または他の式) のデータ型を変換します。 たとえば、次の `CAST` 関数は数値 `$157.27` を文字列 `'157.27'` に変換します。
  
```sql
CAST ( $157.27 AS VARCHAR(10) )  
```  
  
[!INCLUDE[tsql](../../includes/tsql-md.md)] のプログラム コードを ISO に準拠させる場合は、CONVERT ではなく CAST を使います。 CONVERT のスタイル機能を利用する場合は、CAST ではなく CONVERT を使用します。
  
次の図は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システムで提供されるデータ型に許可されている、すべての明示的および暗黙的なデータ型変換です。 **xml**、**bigint**、**sql_variant** が含まれます。 代入時に **sql_variant** データ型からの暗黙的な変換は行われませんが、**sql_variant** への暗黙的な変換は行われます。
  
![データ型変換表](../../t-sql/data-types/media/lrdatahd.png "データ型変換表")
  
## <a name="data-type-conversion-behaviors"></a>データ型変換の動作
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクト間のデータ型の変換を行う場合、暗黙的または明示的なデータ型変換がサポートされない場合があります。 たとえば、**nchar** 型の値を **image** 型の値に変換することはできません。 **nchar** は明示的な変換によってのみ **binary** に変換できます。**binary** への暗黙的な変換はサポートされません。 ただし、**nchar** は暗黙的、明示的のどちらでも **nvarchar** に変換できます。
  
次のトピックでは、対応するデータ型変換の動作について説明しています。
  
 - [binary と varbinary &#40;Transact-SQL&#41;](../../t-sql/data-types/binary-and-varbinary-transact-sql.md)  
 - [datetime2 &#40;Transact-SQL&#41;](../../t-sql/data-types/datetime2-transact-sql.md)  
 - [money および smallmoney & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/data-types/money-and-smallmoney-transact-sql.md)  
 - [bit &#40;Transact-SQL&#41;](../../t-sql/data-types/bit-transact-sql.md)  
 - [datetimeoffset &#40;Transact-SQL&#41;](../../t-sql/data-types/datetimeoffset-transact-sql.md)  
 - [smalldatetime &#40;Transact-SQL&#41;](../../t-sql/data-types/smalldatetime-transact-sql.md)  
 - [char および varchar &#40;Transact-SQL&#41;](../../t-sql/data-types/char-and-varchar-transact-sql.md)  
 - [10 進数の数値と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/data-types/decimal-and-numeric-transact-sql.md)  
 - [sql_variant &#40;Transact-SQL&#41;](../../t-sql/data-types/sql-variant-transact-sql.md)  
 - [date &#40;Transact-SQL&#41;](../../t-sql/data-types/date-transact-sql.md)  
 - [float、real および #40 です。TRANSACT-SQL と #41 です。](../../t-sql/data-types/float-and-real-transact-sql.md)  
 - [time &#40;Transact-SQL&#41;](../../t-sql/data-types/time-transact-sql.md)  
 - [datetime &#40;Transact-SQL&#41;](../../t-sql/data-types/datetime-transact-sql.md)  
 - [int、bigint、smallint、および tinyint &#40;Transact-SQL&#41;](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)  
 - [uniqueidentifier &#40;Transact-SQL&#41;](../../t-sql/data-types/uniqueidentifier-transact-sql.md)  
  
###  <a name="converting-data-types-by-using-ole-automation-stored-procedures"></a>OLE オートメーション ストアド プロシージャを使用したデータ型の変換  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は [!INCLUDE[tsql](../../includes/tsql-md.md)] のデータ型を使用し、OLE オートメーションは [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] のデータ型を使用するため、OLE オートメーション ストアド プロシージャでは両方の間で渡されるデータの型を変換する必要があります。
  
次の表は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型から [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] データ型への変換を示します。
  
|SQL Server データ型|Visual Basic データ型|  
|--------------------------|----------------------------|  
|**char**、**varchar**、**text**、**nvarchar**、**ntext**|**String**|  
|**decimal**、**numeric**|**String**|  
|**bit**|**ブール値**|  
|**binary**、**varbinary**、**image**|1 次元 **Byte()** 配列|  
|**int**|**Long**|  
|**smallint**|**Integer**|  
|**tinyint**|**Byte**|  
|**float**|**Double**|  
|**real**|**単一**|  
|**money**、 **smallmoney**|**Currency**|  
|**datetime**、**smalldatetime**|**日付**|  
|上記以外は NULL に設定|null 値に設定された **Variant**|  
  
**binary**、**varbinary**、**image** の各型の値を除いて、1 つの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 値はすべて 1 つの [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 値に変換されます。 これらの値は [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] の 1 次元 **Byte()** 配列に変換されます。 この配列の範囲は、**Byte(** 0 ～ *length*1 **)** です。*length* は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の **binary**、**varbinary**、または **image** の値のバイト数です。
  
次の表は、[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] データ型から [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型への変換を示しています。
  
|Visual Basic データ型|SQL Server データ型|  
|----------------------------|--------------------------|  
|**Long**、**Integer**、**Byte**、**Boolean**、**Object**|**int**|  
|**Double**、**Single**|**float**|  
|**Currency**|**money**|  
|**日付**|**datetime**|  
|4,000 文字以下の **String**|**varchar**/**nvarchar**|  
|4,000 文字を超える **String**|**text**/**ntext**|  
|8,000 バイト以下の 1 次元 **Byte()** 配列|**varbinary**|  
|8,000 バイトを超える 1 次元 **Byte()** 配列|**image**|  
  
## <a name="see-also"></a>参照
[OLE オートメーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)  
[CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[COLLATE &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/4ba6b7d8-114a-4f4e-bb38-fe5697add4e9)
  
  
