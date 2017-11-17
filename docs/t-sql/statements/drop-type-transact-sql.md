---
title: "ドロップ タイプ (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/12/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP TYPE
- DROP_TYPE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- user-defined types [SQL Server], deleting
- UDTs [SQL Server], deleting
- alias data types [SQL Server], removing
- DROP TYPE statement
ms.assetid: 11bf83f9-0718-4238-a835-83d2eb14ae7b
caps.latest.revision: 41
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4187c6bff08e5502f5edc6acd8d82334684a68d4
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="drop-type-transact-sql"></a>DROP TYPE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  現在のデータベースから、別名データ型または共通言語ランタイム (CLR) ユーザー定義型を削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
DROP TYPE [ IF EXISTS ] [ schema_name. ] type_name [ ; ]  
```  
  
## <a name="arguments"></a>引数  
 *場合に存在します。*  
 **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。  
  
 条件付きでは既に存在する場合にのみ、型を削除します。  
  
 *schema_name*  
 別名データ型またはユーザー定義型が属するスキーマの名前を指定します。  
  
 *type_name*  
 削除する別名データ型またはユーザー定義型の名前を指定します。  
  
## <a name="remarks"></a>解説  
 次のいずれかに当てはまる場合には、DROP TYPE ステートメントは実行されません。  
  
-   削除しようとしている別名データ型またはユーザー定義型の列を含むテーブルがデータベースにある場合。 クエリを実行して別名またはユーザー定義型の列に関する情報を取得できます、 [sys.columns](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)または[sys.column_type_usages](../../relational-databases/system-catalog-views/sys-column-type-usages-transact-sql.md)カタログ ビューです。  
  
-   計算列、CHECK 制約、スキーマ バインド ビュー、およびスキーマ バインド関数の中には、別名型またはユーザー定義型への参照を含む定義を持つものもあります。 クエリを実行してこれらの参照に関する情報を取得することができます、 [sys.sql_expression_dependencies](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)カタログ ビューです。  
  
-   データベースに関数、ストアド プロシージャ、またはトリガーが作成されていて、それらのルーチンが、削除しようとしている別名データ型またはユーザー定義型の変数やパラメーターを使用している場合。 クエリを実行して別名またはユーザー定義型のパラメーターに関する情報を取得できます、 [sys.parameters](../../relational-databases/system-catalog-views/sys-parameters-transact-sql.md)または[sys.parameter_type_usages](../../relational-databases/system-catalog-views/sys-parameter-type-usages-transact-sql.md)カタログ ビューです。  
  
## <a name="permissions"></a>Permissions  
 に対する CONTROL 権限が必要です*type_name*に対する ALTER 権限または*schema_name*です。  
  
## <a name="examples"></a>使用例  
 次の例では、`ssn` という名前の型が現在のデータベースに既に作成されていることを前提としています。  
  
```  
DROP TYPE ssn ;  
```  
  
## <a name="see-also"></a>参照  
 [CREATE TYPE &#40;Transact-SQL&#41;](../../t-sql/statements/create-type-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  

