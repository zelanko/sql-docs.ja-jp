---
title: xp_sqlmaint (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- xp_sqlmaint
- xp_sqlmaint_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- xp_sqlmaint
ms.assetid: bda66e1b-6bbd-49be-b86e-37efc920e912
caps.latest.revision: 37
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b5509b126a88ab2500fca0509789b61182af2ad2
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33256650"
---
# <a name="xpsqlmaint-transact-sql"></a>xp_sqlmaint (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  呼び出し、 **sqlmaint**ユーティリティを含む文字列を**sqlmaint**スイッチ。 **Sqlmaint**ユーティリティは、1 つまたは複数のデータベースでメンテナンス操作のセットを実行します。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
xp_sqlmaint 'switch_string'     
```  
  
## <a name="arguments"></a>引数  
 **'** *switch_string* **'**  
 含む文字列、 **sqlmaint**ユーティリティ スイッチです。 スイッチとその値は、空白で区切る必要があります。  
  
 **-しますか?** スイッチは無効**xp_sqlmaint**です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 [なし] : エラーが返されます、 **sqlmaint**ユーティリティが失敗します。  
  
## <a name="remarks"></a>解説  
 SQL Server 認証でログオンするユーザーによってこのプロシージャが呼び出される場合、 **-u"***login_id***"** と **-p"***パスワード***"** スイッチ前に付加されます*switch_string*実行前にします。 Windows 認証では、ユーザーがログオンしている場合*switch_string*を変更せずに渡される**sqlmaint**です。  
  
## <a name="permissions"></a>権限  
 **sysadmin** 固定サーバー ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、`xp_sqlmaint`呼び出し`sqlmaint`整合性チェックを実行するのには、レポート ファイルを作成および更新`msdb.dbo.sysdbmaintplan_history`です。  
  
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
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
