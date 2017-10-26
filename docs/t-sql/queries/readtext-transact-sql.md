---
title: "READTEXT (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
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
caps.latest.revision: 27
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2c501fe8ea8146b4b2ec6e138f72fc2604b4b374
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="readtext-transact-sql"></a>READTEXT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  読み取り**テキスト**、 **ntext**、または**イメージ**値から、**テキスト**、 **ntext**、または**イメージ**列で、指定されたオフセットから開始し、指定したバイト数を読み取るします。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]使用して、 [SUBSTRING](../../t-sql/functions/substring-transact-sql.md)関数を使用します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
READTEXT { table.column text_ptr offset size } [ HOLDLOCK ]  
```  
  
## <a name="arguments"></a>引数  
 *テーブル***です。** *列*  
 読み取り元のテーブルと列の名前です。 テーブルおよび列名は、規則に従う必要があります[識別子](../../relational-databases/databases/database-identifiers.md)です。 テーブル名と列名は必ず指定してください。しかし、データベース名と所有者の指定は省略可能です。  
  
 *text_ptr*  
 有効なテキスト ポインターです。 *text_ptr*する必要があります**binary (16)**です。  
  
 *オフセット*  
 バイトの数です (ときに、**テキスト**または**イメージ**データ型を使用) または文字 (ときに、 **ntext**データ型を使用)、の読み取りを開始する前にスキップする**テキスト**、**イメージ**、または**ntext**データ。  
  
 *サイズ*  
 バイトの数です (ときに、**テキスト**または**イメージ**データ型を使用) または文字 (ときに、 **ntext**データ型を使用) 読み取るデータのです。 場合*サイズ*0 の場合は、4 kb のデータを読み取る。  
  
 HOLDLOCK  
 トランザクションが終了するまでテキスト値の読み取りをロックします。 他のユーザーは読み取りはできますが、変更はできません。  
  
## <a name="remarks"></a>解説  
 使用して、 [TEXTPTR](../../t-sql/functions/text-and-image-functions-textptr-transact-sql.md)有効なを取得する関数*text_ptr*値。 TEXTPTR をへのポインターを返します、**テキスト**、 **ntext**、または**イメージ**、指定された行または列、**テキスト**、 **ntext**、または**イメージ**1 つ以上の行が返される場合に、クエリによって返される最後の行の列です。 TEXTPTR は 16 バイトのバイナリ文字列を返すため、テキスト ポインターを保持するローカル変数を宣言し、READTEXT でその変数を使用することをお勧めします。 ローカル変数の宣言の詳細については、次を参照してください。 [DECLARE @local_variable & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/declare-local-variable-transact-sql.md).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、行内テキスト ポインターが存在しても、有効なことができない可能性があります。 詳細については、**行内テキスト**オプションを参照してください[sp_tableoption & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md). テキスト ポインターを無効化の詳細については、次を参照してください。 [sp_invalidate_textptr (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-invalidate-textptr-transact-sql.md).  
  
 値、@@TEXTSIZE関数 READTEXT READTEXT の指定したサイズよりも小さい場合に指定されたサイズよりも優先されます。 @@TEXTSIZE関数は、SET TEXTSIZE ステートメントによってセットが返されるデータのバイト数の制限を指定します。 TEXTSIZE のセッションの設定を設定する方法の詳細については、次を参照してください。 [SET TEXTSIZE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-textsize-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 READTEXT 権限は、特に指定のない限り指定されたテーブルで SELECT 権限を持つユーザーに与えられます。 SELECT 権限を譲渡した場合は、READTEXT 権限を譲渡できます。  
  
## <a name="examples"></a>使用例  
 次の例では、`pr_info` テーブルの `pub_info` 列の 2 文字目から 26 文字目までを読み取ります。  
  
> [!NOTE]  
>  この例を実行するにインストールする必要があります、 **pubs**サンプル データベース。  
  
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
  
  

