---
title: "言語を設定する (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/05/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET_LANGUAGE_TSQL
- SET LANGUAGE
dev_langs:
- TSQL
helpviewer_keywords:
- LANGUAGE option
- languages [SQL Server], setting language
- SET LANGUAGE statement
- options [SQL Server], date
- default languages
ms.assetid: 0ec0e5cf-e115-4be9-a0db-e65837d6fa45
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 606c97d144bf209836ae89db199bd4d81ef137c0
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="set-language-transact-sql"></a>SET LANGUAGE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

  セッションの言語環境を指定します。 セッション言語の決定、 **datetime**形式とシステム メッセージ。  
  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
SET LANGUAGE { [ N ] 'language' | @language_var }   
```  
  
## <a name="arguments"></a>引数  
 **[N]****'***言語***'**  |   **@**  *language_var*  
 格納されている言語の名前は、 [sys.syslanguages](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md)です。 Unicode、または Unicode に変換される DBCS のいずれかを指定できます。 Unicode での言語を指定するには使用**N'***言語***'**です。 変数を指定する必要がありますを変数として指定すると場合、 **sysname**です。  
  
## <a name="remarks"></a>解説  
 SET LANGUAGE は、解析時ではなく実行時に設定されます。  
  
 SET LANGUAGE の設定を暗黙的に設定する[SET DATEFORMAT](../../t-sql/statements/set-dateformat-transact-sql.md)です。  
  
## <a name="permissions"></a>Permissions  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、既定の言語を `Italian` に設定して月名を表示した後、`us_english` に切り替えて再度月名を表示します。  
  
```  
DECLARE @Today DATETIME;  
SET @Today = '12/5/2007';  
  
SET LANGUAGE Italian;  
SELECT DATENAME(month, @Today) AS 'Month Name';  
  
SET LANGUAGE us_english;  
SELECT DATENAME(month, @Today) AS 'Month Name' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [syslanguages](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md)   
 [sp_helplanguage &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helplanguage-transact-sql.md)   
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
  
  
