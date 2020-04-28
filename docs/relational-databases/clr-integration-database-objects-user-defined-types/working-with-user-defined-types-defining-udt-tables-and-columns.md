---
title: UDT テーブルと列の定義 |Microsoft Docs
description: UDT 定義を含むアセンブリを登録したら、それを列定義で使用できます。
ms.custom: ''
ms.date: 12/05/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- user-defined types [CLR integration], columns
- UDTs [CLR integration], columns
- columns [CLR integration]
- user-defined types [CLR integration], tables
- tables [CLR integration]
- UDTs [CLR integration], tables
- UDTs [CLR integration], indexes
- user-defined types [CLR integration], indexes
- indexes [CLR integration]
ms.assetid: aea495f4-ce26-4952-b019-38f012625f3f
author: rothja
ms.author: jroth
ms.openlocfilehash: 3f46ebc5089a4cb2fdb974df52d9bc876f925da4
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81486895"
---
# <a name="working-with-user-defined-types---defining-udt-tables-and-columns"></a>ユーザー定義の型の使用 - UDT テーブルと列の定義
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  ユーザー定義型 (UDT) 定義を含むアセンブリが[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースに登録されると、列定義で使用できます。 詳細については、「 [CREATE TYPE (Transact-SQL)](../../t-sql/statements/create-type-transact-sql.md)」を参照してください。  
  
## <a name="creating-tables-with-udts"></a>UDT を含むテーブルの作成  
 テーブルに UDT 列を作成するために特別な構文は用意されていません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 固有のデータ型であるかのように、列定義に UDT の名前を使用できます。 次の CREATE TABLE [!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントで**は、point という名前**のテーブルを作成します。この列には、 **id**という名前の列があります。これは、 **int** id 列とテーブルの主キーとして定義されています。 2番目の列は**Pointvalue**という名前で、データ型は**point**です。 この例で使用するスキーマ名は**dbo**です。 この操作には、スキーマ名を指定する権限が必要です。 スキーマ名を省略すると、データベース ユーザーの既定のスキーマが使用されます。  
  
```sql  
CREATE TABLE dbo.Points   
(ID int IDENTITY(1,1) PRIMARY KEY, PointValue Point)  
```  
  
## <a name="creating-indexes-on-udt-columns"></a>UDT 列でのインデックスの作成  
 UDT 列のインデックスの作成には次の 2 つの方法があります。  
  
-   **完全な値のインデックスを作成します。** この場合、UDT がバイナリ順であれば、CREATE INDEX [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用して UDT 列全体のインデックスを作成できます。  
  
-   **UDT 式のインデックスを作成します。** 保存される計算列のインデックスを UDT 式を使用して作成できます。 UDT のフィールド、メソッド、またはプロパティを UDT 式にできます。 この式は決定的である必要があり、この式でデータ アクセスを実行しないでください。  
  
 詳細については、「[CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server でのユーザー定義型の使用](../../relational-databases/clr-integration-database-objects-user-defined-types/working-with-user-defined-types-in-sql-server.md)     
 [CREATE TYPE (Transact-sql)](../../t-sql/statements/create-type-transact-sql.md)     
 [CLR ユーザー定義型](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)     
