---
title: "-(コメント) (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- --_TSQL
- Comment
- --
dev_langs: TSQL
helpviewer_keywords:
- nonexecuting text strings [SQL Server]
- remarks [SQL Server]
- -- (comment character)
- comments [SQL Server]
ms.assetid: 676ea8c2-52c1-4ef6-9354-320f1a091153
caps.latest.revision: "43"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 132d4dc19112858df5fbab33961b5ad99c70dd1c
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="---comment-transact-sql"></a>-- (コメント) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  ユーザーが入力したテキストを示します。 コメントは、単独行に指定したり、[!INCLUDE[tsql](../../includes/tsql-md.md)] コマンド ラインの終端で入れ子にしたり、または、[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントの中に指定したりすることができます。 サーバーはコメントを評価しません。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
-- text_of_comment  
```  
  
## <a name="arguments"></a>引数  
 *text_of_comment*  
 コメントのテキストを構成する文字列です。  
  
## <a name="remarks"></a>解説  
 1 行のコメントまたは入れ子にしたコメントには、2 つのハイフン (--) を使用します。 -- と共に挿入されるコメントは、改行文字で終了します。 コメントの長さには制限がありません。 次の表に、テキストのコメント化/コメント解除に使用できるキーボード ショートカットを示します。  
  
|操作|Standard|  
|------------|--------------|  
|選択したテキストをコメント化する|Ctrl + K、Ctrl + C|  
|選択したテキストのコメント化を解除する|Ctrl + K、Ctrl + U|  
  
 キーボード ショートカットの詳細については、次を参照してください。 [SQL Server Management Studio のキーボード ショートカット](../../tools/sql-server-management-studio/sql-server-management-studio-keyboard-shortcuts.md)です。  
  
 複数行のコメントを参照してください。[スラッシュ スター &#40;です。ブロック コメント &#41;&#40;です。TRANSACT-SQL と #41 です](../../t-sql/language-elements/slash-star-comment-transact-sql.md)。  
  
## <a name="examples"></a>使用例  
 次の例では、-- コメント文字を使用します。  
  
```  
-- Choose the AdventureWorks2012 database.  
USE AdventureWorks2012;  
GO  
-- Choose all columns and all rows from the Address table.  
SELECT *  
FROM Person.Address  
ORDER BY PostalCode ASC; -- We do not have to specify ASC because   
-- that is the default.  
GO  
```  
  
## <a name="see-also"></a>参照  
 [フロー制御言語 &#40;です。TRANSACT-SQL と #41 です。](~/t-sql/language-elements/control-of-flow.md)  
  
  
