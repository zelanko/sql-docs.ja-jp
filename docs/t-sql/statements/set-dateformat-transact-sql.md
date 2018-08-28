---
title: SET DATEFORMAT (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2cca6d29087d3ea638fec942d364927441d8b798
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43092455"
---
# <a name="set-dateformat-transact-sql"></a>SET DATEFORMAT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  **date**、**smalldatetime**、**datetime**、**datetime2**、**datetimeoffset** の各文字列を解釈する際の日付要素 (月、日、年) の順序を指定します。  
  
 すべての概要については [!INCLUDE[tsql](../../includes/tsql-md.md)] 日付と時刻のデータ型および関数、を参照してください。[ 日付と時刻のデータ型および関数と #40 です。TRANSACT-SQL と #41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
SET DATEFORMAT { format | @format_var }   
```  
  
## <a name="arguments"></a>引数  
 *format* | **@***format_var*  
 日付要素の順序を指定します。 有効なパラメーターは、**mdy**、**dmy**、**ymd**、**ydm**、**myd**、**dym** です。 Unicode または Unicode に変換可能な 2 バイト文字セット (DBCS) を指定できます。 言語設定が英語の既定値は **mdy** です。 サポートされている全言語の既定の DATEFORMAT については、「[sp_helplanguage &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helplanguage-transact-sql.md)」を参照してください。  
  
## <a name="remarks"></a>Remarks  
 DATEFORMAT **ydm** は、**date**、**datetime2**、**datetimeoffset** データ型にはサポートされていません。  
  
 文字列の形式によっては、DATEFORMAT 設定が文字列の解釈に与える影響が、**datetime** および **smalldatetime** の値と、**date**、**datetime2**、**datetimeoffset** の値で、異なる場合があります。 この設定は、文字列をデータベース格納用の日付値に変換する際の解釈に影響します。 データベースに格納された日付データ型の値 (ストレージ形式) の表示には影響しません。  
  
 ISO 8601 など、一部の文字列形式は、DATEFORMAT 設定とは無関係に解釈されます。  
  
 SET DATEFORMAT は、解析時ではなく実行時に設定されます。  
  
 SET DATEFORMAT で設定される日付の形式は、[SET LANGUAGE](../../t-sql/statements/set-language-transact-sql.md) で暗黙的に設定される日付の形式をオーバーライドします。  
  
## <a name="permissions"></a>アクセス許可  
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
  
## <a name="see-also"></a>参照  
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
  
  

