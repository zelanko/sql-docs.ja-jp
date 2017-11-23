---
title: "TRIGGER_NESTLEVEL (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TRIGGER_NESTLEVEL
- TRIGGER_NESTLEVEL_TSQL
dev_langs: TSQL
helpviewer_keywords:
- triggers [SQL Server], number executed
- number of triggers
- TRIGGER_NESTLEVEL function
ms.assetid: 6a33e74a-0cf9-4ae1-a1e4-4a137a3ea39d
caps.latest.revision: "31"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 0416b80079ac4c1dfb6dc10b507fd85800dd3a27
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="triggernestlevel-transact-sql"></a>TRIGGER_NESTLEVEL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  トリガーを起動したステートメントに対して実行されたトリガーの数を返します。 TRIGGER_NESTLEVEL は、DML トリガーおよび DDL トリガーで、現在の入れ子レベルを調べるときに使用します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
TRIGGER_NESTLEVEL ( [ object_id ] , [ 'trigger_type' ] , [ 'trigger_event_category' ] )  
```  
  
## <a name="arguments"></a>引数  
 *object_id*  
 トリガーのオブジェクト ID です。 場合*object_id*を指定すると、ステートメントが返されたについて、指定されたトリガーが実行された回数。 場合*object_id*が指定されていないステートメントが返されるすべてのトリガーが実行された回数。  
  
 **'** *trigger_type* **'**  
 AFTER トリガーと INSTEAD OF トリガーのどちらに TRIGGER_NESTLEVEL を適用するかを指定します。 指定**AFTER** AFTER トリガーの場合。 指定**IOT** INSTEAD OF トリガー。 場合*trigger_type*が指定されている*trigger_event_category*も指定する必要があります。  
  
 **'** *trigger_event_category* **'**  
 DML トリガーと DDL トリガーのどちらに TRIGGER_NESTLEVEL を適用するかを指定します。 指定**DML** DML トリガーです。 指定**DDL** DDL トリガー。 場合*trigger_event_category*が指定されている*trigger_type*も指定する必要があります。 のみです**AFTER**で指定できる**DDL**、DDL トリガーは AFTER トリガーのみできます。  
  
## <a name="remarks"></a>解説  
 パラメーターを指定しない場合、TRIGGER_NESTLEVEL は呼び出し履歴上のトリガーの合計数を返します。 この合計数にはそのトリガー自身も含まれます。 トリガーがコマンドを実行することにより、別のトリガーが起動されたり、トリガーを起動するセッションを作成するときはパラメーターを省略できます。  
  
 トリガーを特定の型とイベント カテゴリの呼び出し履歴上のトリガーの合計数を返すには指定*object_id* 0 を = です。  
  
 TRIGGER_NESTLEVEL をトリガーの外部で実行し、かつ、どのパラメーターも NULL でない場合は、0 が返されます。  
  
 任意のパラメーターに明示的に NULL を指定した場合、TRIGGER_NESTLEVEL をトリガーの内部で使用したか外部で使用したかにかかわらず、値 NULL が返されます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-testing-the-nesting-level-of-a-specific-dml-trigger"></a>A. 特定の DML トリガーの入れ子レベルを調べる  
  
```  
IF ( (SELECT TRIGGER_NESTLEVEL( OBJECT_ID('xyz') , 'AFTER' , 'DML' ) ) > 5 )  
   RAISERROR('Trigger xyz nested more than 5 levels.',16,-1)  
```  
  
### <a name="b-testing-the-nesting-level-of-a-specific-ddl-trigger"></a>B. 特定の DDL トリガーの入れ子レベルを調べる  
  
```  
IF ( ( SELECT TRIGGER_NESTLEVEL ( ( SELECT object_id FROM sys.triggers  
WHERE name = 'abc' ), 'AFTER' , 'DDL' ) ) > 5 )  
   RAISERROR ('Trigger abc nested more than 5 levels.',16,-1)  
```  
  
### <a name="c-testing-the-nesting-level-of-all-triggers-executed"></a>C. 実行されたすべてのトリガーの入れ子レベルを調べる  
  
```  
IF ( (SELECT trigger_nestlevel() ) > 5 )  
   RAISERROR  
      ('This statement nested over 5 levels of triggers.',16,-1)  
```  
  
## <a name="see-also"></a>参照  
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)  
  
  
