---
title: READTEXT (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 10/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- READTEXT_TSQL
- READTEXT
dev_langs:
- TSQL
helpviewer_keywords:
- column reading [SQL Server]
- READTEXT statement
- reading columns
ms.assetid: 91b69853-1381-4306-8343-afdb73105738
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c1659dfcc9ca8908ce756eb41b32fd30649decfa
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="readtext-transact-sql"></a>READTEXT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  **text**、**ntext**、または **image** 列から **text**、**ntext**、または **image** 値を読み取ります。指定したオフセットから読み取りを開始し、指定したバイト数を読み取ります。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 代わりに、[SUBSTRING](../../t-sql/functions/substring-transact-sql.md) 関数を使用してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
READTEXT { table.column text_ptr offset size } [ HOLDLOCK ]  
```  
  
## <a name="arguments"></a>引数  
 *table* **.** *column*  
 読み取り元のテーブルと列の名前です。 テーブル名と列名は、[識別子](../../relational-databases/databases/database-identifiers.md)のルールに従っている必要があります。 テーブル名と列名は必ず指定してください。しかし、データベース名と所有者の指定は省略可能です。  
  
 *text_ptr*  
 有効なテキスト ポインターです。 *text_ptr* は **binary(16)** 型である必要があります。  
  
 *offset*  
 **text**、**image**、または **ntext** データの読み取りを開始する前にスキップするバイト数 (**text** または **image** データ型が使用される場合) または文字数 (**ntext** データ型が使用される場合) です。  
  
 *size*  
 読み取るデータのバイト数 (**text** または **image** データ型が使用される場合) または文字数 (**ntext** データ型が使用される場合) です。 *size* が 0 の場合は、4 KB のデータを読み取ります。  
  
 HOLDLOCK  
 トランザクションが終了するまでテキスト値の読み取りをロックします。 他のユーザーは読み取りはできますが、変更はできません。  
  
## <a name="remarks"></a>Remarks  
 有効な *text_ptr* 値を取得するには、[TEXTPTR](../../t-sql/functions/text-and-image-functions-textptr-transact-sql.md) 関数を使用します。 TEXTPTR は、指定された行の **text**、**ntext**、または **image** 列へのポインター、あるいは、複数の行が返される場合には、クエリにより最後に返された行の **text**、**ntext**、または **image** 列へのポインターを返します。 TEXTPTR は 16 バイトのバイナリ文字列を返すため、テキスト ポインターを保持するローカル変数を宣言し、READTEXT でその変数を使用することをお勧めします。 ローカル変数の宣言の詳細については、「[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)」を参照してください。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、行内テキスト ポインターが存在しても、有効ではない場合があります。 **text in row** オプションの詳細については、「[sp_tableoption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md)」を参照してください。 テキスト ポインターを無効にする方法の詳細については、「[sp_invalidate_textptr &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-invalidate-textptr-transact-sql.md)」を参照してください。  
  
 READTEXT で指定されたサイズよりも @@TEXTSIZE 関数の値の方が小さい場合は、READTEXT に代わってその関数の値が使用されます。 @@TEXTSIZE 関数は、SET TEXTSIZE ステートメントで設定される、返されるデータのバイト数の上限を指定します。 TEXTSIZE のセッション設定の設定方法の詳細については、「[SET TEXTSIZE &#40;Transact-SQL&#41;](../../t-sql/statements/set-textsize-transact-sql.md)」を参照してください。  
  
## <a name="permissions"></a>アクセス許可  
 READTEXT 権限は、特に指定のない限り指定されたテーブルで SELECT 権限を持つユーザーに与えられます。 SELECT 権限を譲渡した場合は、READTEXT 権限を譲渡できます。  
  
## <a name="examples"></a>使用例  
 次の例では、`pr_info` テーブルの `pub_info` 列の 2 文字目から 26 文字目までを読み取ります。  
  
> [!NOTE]  
>  この例を実行するには、**pubs** サンプル データベースをインストールする必要があります。  
  
```  
USE pubs;  
GO  
DECLARE @ptrval varbinary(16);  
SELECT @ptrval = TEXTPTR(pr_info)   
   FROM pub_info pr INNER JOIN publishers p  
      ON pr.pub_id = p.pub_id   
      AND p.pub_name = 'New Moon Books'  
READTEXT pub_info.pr_info @ptrval 1 25;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [@@TEXTSIZE &#40;Transact-SQL&#41;](../../t-sql/functions/textsize-transact-sql.md)   
 [UPDATETEXT &#40;Transact-SQL&#41;](../../t-sql/queries/updatetext-transact-sql.md)   
 [WRITETEXT &#40;Transact-SQL&#41;](../../t-sql/queries/writetext-transact-sql.md)  
  
  
