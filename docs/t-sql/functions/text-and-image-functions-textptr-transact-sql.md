---
title: "TEXTPTR (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/23/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TEXTPTR_TSQL
- TEXTPTR
dev_langs:
- TSQL
helpviewer_keywords:
- TEXTPTR function
- viewing text pointer values
- text-pointer values
- displaying text pointer values
ms.assetid: 2672b8cb-f747-46f3-9358-9b49b3583b8e
caps.latest.revision: 36
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 84eaad80eff48689f91ab2679611d6eab6b2ce4d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="text-and-image-functions---textptr-transact-sql"></a>テキストとイメージ関数の TEXTPTR (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  返します。 テキスト ポインター値に対応する、**テキスト**、 **ntext**、または**イメージ**内の列**varbinary**形式です。 取得したテキスト ポインターの値は、READTEXT、WRITETEXT、および UPDATETEXT ステートメントで使用します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]代替機能は使用できません。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
TEXTPTR ( column )  
```  
  
## <a name="arguments"></a>引数  
 *列*  
 **テキスト**、 **ntext**、または**イメージ**に使用される列。  
  
## <a name="return-types"></a>戻り値の型  
 **varbinary**  
  
## <a name="remarks"></a>解説  
 行内テキストがあるテーブルの場合、TEXTPTR は、処理されるテキストのハンドルを返します。 テキストの値が NULL である場合も、有効なテキスト ポインターを取得できます。  
  
 ビューの列に対して TEXTPTR 関数を使用することはできません。 テーブルの列に対してのみ使用できます。 ビューの列に対して TEXTPTR 関数を使用する必要があります、互換性レベルを設定する 80 を使用して[ALTER DATABASE 互換性レベル](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)です。 場合と、テーブルに行内テキストがない場合、**テキスト**、 **ntext**、または**イメージ**列が UPDATETEXT ステートメントで初期化されていない、TEXTPTR は null ポインターを返します。  
  
 テキスト ポインターが存在するかどうかをテストするには、TEXTVALID を使ってください。 有効なテキスト ポインターがないと、UPDATETEXT、WRITETEXT、READTEXT は使用できません。  
  
 これらの関数とステートメントにも役立ちますを操作するときに**テキスト**、 **ntext**、および**イメージ**データ。  
  
|関数またはステートメント|Description|  
|---------------------------|-----------------|  
|PATINDEX**('***パターンを %***'、** *式***)**|指定された文字列内の文字位置を返します**テキスト**または**ntext**列です。|  
|DATALENGTH**(***式***)**|内のデータの長さを返します**テキスト**、 **ntext**、および**イメージ**列です。|  
|[SET TEXTSIZE]|制限 (バイト単位) を返します、**テキスト**、 **ntext**、または**イメージ**は SELECT ステートメントで返されるデータ。|  
|部分文字列**(***text_column*、*開始*、*長さ***)**|返します、 **varchar**によって指定された文字列*開始*オフセットおよび*長さ*です。 長さは 8 KB 未満で指定してください。|  
  
## <a name="examples"></a>使用例  
  
> [!NOTE]  
>  次の例を実行するにインストールする必要があります、 **pubs**データベース。  
  
### <a name="a-using-textptr"></a>A. TEXTPTR を使用する  
 次の例では、`TEXTPTR`を検索する関数、**イメージ**列`logo`に関連付けられている`New Moon Books`で、`pub_info`のテーブル、`pubs`データベース。 テキスト ポインターは、ローカル変数 `@ptrval.` に格納されます。  
  
```  
USE pubs;  
GO  
DECLARE @ptrval varbinary(16);  
SELECT @ptrval = TEXTPTR(logo)  
FROM pub_info pr, publishers p  
WHERE p.pub_id = pr.pub_id   
   AND p.pub_name = 'New Moon Books';  
