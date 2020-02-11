---
title: サポートされるデータ型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: a7380ef0-c9d7-49e4-b6de-fad34752b9f3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: de5f805a9d722974adf7975f713436bc7b1ca4d0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63155150"
---
# <a name="supported-data-types"></a>サポートされるデータ型
  メモリ最適化テーブルとネイティブコンパイルストアドプロシージャでは、次のデータ型がサポートされ**て**います。  
  
 **数値データ型**  
  
|データ型|詳細情報|  
|---------------|--------------------------|  
|INT|[int、bigint、smallint、および tinyint &#40;Transact-sql&#41;](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql)|  
|bigint|[int、bigint、smallint、および tinyint &#40;Transact-sql&#41;](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql)|  
|smallint|[int、bigint、smallint、および tinyint &#40;Transact-sql&#41;](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql)|  
|tinyint|[int、bigint、smallint、および tinyint &#40;Transact-sql&#41;](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql)|  
|decimal|[decimal および numeric &#40;Transact-sql&#41;](/sql/t-sql/data-types/decimal-and-numeric-transact-sql)|  
|numeric|[decimal および numeric &#40;Transact-sql&#41;](/sql/t-sql/data-types/decimal-and-numeric-transact-sql)|  
|float|[Transact-sql&#41;の float 型と real 型の &#40;](/sql/t-sql/data-types/float-and-real-transact-sql)|  
|real|[Transact-sql&#41;の float 型と real 型の &#40;](/sql/t-sql/data-types/float-and-real-transact-sql)|  
|money|[money と smallmoney &#40;Transact-sql&#41;](/sql/t-sql/data-types/money-and-smallmoney-transact-sql)|  
|smallmoney|[money と smallmoney &#40;Transact-sql&#41;](/sql/t-sql/data-types/money-and-smallmoney-transact-sql)|  
  
 **文字列データ型**  
  
|データ型|詳細情報|  
|---------------|--------------------------|  
|char(n)|[char および varchar &#40;Transact-sql&#41;](/sql/t-sql/data-types/char-and-varchar-transact-sql)|  
|varchar (n) <sup>1</sup>|[char および varchar &#40;Transact-sql&#41;](/sql/t-sql/data-types/char-and-varchar-transact-sql)|  
|nchar(n)|[nchar および nvarchar &#40;Transact-sql&#41;](/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql)|  
|nvarchar (n) <sup>1</sup>|[nchar および nvarchar &#40;Transact-sql&#41;](/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql)|  
|sysname|[nchar および nvarchar &#40;Transact-sql&#41;](/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql)|  
  
 <sup>1</sup>行の合計で8060バイトの制限があり、可変長型の場合はカウント (n) です。  
  
 サポートされている照合順序の詳細については、「[照合順序とコードページ](../../database-engine/collations-and-code-pages.md)」を参照してください。  
  
 **日付と時刻のデータ型**  
  
|データ型|詳細情報|  
|---------------|--------------------------|  
|date|[Transact-sql&#41;&#40;日付](/sql/t-sql/data-types/date-transact-sql)|  
|time|[Transact-sql&#41;&#40;時間](/sql/t-sql/data-types/time-transact-sql)|  
|DATETIME|[datetime &#40;Transact-sql&#41;](/sql/t-sql/data-types/datetime-transact-sql)|  
|datetime2|[datetime2 &#40;Transact-sql&#41;](/sql/t-sql/data-types/datetime2-transact-sql)|  
|smalldatetime|[smalldatetime &#40;Transact-sql&#41;](/sql/t-sql/data-types/smalldatetime-transact-sql)|  
  
 **バイナリ データ型**  
  
|データ型|詳細情報|  
|---------------|--------------------------|  
|bit|[Transact-sql&#41;のビット &#40;](/sql/t-sql/data-types/bit-transact-sql)|  
|binary(n)|[binary および varbinary &#40;Transact-sql&#41;](/sql/t-sql/data-types/binary-and-varbinary-transact-sql)|  
|varbinary (n) <sup>1</sup>|[binary および varbinary &#40;Transact-sql&#41;](/sql/t-sql/data-types/binary-and-varbinary-transact-sql)|  
  
 <sup>1</sup>行の合計で8060バイトの制限があり、可変長型の場合はカウント (n) です。  
  
 **その他のデータ型**  
  
|データ型|詳細情報|  
|---------------|--------------------------|  
|UNIQUEIDENTIFIER|[uniqueidentifier &#40;Transact-sql&#41;](/sql/t-sql/data-types/uniqueidentifier-transact-sql)|  
  
 **サポートされていないデータ型**  
  
 次のデータ型はサポートされません。  
  
||||  
|-|-|-|  
|DATETIMEOFFSET|GEOGRAPHY|GEOMETRY|  
|HIERARCHYID|ラージ オブジェクト (LOB)。 例: varchar(max)、nvarchar(max)、varbinary(max)、image、xml、text、ntext。|ROWVERSION|  
|sql_variant|CLR 関数|UDT (ユーザー定義型)|  
  
## <a name="see-also"></a>参照  
 [Transact-sql によるインメモリ OLTP のサポート](transact-sql-support-for-in-memory-oltp.md)   
 [メモリ最適化テーブルへの LOB 列の実装](../../database-engine/implementing-lob-columns-in-a-memory-optimized-table.md)   
 [メモリ最適化テーブルへの SQL_VARIANT の実装](implementing-sql-variant-in-a-memory-optimized-table.md)  
  
  
