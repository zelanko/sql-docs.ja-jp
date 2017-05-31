---
title: "ネイティブ コンパイル ストアド プロシージャの作成 | Microsoft Docs"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6b34010-cf62-4f65-bbdf-117f291cde7b
caps.latest.revision: 15
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 002507c03a66bd262e7d5dfa44283d2e3e0a901a
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="creating-natively-compiled-stored-procedures"></a>ネイティブ コンパイル ストアド プロシージャの作成
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  ネイティブ コンパイル ストアド プロシージャには、 [!INCLUDE[tsql](../../includes/tsql-md.md)] のプログラミングとクエリのセキュリティ構成が完全には実装されていません。 ネイティブ コンパイル ストアド プロシージャ内部で使用できない特定の [!INCLUDE[tsql](../../includes/tsql-md.md)] 構造が存在します。 詳細については、「 [ネイティブ コンパイル T-SQL モジュールでサポートされる機能](../../relational-databases/in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md)」を参照してください。  
  
 ただし、ネイティブ コンパイル ストアド プロシージャに対してのみサポートされる [!INCLUDE[tsql](../../includes/tsql-md.md)] 機能がいくつかあります。  
  
-   ATOMIC ブロック。 詳細については、「 [Atomic Blocks](../../relational-databases/in-memory-oltp/atomic-blocks-in-native-procedures.md)」を参照してください。  
  
-   ネイティブ コンパイル ストアド プロシージャのパラメーターおよび変数の**NOT NULL** 制約。 **NULL** として宣言されているパラメーターまたは変数に **NOT NULL**値を割り当てることはできません。 詳細については、「[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)」を参照してください。  
  
    -   CREATE PROCEDURE dbo.myproc (@myVarchar  varchar(32)  **not null**) ...  
  
    -   DECLARE @myVarchar  varchar(32)  **not null = "Hello"**; -- *(値に初期化する必要があります。)*  
  
    -   SET @myVarchar **= null**; -- *(コンパイルされますが実行時に失敗します。)*  
  
-   ネイティブ コンパイル ストアド プロシージャのスキーマ バインド。  
  
 ネイティブ コンパイル ストアド プロシージャは、[CREATE PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/create-procedure-transact-sql.md) を使用して作成します。 次の例は、メモリ最適化テーブルと、このテーブルに行を挿入するために使用されるネイティブ コンパイル ストアド プロシージャを示します。  
  
```tsql  
create table dbo.Ord  
(OrdNo integer not null primary key nonclustered,   
 OrdDate datetime not null,   
 CustCode nvarchar(5) not null)   
 with (memory_optimized=on)  
go  
  
create procedure dbo.OrderInsert(@OrdNo integer, @CustCode nvarchar(5))  
with native_compilation, schemabinding  
as   
begin atomic with  
(transaction isolation level = snapshot,  
language = N'English')  
  
  declare @OrdDate datetime = getdate();  
  insert into dbo.Ord (OrdNo, CustCode, OrdDate) values (@OrdNo, @CustCode, @OrdDate);  
end  
go  
```  
  
 コード サンプルの **NATIVE_COMPILATION** は、この [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャがネイティブ コンパイル ストアド プロシージャであることを示しています。 以下のオプションは必須です。  
  
|オプション|説明|  
|------------|-----------------|  
|**SCHEMABINDING**|ネイティブ コンパイル ストアド プロシージャは、参照するオブジェクトのスキーマにバインドされている必要があります。 これは、プロシージャによるテーブル参照が必要であることを意味しています。 プロシージャ内で参照されているテーブルにはスキーマ名が含まれている必要があり、クエリでワイルドカード (\*) は使用できません ( `SELECT * from...`はありません)。 このバージョンの**では、ネイティブ コンパイル ストアド プロシージャに対してのみ** SCHEMABINDING [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]がサポートされます。|  
|**BEGIN ATOMIC**|ネイティブ コンパイル ストアド プロシージャの本体は、厳密に 1 つの ATOMIC ブロックで構成されている必要があります。 ATOMIC ブロックでは、ストアド プロシージャのアトミック実行が保証されます。 プロシージャをアクティブなトランザクションのコンテキストの外部で呼び出した場合、新しいトランザクションが開始され、ATOMIC ブロックの末尾でコミットされます。 ネイティブ コンパイル ストアド プロシージャの ATOMIC ブロックには、次の 2 つの必須オプションがあります。<br /><br /> **TRANSACTION ISOLATION LEVEL**。 サポートされる分離レベルについては、「 [メモリ最適化テーブルのトランザクション分離](http://msdn.microsoft.com/library/8a6a82bf-273c-40ab-a101-46bd3615db8a) 」を参照してください。<br /><br /> **LANGUAGE**。 ストアド プロシージャの言語は、使用可能な言語または言語の別名の 1 つに設定されている必要があります。|  
  
## <a name="see-also"></a>参照  
 [ネイティブ コンパイル ストアド プロシージャ](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)  
  
  
