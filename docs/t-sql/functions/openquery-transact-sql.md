---
title: OPENQUERY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- OPENQUERY_TSQL
- OPENQUERY
dev_langs:
- TSQL
helpviewer_keywords:
- DELETE statement [SQL Server], OPENQUERY function
- OPENQUERY function
- FROM clause, OPENQUERY function
- UPDATE statement [SQL Server], OPENQUERY function
- pass-through queries [SQL Server]
- INSERT statement [SQL Server], OPENQUERY function
ms.assetid: b805e976-f025-4be1-bcb0-3a57b0c57717
caps.latest.revision: 42
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cbe4bb57e37d650a56f88413b03b8002f6ac2096
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/04/2018
ms.locfileid: "37787673"
---
# <a name="openquery-transact-sql"></a>OPENQUERY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定したパススルー クエリを、指定したリンク サーバーで実行します。 このサーバーは OLE DB データ ソースです。 OPENQUERY は、テーブル名と同じように、クエリの FROM 句で参照できます。 また、INSERT、UPDATE、または DELETE ステートメントの対象テーブルとして参照することもできます。 これは OLE DB プロバイダーの機能により制限されます。 クエリでは複数の結果セットが返されることがありますが、OPENQUERY では最初の 1 つのみが返されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
OPENQUERY ( linked_server ,'query' )  
```  
  
## <a name="arguments"></a>引数  
 *linked_server*  
 リンク サーバーの名前を表す識別子を指定します。  
  
 **'** *query* **'**  
 リンク サーバーで実行するクエリ文字列を指定します。 文字列の最大長は 8 KB です。  
  
## <a name="remarks"></a>Remarks  
 OPENQUERY の引数に変数は指定できません。  
  
 OPENQUERY を使用して、リンク サーバーで拡張ストアド プロシージャを実行することはできません。 ただし、4 つの要素で構成される名前を使用して、リンク サーバーで拡張ストアド プロシージャを実行することはできます。 例 :  
  
```sql  
EXEC SeattleSales.master.dbo.xp_msver  
```  
  
 FROM 句での OPENDATASOURCE、OPENQUERY、または OPENROWSET の呼び出しは、更新の対象として使用されるこれらの関数の呼び出しとは別に評価されます。これは、両方の呼び出しに同じ引数が指定されている場合にも当てはまります。 特に、いずれか一方の呼び出しの結果に適用されるフィルター条件または結合条件は、もう一方の結果に影響しません。  
  
## <a name="permissions"></a>アクセス許可  
 すべてのユーザーが OPENQUERY を実行できます。 リモート サーバーへの接続に使用される権限は、リンク サーバー用の定義から取得されます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-executing-an-update-pass-through-query"></a>A. UPDATE パススルー クエリを実行する  
 次の例では、例 A で作成したリンク サーバーに対して、`UPDATE` パススルー クエリを使用します。  
  
```sql  
UPDATE OPENQUERY (OracleSvr, 'SELECT name FROM joe.titles WHERE id = 101')   
SET name = 'ADifferentName';  
```  
  
### <a name="b-executing-an-insert-pass-through-query"></a>B. INSERT パススルー クエリを実行する  
 次の例では、例 A で作成したリンク サーバーに対して、`INSERT` パススルー クエリを使用します。  
  
```sql  
INSERT OPENQUERY (OracleSvr, 'SELECT name FROM joe.titles')  
VALUES ('NewTitle');  
```  
  
### <a name="c-executing-a-delete-pass-through-query"></a>C. DELETE パススルー クエリを実行する  
 次の例では、`DELETE` パススルー クエリを使用して、例 C で追加した行を削除します。  
  
```sql  
DELETE OPENQUERY (OracleSvr, 'SELECT name FROM joe.titles WHERE name = ''NewTitle''');  
```  
  
### <a name="d-executing-a-select-pass-through-query"></a>D. SELECT パススルー クエリを実行する  
 次の例では、`SELECT` パススルー クエリを使用して、例 C で追加した行を選択します。  
  
```sql  
SELECT * FROM OPENQUERY (OracleSvr, 'SELECT name FROM joe.titles WHERE name = ''NewTitle''');  
```  
    
## <a name="see-also"></a>参照  
 [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)   
 [FROM &#40;Transact-SQL&#41;](../../t-sql/queries/from-transact-sql.md)   
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [OPENDATASOURCE &#40;Transact-SQL&#41;](../../t-sql/functions/opendatasource-transact-sql.md)   
 [OPENROWSET &#40;Transact-SQL&#41;](../../t-sql/functions/openrowset-transact-sql.md)   
 [行セット関数 &#40;Transact-SQL&#41;](../../t-sql/functions/rowset-functions-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_serveroption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-serveroption-transact-sql.md)   
 [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)   
 [WHERE &#40;Transact-SQL&#41;](../../t-sql/queries/where-transact-sql.md)  
  
  
