---
title: UDT テーブルと列の定義 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: clr
ms.tgt_pltfrm: ''
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
caps.latest.revision: 11
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 360715f3b239347aedcae2b50a0e21f7a2943125
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37351804"
---
# <a name="defining-udt-tables-and-columns"></a>UDT テーブルと UDT 列の定義
  ユーザー定義型 (UDT) を含むアセンブリの定義に登録されていると、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース、列定義で使用できます。  
  
## <a name="creating-tables-with-udts"></a>UDT を含むテーブルの作成  
 テーブルに UDT 列を作成するために特別な構文は用意されていません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 固有のデータ型であるかのように、列定義に UDT の名前を使用できます。 次の CREATE TABLE[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントでは、という名前のテーブルを作成します。**ポイント**、という名前の列で**ID、** として定義されている、 `int` id 列と \、テーブルの主キー。 2 番目の列の名前は**PointValue**のデータ型を持つ**ポイント**します。 この例で使用するスキーマ名が**dbo**します。 この操作には、スキーマ名を指定する権限が必要です。 スキーマ名を省略すると、データベース ユーザーの既定のスキーマが使用されます。  
  
```  
CREATE TABLE dbo.Points   
(ID int IDENTITY(1,1) PRIMARY KEY, PointValue Point)  
```  
  
## <a name="creating-indexes-on-udt-columns"></a>UDT 列でのインデックスの作成  
 UDT 列のインデックスの作成には次の 2 つの方法があります。  
  
-   完全な値のインデックスを作成します。 この場合、UDT がバイナリ順であれば、CREATE INDEX [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用して UDT 列全体のインデックスを作成できます。  
  
-   UDT 式のインデックスを作成します。 保存される計算列のインデックスを UDT 式を使用して作成できます。 UDT のフィールド、メソッド、またはプロパティを UDT 式にできます。 この式は決定的である必要があり、この式でデータ アクセスを実行しないでください。  
  
 詳細については、次を参照してください。 [clr ユーザー定義型](clr-user-defined-types.md)と[CREATE INDEX & #40 です。TRANSACT-SQL と #41 です](/sql/t-sql/statements/create-index-transact-sql)。  
  
## <a name="see-also"></a>参照  
 [SQL Server でのユーザー定義型の使用](working-with-user-defined-types-in-sql-server.md)  
  
  
