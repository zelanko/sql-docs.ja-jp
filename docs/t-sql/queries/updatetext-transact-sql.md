---
title: "UPDATETEXT (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/23/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- UPDATETEXT
- UPDATETEXT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- text updates [SQL Server]
- updating data [SQL Server]
- data updates [SQL Server], UPDATETEXT statement
- UPDATETEXT statement
ms.assetid: d73c28ee-3972-4afd-af8d-ebbbd9e50793
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c4d7c7a51daeba116e695ba9cae797f0d69c70cf
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="updatetext-transact-sql"></a>UPDATETEXT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  既存の更新**テキスト**、 **ntext**、または**イメージ**フィールドです。 一部のみを変更する UPDATETEXT を使用して、**テキスト**、 **ntext**、または**イメージ**の列に適切です。 WRITETEXT を使用して更新し、全体を置き換える**テキスト**、 **ntext**、または**イメージ**フィールドです。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]大きな値データ型を使用し、 **.**WRITE 句、[更新](../../t-sql/queries/update-transact-sql.md)ステートメント代わりにします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
UPDATETEXT [BULK] { table_name.dest_column_name dest_text_ptr }  
  { NULL | insert_offset }  
     { NULL | delete_length }  
     [ WITH LOG ]  
     [ inserted_data  
    | { table_name.src_column_name src_text_ptr } ]  
```  
  
## <a name="arguments"></a>引数  
 BULK  
 アップロード ツールによるバイナリ データ ストリームのアップロードを有効にします。 ストリームは、TDS プロトコル レベルでツールが提供する必要があります。 データ ストリームが存在しない場合、クエリ プロセッサは BULK オプションを無視します。  
  
> [!IMPORTANT]  
>  BULK オプションで使用しないことをお勧め[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-ベースのアプリケーションです。 このオプションを変更またはの将来のバージョンで削除された可能性があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 *table_name* **.** *dest_column_name*  
 テーブルの名前を指定し、**テキスト**、 **ntext**、または**イメージ**を更新する列。 テーブル名と列名は、規則に従う必要があります[識別子](../../relational-databases/databases/database-identifiers.md)です。 データベース名と所有者名の指定は省略可能です。  
  
 *dest_text_ptr*  
 テキスト ポインター値 (TEXTPTR 関数から返される) を指す、**テキスト**、 **ntext**、または**イメージ**にデータを更新します。 *dest_text_ptr* must be **binary(**16**)**.  
  
 *insert_offset*  
 更新の開始位置を 0 を起点として指定します。 **テキスト**または**イメージ**列、 *insert_offset*新しいデータを挿入する前に、既存の列の先頭からスキップするバイト数です。 **Ntext**列、 *insert_offset*文字の数です (各**ntext**文字は 2 バイト)。 既存の**テキスト**、 **ntext**、または**イメージ**この 0 から始まる開始位置以降にあるデータが新しいデータを確保するために右にシフトします。 値 0 を指定した場合、新しいデータは既存のデータの先頭に挿入されます。 NULL の場合、新しいデータは既存のデータの最後に追加されます。  
  
 *delete_length*  
 既存のファイルから削除するデータの長さ**テキスト**、 **ntext**、または**イメージ**列で、開始位置として、 *insert_offset*位置。 *Delete_length*(バイト) 値が指定されて**テキスト**と**イメージ**列の文字**ntext**列です。 各**ntext**文字は 2 バイトです。 値 0 を指定した場合、データは削除されません。 NULL の値からのすべてのデータを削除する、 *insert_offset* 、既存の末尾に位置**テキスト**または**イメージ**列です。  
  
 WITH LOG  
 ログ記録は、データベースで有効になっている復旧モデルによって異なります。  
  
 *inserted_data*  
 既存に挿入されるデータは、**テキスト**、 **ntext**、または**イメージ**位置にある列、 *insert_offset*場所。 これは、1 つ**char**、 **nchar**、 **varchar**、 **nvarchar**、**バイナリ**、 **varbinary**、**テキスト**、 **ntext**、または**イメージ**値。 *inserted_data*リテラルまたは変数を指定できます。  
  
 *table_name.src_column_name*  
 テーブルの名前を指定し、**テキスト**、 **ntext**、または**イメージ**列を挿入するデータのソースとして使用します。 テーブル名と列名は、識別子の規則に従っている必要があります。  
  
 *src_text_ptr*  
 テキスト ポインター値 (TEXTPTR 関数から返される) を指す、**テキスト**、 **ntext**、または**イメージ**列を挿入するデータのソースとして使用します。  
  
> [!NOTE]  
>  *scr_text_ptr*値することはできませんと同じ*dest_text_ptr*値。  
  
## <a name="remarks"></a>解説  
 新しく挿入されるデータは、1 つを指定できます*inserted_data*定数、テーブル名、列名、またはテキスト ポインターです。  
  
|[更新] 操作|UPDATETEXT パラメーター|  
|-------------------|---------------------------|  
|既存のデータの置換|Null 以外を指定*insert_offset*値、0 以外*delete_length*値、および、新しいデータを挿入します。|  
|既存のデータの削除|Null 以外を指定*insert_offset*値および 0 以外*delete_length*です。 挿入する新しいデータは指定しないでください。|  
|新しいデータの挿入|指定して、 *insert_offset*値、 *delete_length* 0 であり、新しいデータを挿入します。|  
  
 最適なパフォーマンスをことをお勧め**テキスト**、 **ntext**と**イメージ**データを挿入または 8,040 バイトの倍数である単位で更新します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、行内テキスト ポインターを**テキスト**、 **ntext**、または**イメージ**データが存在しても、有効なことができない可能性があります。 Text in row オプションの詳細については、次を参照してください。 [sp_tableoption &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md). テキスト ポインターを無効になります。 詳細については、次を参照してください。 [sp_invalidate_textptr (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-invalidate-textptr-transact-sql.md).  
  
 初期化するために**テキスト**列を NULL、WRITETEXT; を使用します。UPDATETEXT を初期化します**テキスト**列が空の文字列。  
  
## <a name="permissions"></a>権限  
 指定したテーブルの UPDATE 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、テキスト ポインターをローカル変数 `@ptrval` に代入した後、`UPDATETEXT` を使用してスペル ミスを更新します。  
  
> [!NOTE]  
>  この例を実行するには、pubs データベースをインストールする必要があります。  
  
```  
USE pubs;  
GO  
ALTER DATABASE pubs SET RECOVERY SIMPLE;  
GO  
DECLARE @ptrval binary(16);  
SELECT @ptrval = TEXTPTR(pr_info)   
   FROM pub_info pr, publishers p  
      WHERE p.pub_id = pr.pub_id   
      AND p.pub_name = 'New Moon Books'  
UPDATETEXT pub_info.pr_info @ptrval 88 1 'b';  
GO  
ALTER DATABASE pubs SET RECOVERY FULL;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [READTEXT &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/queries/readtext-transact-sql.md)   
 [TEXTPTR &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/text-and-image-functions-textptr-transact-sql.md)   
 [WRITETEXT &#40;Transact-SQL&#41;](../../t-sql/queries/writetext-transact-sql.md)  
  
  
