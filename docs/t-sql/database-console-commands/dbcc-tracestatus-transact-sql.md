---
title: "DBCC TRACESTATUS (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/17/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|database-console-commands
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DBCC_TRACESTATUS_TSQL
- DBCC TRACESTATUS
- TRACESTATUS_TSQL
- TRACESTATUS
dev_langs:
- TSQL
helpviewer_keywords:
- global trace flags [SQL Server]
- status information [SQL Server], trace flags
- trace flags [SQL Server], status information
- DBCC TRACESTATUS statement
- session trace flags [SQL Server]
- displaying trace flag status
ms.assetid: 9be51199-78b4-4b87-ae6e-557246b7e29a
caps.latest.revision: 36
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 75d78069427891cfab6f7aaef7192d498912611a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="dbcc-tracestatus-transact-sql"></a>DBCC TRACESTATUS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

トレース フラグの状態を表示します。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
DBCC TRACESTATUS ( [ [ trace# [ ,...n ] ] [ , ] [ -1 ] ] )   
[ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>引数  
*trace #*  
状態を表示するトレース フラグの番号です。 場合*trace #*-1 が指定されていないと、セッションを有効になっているすべてのトレース フラグが表示されます。
  
*n*  
複数のトレース フラグを指定できることを示すプレースホルダーです。
  
-1  
グローバルに有効化されているトレース フラグの状態を表示します。 -1 がなく指定されている場合*trace #*、有効になっているすべてのグローバル トレース フラグが表示されます。
  
WITH NO_INFOMSGS  
重大度レベル 0 から 10 のすべての情報メッセージを表示しないようにします。
  
## <a name="result-sets"></a>結果セット  
次の表では、結果セットに表示される情報について説明します。
  
|列名|Description|  
|---|---|
|**トレース フラグ**|トレース フラグの名前です。|  
|**[状態]**|トレース フラグがグローバルまたはセッションごとに ON または OFF に設定されているかどうかを示します。<br /><br /> 1 = ON <br /><br /> 0 = OFF|  
|**グローバル**|トレース フラグがグローバルに設定されているかどうかを示します。<br /><br /> 1 = True<br /><br /> 0 = False|  
|**セッション**|トレース フラグがセッションに対して設定されているかどうかを示します。<br /><br /> 1 = True<br /><br /> 0 = False|  
  
DBCC TRACESTATUS はトレース フラグ番号の列と状態の列を返します。 これは、トレース フラグがオン (1)、オフ (0) のどちらになっているかを示します。 トレース フラグ番号は、いずれかの列ヘッダー **Global Trace Flag**または**Session Trace Flag**グローバルまたはセッション トレース フラグの状態をチェックするかどうかに応じて、します。
  
## <a name="remarks"></a>解説  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、トレース フラグの 2 種類があります: セッションとグローバルです。 セッション トレース フラグは、1 つの接続についてアクティブで、その接続に対してのみ表示可能です。 グローバル トレース フラグは、サーバー レベルで設定され、サーバー上のすべての接続に対して表示可能です。
  
## <a name="permissions"></a>Permissions  
ロール **public** のメンバーシップが必要です。
  
## <a name="examples"></a>使用例  
次の例は、現在グローバルに有効化されているすべてのトレース フラグの状態を表示します。
  
```sql  
DBCC TRACESTATUS(-1);  
GO  
```  
  
次の例は、トレース フラグの状態を表示`2528`と`3205`です。
  
```sql  
DBCC TRACESTATUS (2528, 3205);  
GO  
```  
  
次の例を表示するかどうかトレース フラグ`3205`がグローバルに有効になっています。
  
```sql  
DBCC TRACESTATUS (3205, -1);  
GO  
```  
  
次の例では、現在のセッションに対して有効になっているすべてのトレース フラグを一覧表示します。
  
```sql  
DBCC TRACESTATUS();  
GO  
```  
  
## <a name="see-also"></a>参照  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[DBCC TRACEOFF &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-traceoff-transact-sql.md)  
[DBCC TRACEON &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-traceon-transact-sql.md)  
[トレース フラグ &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)
  
  

