---
title: xp_sqlmaint (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- xp_sqlmaint
- xp_sqlmaint_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- xp_sqlmaint
ms.assetid: bda66e1b-6bbd-49be-b86e-37efc920e912
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9948767ca0eca5721207079f978987142653e9c2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68091907"
---
# <a name="xp_sqlmaint-transact-sql"></a>xp_sqlmaint (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **Sqlmaint**スイッチを含む文字列を使用して**sqlmaint**ユーティリティを呼び出します。 **Sqlmaint**ユーティリティは、1つまたは複数のデータベースに対して一連のメンテナンス操作を実行します。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
xp_sqlmaint 'switch_string'     
```  
  
## <a name="arguments"></a>引数  
 **'** *switch_string* **'**  
 **Sqlmaint**ユーティリティスイッチを含む文字列です。 スイッチとその値は、空白で区切る必要があります。  
  
 **-?** スイッチは**xp_sqlmaint**に対して無効です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 [なし] : **Sqlmaint**ユーティリティが失敗した場合は、エラーが返されます。  
  
## <a name="remarks"></a>解説  
 SQL Server 認証を使用してログオンしたユーザーがこのプロシージャを呼び出すと、 **-U "***login_id***"** および **-P "***password***"** スイッチが、実行前に*switch_string*に付加されます。 ユーザーが Windows 認証でログオンしている場合、 *switch_string*は**sqlmaint**に変更されることなく渡されます。  
  
## <a name="permissions"></a>アクセス許可  
 
  **sysadmin** 固定サーバー ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>例  
 次の例では`xp_sqlmaint` 、 `sqlmaint`を呼び出して整合性チェックを実行し、レポートファイルを`msdb.dbo.sysdbmaintplan_history`作成して、を更新します。  
  
```  
EXEC xp_sqlmaint '-D AdventureWorks2012 -PlanID 02A52657-D546-11D1-9D8A-00A0C9054212   
   -Rpt "C:\Program Files\Microsoft SQL Server\MSSQL\LOG\DBMaintPlan2.txt" -WriteHistory  -CkDB -CkAl';   
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
The command(s) executed successfully.  
```  
  
## <a name="see-also"></a>参照  
 [sqlmaint ユーティリティ](../../tools/sqlmaint-utility.md)   
 [システムストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
