---
title: "UDT テーブルと列の定義 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 55419a1d921713b88bfc046c94be74b137eb037a
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="working-with-user-defined-types---defining-udt-tables-and-columns"></a>UDT テーブルと列を定義する、ユーザー定義の型の使用
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
ユーザー定義型 (UDT) を含むアセンブリの定義が登録されるは[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース、列定義で使用できます。  
  
## <a name="creating-tables-with-udts"></a>UDT を含むテーブルの作成  
 テーブルに UDT 列を作成するために特別な構文は用意されていません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 固有のデータ型であるかのように、列定義に UDT の名前を使用できます。 次の CREATE TABLE[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントがという名前のテーブルを作成**ポイント**、という列を持つ**ID、**として定義されている、 **int** id 列とテーブルの主キー。 2 番目の列の名前は**PointValue**、データ型の**ポイント**です。 この例では使用されているスキーマ名**dbo**です。 この操作には、スキーマ名を指定する権限が必要です。 スキーマ名を省略すると、データベース ユーザーの既定のスキーマが使用されます。  
  
```  
CREATE TABLE dbo.Points   
(ID int IDENTITY(1,1) PRIMARY KEY, PointValue Point)  
```  
  
## <a name="creating-indexes-on-udt-columns"></a>UDT 列でのインデックスの作成  
 UDT 列のインデックスの作成には次の 2 つの方法があります。  
  
-   完全な値のインデックスを作成します。 この場合、UDT がバイナリ順であれば、CREATE INDEX [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用して UDT 列全体のインデックスを作成できます。  
  
-   UDT 式のインデックスを作成します。 保存される計算列のインデックスを UDT 式を使用して作成できます。 UDT のフィールド、メソッド、またはプロパティを UDT 式にできます。 この式は決定的である必要があり、この式でデータ アクセスを実行しないでください。  
  
 詳細については、次を参照してください。 [clr ユーザー定義型](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)と[CREATE INDEX &#40;です。TRANSACT-SQL と #41 です](../../t-sql/statements/create-index-transact-sql.md)。  
  
## <a name="see-also"></a>参照  
 [SQL Server のユーザー定義型の使用](../../relational-databases/clr-integration-database-objects-user-defined-types/working-with-user-defined-types-in-sql-server.md)  
  
  
