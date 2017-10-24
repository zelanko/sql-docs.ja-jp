---
title: "WRITETEXT (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- WRITETEXT_TSQL
- WRITETEXT
dev_langs:
- TSQL
helpviewer_keywords:
- replacing data
- WRITETEXT statement
- updating data [SQL Server]
- nonlogged updating
- minimally logged updating [SQL Server]
- overwriting data
- data updates [SQL Server], WRITETEXT statement
ms.assetid: 80c252fd-a8b8-4a2e-888a-059081ed4109
caps.latest.revision: 52
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5bf092ec05c2ae07864c12f092cf8b98f97234fa
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="writetext-transact-sql"></a>WRITETEXT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  最小ログ記録、対話型が、既存の更新を許可**テキスト**、 **ntext**、または**イメージ**列です。 WRITETEXT は、影響のある列内の既存のすべてのデータを上書きします。 は、WRITETEXT を使用できません**テキスト**、 **ntext**、および**イメージ**ビュー内の列です。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]大きな値データ型を使用し、 **.**WRITE 句、[更新](../../t-sql/queries/update-transact-sql.md)ステートメント代わりにします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
WRITETEXT [BULK]  
  { table.column text_ptr }  
  [ WITH LOG ] { data }  
```  
  
## <a name="arguments"></a>引数  
 BULK  
 アップロード ツールによるバイナリ データ ストリームのアップロードを有効にします。 ストリームは、TDS プロトコル レベルでツールが提供する必要があります。 データ ストリームが存在しない場合、クエリ プロセッサは BULK オプションを無視します。  
  
> [!IMPORTANT]  
>  BULK オプションで使用しないことをお勧め[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-ベースのアプリケーションです。 このオプションを変更またはの将来のバージョンで削除された可能性があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 *テーブル* **.column**  
 テーブルの名前を指定および**テキスト**、 **ntext**、または**イメージ**列が更新されます。 テーブルおよび列名は、規則に従う必要があります[識別子](../../relational-databases/databases/database-identifiers.md)です。 データベース名と所有者名の指定は省略可能です。  
  
 *text_ptr*  
 ポインターを格納する値は、**テキスト**、 **ntext**、または**イメージ**データ。 *text_ptr*する必要があります**binary (16)**です。テキスト ポインターを作成するには、実行、[挿入](../../t-sql/statements/insert-transact-sql.md)または[更新](../../t-sql/queries/update-transact-sql.md)ステートメントがの null でないデータを**テキスト**、 **ntext**、または**イメージ**列です。  
  
 WITH LOG  
 によって無視[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 ログ記録は、データベースで有効になっている復旧モデルによって異なります。  
  
 *データ*  
 実際は**テキスト**、 **ntext**または**イメージ**格納するデータ。 *データ*リテラルまたはパラメーターを指定できます。 WRITETEXT を使用して対話的に挿入できるテキストの最大長は約 120 KB です**テキスト**、 **ntext**、および**イメージ**データ。  
  
## <a name="remarks"></a>解説  
 WRITETEXT を使用してに置き換える**テキスト**、 **ntext**、および**イメージ**データとを変更する UPDATETEXT**テキスト**、 **ntext**、および**イメージ**データ。 UPDATETEXT より柔軟の一部だけを変更するため、**テキスト**、 **ntext**、または**イメージ**列全体ではなく列です。  
  
 最適なパフォーマンスをことをお勧め**テキスト**、 **ntext**、および**イメージ**データを挿入または 8,040 バイトの倍数であるチャンクのサイズを更新します。  
  
 データベースの復旧モデルが単純型または一括ログ記録場合**テキスト**、 **ntext**、および**イメージ**WRITETEXT を使用する操作は、新しいデータが、最小ログ記録操作挿入または追加します。  
  
> [!NOTE]  
>  既存の値を更新するときには、最小限のログ記録は使用されません。  
  
 WRITETEXT が正しく機能するためには、その列は既に有効なテキスト ポインターを含んでいる必要があります。  
  
 行内のテキスト、テーブルがない場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]初期化しないで領域を節約**テキスト**列で明示的または暗黙的な null 値が追加されると**テキスト**INSERT、およびなしのテキスト ポインターを持つ列を指定できますこのような null 値を取得します。 初期化するために**テキスト**列を NULL には、UPDATE ステートメントを使用します。 テーブルに行内テキストがある場合、テキスト列を初期化して NULL にする必要はなく、常にテキスト ポインターを取得できます。  
  
 ODBC SQLPutData 関数は高速であり、WRITETEXT よりも小さい動的メモリを使用します。 この関数の 2 ギガバイトを挿入できる**テキスト**、 **ntext**、または**イメージ**データ。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の行内テキスト ポインター**テキスト**、 **ntext**、または**イメージ**データが存在しても、有効なことができない可能性があります。 Text in row オプションの詳細については、次を参照してください。 [sp_tableoption & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md). テキスト ポインターを無効になります。 詳細については、次を参照してください。 [sp_invalidate_textptr (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-invalidate-textptr-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 指定したテーブルの UPDATE 権限が必要です。 UPDATE 権限が転送されるときに、この権限は譲渡できます。  
  
## <a name="examples"></a>使用例  
 次の例では、テキスト ポインターをローカル変数 `@ptrval` に置き、`WRITETEXT` が指す行に `@ptrval` で新しいテキスト文字列を入れます。  
  
> [!NOTE]  
>  この例を実行するには、pubs サンプル データベースをインストールする必要があります。  
  
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
WRITETEXT pub_info.pr_info @ptrval 'New Moon Books (NMB) has just released another top ten publication. With the latest publication this makes NMB the hottest new publisher of the year!';  
GO  
ALTER DATABASE pubs SET RECOVERY SIMPLE;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
 [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [UPDATETEXT & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/updatetext-transact-sql.md)  
  
  

