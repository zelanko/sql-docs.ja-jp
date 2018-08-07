---
title: SET DEADLOCK_PRIORITY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: sql-data-warehouse, database-engine, pdw, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- SET DEADLOCK_PRIORITY
- DEADLOCK_PRIORITY_TSQL
- SET_DEADLOCK_PRIORITY_TSQL
- DEADLOCK_PRIORITY
dev_langs:
- TSQL
helpviewer_keywords:
- deadlocks [SQL Server], priority settings
- DEADLOCK_PRIORITY option
- locking [SQL Server], deadlocks
- priority deadlock settings [SQL Server]
- SET DEADLOCK_PRIORITY statement
ms.assetid: 810a3a8e-3da3-4bf9-bb15-7b069685a1b6
caps.latest.revision: 35
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 35707b21917cca45075c02f4592f51ec8bdc9213
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/02/2018
ms.locfileid: "39456716"
---
# <a name="set-deadlockpriority-transact-sql"></a>SET DEADLOCK_PRIORITY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  現在のセッションが別のセッションによりデッドロックされている場合、現在のセッションが処理を継続することの相対的な重要度を指定します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
SET DEADLOCK_PRIORITY { LOW | NORMAL | HIGH | <numeric-priority> | @deadlock_var | @deadlock_intvar }  
  
<numeric-priority> ::= { -10 | -9 | -8 | … | 0 | … | 8 | 9 | 10 }  
```  
  
## <a name="arguments"></a>引数  
 LOW  
 現在のセッションがデッドロックに含まれ、デッドロック チェーンに含まれる他のセッションが、デッドロックの優先度を NORMAL または HIGH に設定しているか、-5 より大きい整数値に設定している場合、現在のセッションがデッドロックの対象になります。 他のセッションが、デッドロックの優先度を -5 より小さい整数値に設定している場合は、現在のセッションはデッドロックの対象になりません。 また、別のセッションが、デッドロックの優先度を LOW または -5 に等しい整数値に設定している場合、現在のセッションはデッドロック対象の候補になります。  
  
 NORMAL  
 デッドロック チェーンに含まれる他のセッションが、デッドロック優先度を HIGH または 0 より大きい整数値に設定している場合、現在のセッションがデッドロックの対象になります。ただし、他のセッションがデッドロックの優先度を LOW または 0 より小さい整数値に設定している場合は、現在のセッションはデッドロックの対象にはなりません。 また、別のセッションが、デッドロックの優先度を NORMAL または 0 に等しい整数値に設定している場合、現在のセッションがデッドロック対象の候補になります。 NORMAL が既定の優先度です。  
  
 HIGH  
 デッドロック チェーンに含まれる他のセッションが、デッドロック優先度を 5 より大きい整数値に設定している場合、現在のセッションがデッドロックの対象になります。また、別のセッションがデッドロックの優先度を HIGH または 5 に等しい整数値に設定している場合、現在のセッションはデッドロック対象の候補になります。  
  
 \<numeric-priority>  
 -10 ～ 10 の範囲の整数値です。デッドロックの優先度を 21 段階のレベルで示します。 デッドロック チェーンに含まれる他のセッションが、高いデッドロック優先度値で実行中の場合、現在のセッションはデッドロックの対象になりますが、他のセッションが現在のセッションの値より低いデッドロック優先度値で実行中の場合は、現在のセッションはデッドロックの対象にはなりません。 別のセッションが現在のセッションと同じデッドロック優先度値で実行中の場合は、現在のセッションがデッドロック対象の候補になります。 LOW は -5 に、NORMAL は 0 に、HIGH は 5 にマップされます。  
  
 **@** *deadlock_var*  
 デッドロックの優先度を表す文字変数を指定します。 変数は、'LOW'、'NORMAL' または 'HIGH' の値に設定する必要があります。 変数は文字列全体を十分格納できるサイズであることが必要です。  
  
 **@** *deadlock_intvar*  
 デッドロックの優先度を表す整数変数を指定します。 変数は -10 ～ 10 の範囲の整数値に設定する必要があります。  
  
## <a name="remarks"></a>Remarks  
 デッドロックは、2 つのセッションが両方とも、一方のセッションによりロックされているリソースへのアクセスを待機しているときに発生します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにより、2 つのセッションがデッドロックされていることが検出されると、セッションの 1 つをデッドロックの対象として選択することにより、デッドロックが解決します。 デッドロック対象セッションの現在のトランザクションがロールバックされて、デッドロック エラー メッセージ 1205 がクライアントに返されます。 これによりそのセッションによって保持されたすべてのロックが解除され、もう一方のセッションを進めることができるようになります。  
  
 どちらのセッションをデッドロック対象として選択するかは、各セッションのデッドロック優先度によって決まります。  
  
-   両方のセッションが同じデッドロック優先度の場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスは、デッドロック対象としてロールバックするのに負担がかからない方のセッションを選択します。 たとえば、両方のセッションがデッドロック優先度を HIGH に設定している場合、インスタンスは、ロールバックするのに負担がかからないと思われるセッションをデッドロック対象として選択します。 コストは、各トランザクションでその時点に書き込まれたログのバイト数を比較することによって決定されます。 (この値はデッドロック グラフの "使用されたログ" として参照できます)。
  
-   セッションの間でデッドロック優先度が異なる場合、一番低いデッドロック優先度のセッションがデッドロック対象として選択されます。  
  
 SET DEADLOCK_PRIORITY は、解析時ではなく実行時に設定されます。  
  
## <a name="permissions"></a>アクセス許可  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、デッドロック優先度を `LOW` に設定する変数を使用します。  
  
```  
DECLARE @deadlock_var NCHAR(3);  
SET @deadlock_var = N'LOW';  
  
SET DEADLOCK_PRIORITY @deadlock_var;  
GO  
```  
  
 次の例では、デッドロック優先度を `NORMAL` に設定します。  
  
```  
SET DEADLOCK_PRIORITY NORMAL;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [@@LOCK_TIMEOUT &#40;Transact-SQL&#41;](../../t-sql/functions/lock-timeout-transact-sql.md)   
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET LOCK_TIMEOUT &#40;Transact-SQL&#41;](../../t-sql/statements/set-lock-timeout-transact-sql.md)  
  
  
