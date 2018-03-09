---
title: "圧縮する (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COMPRESS
- COMPRESS_TSQL
helpviewer_keywords:
- COMPRESS function
ms.assetid: c2bfe9b8-57a4-48b4-b028-e1a3ed5ece88
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 01500cd6560fd60dda2cb9060c2968d7c010d8e2
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="compress-transact-sql"></a>圧縮する (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

GZIP アルゴリズムを使用して、入力式が圧縮されます。 圧縮の結果は型のバイト配列**varbinary (max)**です。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
COMPRESS ( expression )  
```  
  
## <a name="arguments"></a>引数  
*式 (expression)*  
**Nvarchar (***n***)**、 **nvarchar (max)**、 **varchar (** *n*  **)**、 **varchar (max)**、 **varbinary (**  *n*  **)**、 **varbinary (max)**、 **char (***n***)**、 **nchar (**  *n*  **)**、または**バイナリ (***n***)**式。 詳細については、「[式 &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)」を参照してください。
  
## <a name="return-types"></a>戻り値の型
データ型を返す**varbinary (max)**入力の圧縮されたコンテンツを表すです。
  
## <a name="remarks"></a>解説  
圧縮されたデータのインデックスを付けることはできません。
  
COMPRESS 関数は、入力式として指定されたデータを圧縮し、データの圧縮の各セクションを呼び出す必要があります。 記憶域の中に、行またはページ レベルで自動圧縮は、次を参照してください。[データ圧縮](../../relational-databases/data-compression/data-compression.md)です。
  
## <a name="examples"></a>使用例  
  
### <a name="a-compress-data-during-the-table-insert"></a>A. 表の挿入中にデータを圧縮します。  
次の例では、テーブルに挿入されたデータを圧縮する方法を示します。
  
```sql
INSERT INTO player (name, surname, info )  
VALUES (N'Ovidiu', N'Cracium',   
        COMPRESS(N'{"sport":"Tennis","age": 28,"rank":1,"points":15258, turn":17}'));  
  
INSERT INTO player (name, surname, info )  
VALUES (N'Michael', N'Raheem', compress(@info));  
```  
  
### <a name="b-archive-compressed-version-of-deleted-rows"></a>B. 削除された行の圧縮バージョンをアーカイブします。  
次のステートメントから古いレコードをプレーヤーの削除、`player`テーブルが表示され、内のレコードを格納、`inactivePlayer`テーブルに圧縮された形式の領域を節約します。
  
```sql
DELETE player  
WHERE datemodified < @startOfYear  
OUTPUT id, name, surname datemodifier, COMPRESS(info)   
INTO dbo.inactivePlayers ;  
```  
  
## <a name="see-also"></a>参照
[文字列関数 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/string-functions-transact-sql.md)  
[圧縮解除 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/decompress-transact-sql.md)
  
  
