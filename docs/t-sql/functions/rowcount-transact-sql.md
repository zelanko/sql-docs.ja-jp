---
title: "@@ROWCOUNT (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@ROWCOUNT_TSQL'
- '@@ROWCOUNT'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@ROWCOUNT function'
- number of rows affected by statement
- row affected by statements [SQL Server]
- statements [SQL Server], last statement
- counting rows
ms.assetid: 97a47998-81d9-4331-a244-9eb8b6fe4a56
caps.latest.revision: 40
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 411dc7eb628ddff52eb2f9426488e05860c9d279
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="x40x40rowcount-transact-sql"></a>& #x 40; & #x 40 です。ROWCOUNT (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  最後のステートメントの影響を受けた行数を返します。 行の数が 20億をより多くの場合を使用して[ROWCOUNT_BIG](../../t-sql/functions/rowcount-big-transact-sql.md)です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
@@ROWCOUNT  
```  
  
## <a name="return-types"></a>戻り値の型  
 **int**  
  
## <a name="remarks"></a>解説  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントは、@ で値を設定できる@ROWCOUNT次のようにします。  
  
-   セット@ROWCOUNT行の数に影響を受けるか、読み取る。 行はクライアントに送信しても、送信しなくてもかまいません。  
  
-   保持@ROWCOUNT前のステートメントの実行からです。  
  
-   リセット@ROWCOUNTを 0 に、クライアントに値を返さない、します。  
  
 単純な割り当ては常に設定を構成するステートメント、@@ROWCOUNT値は 1 にします。 行はクライアントに送信されません。 これらのステートメントの例には: @ 設定*local_variable*、RETURN、READTEXT、および選択せずに、クエリ SELECT GETDATE や SELECT などのステートメントを実行する**'***一般テキスト***'**.  
  
 クエリで割り当てを作成またはクエリのセットでの戻り値を使用するステートメント、@@ROWCOUNT行の数に値が影響を受けるか、たとえば、クエリによって読み取られた: @ 選択*local_variable* = c1 FROM t1 します。  
  
 データ操作言語 (DML) ステートメントのセット、@@ROWCOUNT値をクエリによって影響を受ける行の数と、クライアントに、その値を返します。 DML ステートメントは、クライアントに行を送信しない場合もあります。  
  
 DECLARE CURSOR および FETCH 設定、@@ROWCOUNT値は 1 にします。  
  
 EXECUTE ステートメントを保持する以前の @@ROWCOUNTです。  
  
 使用するなどのステートメント設定\<オプション >、DEALLOCATE CURSOR、CLOSE CURSOR、BEGIN TRANSACTION または COMMIT TRANSACTION、ROWCOUNT の値を 0 にリセットします。  
  
 ネイティブ コンパイル ストアド プロシージャを保持する以前の @@ROWCOUNTです。 [!INCLUDE[tsql](../../includes/tsql-md.md)]ネイティブ コンパイル ストアド プロシージャ内のステートメントはは設定しないでください@ROWCOUNTです。 詳細については、次を参照してください。 [Natively Compiled Stored Procedures](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)です。  
  
## <a name="examples"></a>使用例  
 次の例では、`UPDATE` ステートメントを実行し、`@@ROWCOUNT` を使用して、変更された行があるかどうかを調べます。  
  
```  
USE AdventureWorks2012;  
GO  
UPDATE HumanResources.Employee   
SET JobTitle = N'Executive'  
WHERE NationalIDNumber = 123456789  
IF @@ROWCOUNT = 0  
PRINT 'Warning: No rows were updated';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [システム関数 &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [SET ROWCOUNT と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-rowcount-transact-sql.md)  
  
  