GO  
```  
  
### <a name="b-using-textptr-with-in-row-text"></a>B. TEXTPTR を行内テキストと使用する  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、行内テキスト ポインターの次の例に示すように、トランザクション内で使用する必要があります。  
  
```  
CREATE TABLE t1 (c1 int, c2 text);  
EXEC sp_tableoption 't1', 'text in row', 'on';  
INSERT t1 VALUES ('1', 'This is text.');  
GO  
BEGIN TRAN;  
   DECLARE @ptrval VARBINARY(16);  
   SELECT @ptrval = TEXTPTR(c2)  
   FROM t1  
   WHERE c1 = 1;  
   READTEXT t1.c2 @ptrval 0 1;  
COMMIT;  
```  
  
### <a name="c-returning-text-data"></a>C. テキスト データを返す  
 次の例では、選択、`pub_id`列との 16 バイトのテキスト ポインター、`pr_info`列から、`pub_info`テーブル。  
  
```  
USE pubs;  
GO  
SELECT pub_id, TEXTPTR(pr_info)  
FROM pub_info  
ORDER BY pub_id;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
pub_id                                      
------ ----------------------------------   
0736   0x6c0000000000feffb801000001000100   
0877   0x6d0000000000feffb801000001000300   
1389   0x6e0000000000feffb801000001000500   
1622   0x700000000000feffb801000001000900   
1756   0x710000000000feffb801000001000b00   
9901   0x720000000000feffb801000001000d00   
9952   0x6f0000000000feffb801000001000700   
9999   0x730000000000feffb801000001000f00   
  
(8 row(s) affected)  
```  
  
 次の例では、TEXTPTR を使用せずにテキストの最初の `8000` バイトを返す方法を示します。  
  
```  
USE pubs;  
GO  
SET TEXTSIZE 8000;  
SELECT pub_id, pr_info  
FROM pub_info  
ORDER BY pub_id;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
pub_id pr_info                                                                                                                                                                                                                                                           
------ -----------------------------------------------------------------  
0736   New Moon Books (NMB) has just released another top ten publication. With the latest publication this makes NMB the hottest new publisher of the year!                                                                                                             
0877   This is sample text data for Binnet & Hardley, publisher 0877 in the pubs database. Binnet & Hardley is located in Washington, D.C.  
  
This is sample text data for Binnet & Hardley, publisher 0877 in the pubs database. Binnet & Hardley is located in Washi   
1389   This is sample text data for Algodata Infosystems, publisher 1389 in the pubs database. Algodata Infosystems is located in Berkeley, California.  
  
9999   This is sample text data for Lucerne Publishing, publisher 9999 in the pubs database. Lucerne publishing is located in Paris, France.  
  
This is sample text data for Lucerne Publishing, publisher 9999 in the pubs database. Lucerne publishing is located in   
  
(8 row(s) affected)  
```  
  
### <a name="d-returning-specific-text-data"></a>D. 特定のテキスト データを返す  
 次の例では検索、`text`列 (`pr_info`) に関連付けられている`pub_id``0736`で、`pub_info`のテーブル、`pubs`データベース。 まず、ローカル変数 `@val` が宣言されます。 テキスト ポインター (長いバイナリ文字列) が配置されます`@val`をパラメーターとして指定し、`READTEXT`ステートメントです。 これによって、5 番目のバイト (オフセットは 4) から開始して、10 バイトのデータが返されます。  
  
```  
USE pubs;  
GO  
DECLARE @val varbinary(16);  
SELECT @val = TEXTPTR(pr_info)   
FROM pub_info  
WHERE pub_id = '0736';  
READTEXT pub_info.pr_info @val 4 10;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
pr_info                                                                                                                                                                                                                                                           
-----------------------------------------------------------------------  
 is sample  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>参照  
 [DATALENGTH & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/datalength-transact-sql.md)   
 [PATINDEX & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/patindex-transact-sql.md)   
 [READTEXT & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/readtext-transact-sql.md)   
 [[SET textsize] & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-textsize-transact-sql.md)   
 [テキストとイメージ関数 & #40 です。TRANSACT-SQL と #41 です。](http://msdn.microsoft.com/library/b9c70488-1bf5-4068-a003-e548ccbc5199)   
 [UPDATETEXT &#40;Transact-SQL&#41;](../../t-sql/queries/updatetext-transact-sql.md)   
 [WRITETEXT &#40;Transact-SQL&#41;](../../t-sql/queries/writetext-transact-sql.md)  
  
  

