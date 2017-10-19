---
title: "SWITCHOFFSET (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 12/02/2015
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SWITCHTZ
- SWITCHTZ_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- functions [SQL Server], time
- functions [SQL Server], date and time
- SWITCHOFFSET function [SQL Server]
- time [SQL Server], functions
- date and time [SQL Server], SWITCHOFFSET
- time zones [SQL Server]
ms.assetid: 32a48e36-0aa4-4260-9fe9-cae9197d16c5
caps.latest.revision: 26
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: 3c81153c233e68d12347dc47ae9c232f4a5ee030
ms.contentlocale: ja-jp
ms.lasthandoff: 10/17/2017

---
# <a name="switchoffset-transact-sql"></a>SWITCHOFFSET (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  返します、 **datetimeoffset**ストアドのタイム ゾーン オフセットから指定された新しいタイム ゾーン オフセットへ変更された値。  
  
 すべての概要については[!INCLUDE[tsql](../../includes/tsql-md.md)]日付と時刻のデータ型および関数を参照してください[日付と時刻のデータ型および関数 &#40;TRANSACT-SQL と #41 です。](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
SWITCHOFFSET ( DATETIMEOFFSET, time_zone )   
```  
  
## <a name="arguments"></a>引数  
 *DATETIMEOFFSET*  
 式に解決されることができるは、 **datetimeoffset (n)**値。  
  
 *time_zone*  
 [+|-]TZH:TZM 形式の文字列、またはタイム ゾーン オフセットを表す (分の) 符号付き整数を指定します。夏時間は認識されて調整されているものと想定されます。  
  
## <a name="return-type"></a>戻り値の型  
 **datetimeoffset**の桁数を持つ、 *DATETIMEOFFSET*引数。  
  
## <a name="remarks"></a>解説  
 SWITCHOFFSET を使用して、選択、 **datetimeoffset**に格納されていたタイム ゾーン オフセットとは異なるタイム ゾーン オフセットの値。 SWITCHOFFSET は、格納されている更新されない*time_zone*値。  
  
 SWITCHOFFSET を使用して更新すること、 **datetimeoffset**列です。  
  
 SWITCHOFFSET を GETDATE() 関数と共に使用すると、クエリの実行速度が遅くなる場合があります。 これは、クエリ オプティマイザーが datetime 値の基数を正確に推定できないためです。 この問題を解決するには、OPTION (RECOMPILE) クエリ ヒントを使用し、次に同じクエリが実行されるときにクエリ オプティマイザーによってクエリ プランが強制的に再コンパイルされるようにします。 その後、オプティマイザーでは、基数の推定が正確になり、より効率的なクエリ プランが生成されます。 RECOMPILE クエリ ヒントの詳細については、次を参照してください。[クエリ ヒント & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/hints-transact-sql-query.md).  
  
```  
DECLARE @dt datetimeoffset = switchoffset (CONVERT(datetimeoffset, GETDATE()), '-04:00');   
SELECT * FROM t    
WHERE c1 > @dt OPTION (RECOMPILE);  
  
```  
  
## <a name="examples"></a>使用例  
 次の例では、`SWITCHOFFSET` を使用して、データベースに保存されている値とは異なるタイム ゾーン オフセットを表示します。  
  
```  
CREATE TABLE dbo.test   
    (  
    ColDatetimeoffset datetimeoffset  
    );  
GO  
INSERT INTO dbo.test   
VALUES ('1998-09-20 7:45:50.71345 -5:00');  
GO  
SELECT SWITCHOFFSET (ColDatetimeoffset, '-08:00')   
FROM dbo.test;  
GO  
--Returns: 1998-09-20 04:45:50.7134500 -08:00  
SELECT ColDatetimeoffset  
FROM dbo.test;  
--Returns: 1998-09-20 07:45:50.7134500 -05:00  
```  
  
## <a name="see-also"></a>参照  
 [CAST および CONVERT & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [タイム ゾーンと #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/at-time-zone-transact-sql.md)  
  
  



