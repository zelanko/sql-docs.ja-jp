---
title: "SET DATEFORMAT (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATEFORMAT
- SET DATEFORMAT
- SET_DATEFORMAT_TSQL
- DATEFORMAT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], formats
- dates [SQL Server], ordering date parts
- SET DATEFORMAT option [SQL Server]
- DATEFORMAT option [SQL Server]
- date and time [SQL Server], SET DATEFORMAT
- options [SQL Server], date
- date and time [SQL Server], DATEFORMAT
- dateparts [SQL Server], dateformat
ms.assetid: da217878-7ec4-477e-aa13-604073c948f8
caps.latest.revision: 49
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: eba2bdb31a805c61b92a88ce5699c05dfa7fe09f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="set-dateformat-transact-sql"></a>SET DATEFORMAT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  解釈するため、月、日、および年の日付部分の順序を設定**日付**、 **smalldatetime**、 **datetime**、 **datetime2**と**datetimeoffset**文字の文字列。  
  
 すべての概要については[!INCLUDE[tsql](../../includes/tsql-md.md)]日付と時刻のデータ型および関数を参照してください[日付と時刻のデータ型および関数 &#40;TRANSACT-SQL と #41 です。](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
SET DATEFORMAT { format | @format_var }   
```  
  
## <a name="arguments"></a>引数  
 *形式* | **@***format_var*  
 日付要素の順序を指定します。 有効なパラメーターは**mdy**、 **dmy**、 **ymd**、 **ydm**、 **myd**、および**dym**. Unicode または Unicode に変換可能な 2 バイト文字セット (DBCS) を指定できます。 言語設定が英語の既定値は**mdy**です。 すべての既定の DATEFORMAT の言語サポートを参照してください[sp_helplanguage (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helplanguage-transact-sql.md).  
  
## <a name="remarks"></a>解説  
 DATEFORMAT **ydm**はサポートされていません**日付**、 **datetime2**と**datetimeoffset**データ型。  
  
 文字の文字列の解釈に DATEFORMAT の設定の効果が異なる可能性があります**datetime**と**smalldatetime**値の場合**日付**、 **datetime2**と**datetimeoffset**文字列の形式によっての値。 この設定は、文字列をデータベース格納用の日付値に変換する際の解釈に影響します。 データベースに格納された日付データ型の値 (ストレージ形式) の表示には影響しません。  
  
 ISO 8601 など、一部の文字列形式は、DATEFORMAT 設定とは無関係に解釈されます。  
  
 SET DATEFORMAT は、解析時ではなく実行時に設定されます。  
  
 SET DATEFORMAT オーバーライドの暗黙の日付の形式を指定[SET LANGUAGE](../../t-sql/statements/set-language-transact-sql.md)です。  
  
## <a name="permissions"></a>Permissions  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 同じ `DATEFORMAT` 設定が適用された各セッションの中で、異なる日付文字列を入力に使用した例を次に示します。  
  
```  
-- Set date format to day/month/year.  
SET DATEFORMAT dmy;  
GO  
DECLARE @datevar datetime2 = '31/12/2008 09:01:01.1234567';  
SELECT @datevar;  
GO  
-- Result: 2008-12-31 09:01:01.123  
SET DATEFORMAT dmy;  
GO  
DECLARE @datevar datetime2 = '12/31/2008 09:01:01.1234567';  
SELECT @datevar;  
GO  
-- Result: Msg 241: Conversion failed when converting date and/or time -- from character string.  
  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
```  
-- Set date format to month/day/year.  
SET DATEFORMAT mdy;  
DECLARE @datevar datetime2 = '12/31/2012 09:01:01.1234567';  
SELECT @datevar;  
  
```  
  
## <a name="see-also"></a>参照  
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
  
  


