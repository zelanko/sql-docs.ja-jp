---
title: xp_logevent (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- xp_logevent
- xp_logevent_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- xp_logevent
ms.assetid: 7b379ad0-5b12-4d2e-9c52-62465df1fdbd
caps.latest.revision: 30
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 251dfca05a27d78618a4f3dbff5cbecd02ee5813
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34582034"
---
# <a name="xplogevent-transact-sql"></a>xp_logevent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ユーザー定義のメッセージを記録、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログ ファイルと Windows イベント ビューアでします。 クライアントに、メッセージを送信せずに警告を送信するのには、xp_logevent を使用できます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
xp_logevent { error_number , 'message' } [ , 'severity' ]  
```  
  
## <a name="arguments"></a>引数  
 *error_number*  
 50,000 より大きい、ユーザー定義のエラー番号を指定します。 最大値は 2,147,483,647 (2^31 - 1) です。  
  
 **'** *メッセージ* **'**  
 最大 2048 バイトまでの文字列を指定します。  
  
 **'** *重大度* **'**  
 INFORMATIONAL、WARNING、または ERROR のうちいずれかの文字列になります。 *重大度*オプションですが、既定値は INFORMATIONAL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 xp_logevent ではコード例に対し、次のエラー メッセージが返されます。  
  
 `The command(s) completed successfully.`  
  
## <a name="remarks"></a>コメント  
 メッセージを送信する場合[!INCLUDE[tsql](../../includes/tsql-md.md)]プロシージャ、トリガー、バッチ、および、xp_logevent ではなく RAISERROR ステートメントを使用します。 xp_logevent は、クライアントのメッセージ ハンドラーの呼び設定したりしないで@ERRORです。 Windows イベント ビューアーにされ、メッセージを書き込むため、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンス内のエラー ログ ファイル[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、RAISERROR ステートメントを実行します。  
  
## <a name="permissions"></a>アクセス許可  
 master データベースの db_owner 固定データベース ロールのメンバーシップ、または sysadmin 固定サーバー ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、メッセージおよびメッセージに渡された変数が、Windows イベント ビューアーに記録されます。  
  
```  
DECLARE @@TABNAME varchar(30), @@USERNAME varchar(30),DECLARE @@MESSAGE varchar(255);  
SET @@TABNAME = 'customers';  
SET @@USERNAME = USER_NAME();  
SELECT @@MESSAGE = 'The table ' + @@TABNAME + ' is not owned by the user   
   ' + @@USERNAME + '.';  
  
USE master;  
EXEC xp_logevent 60000, @@MESSAGE, informational;  
```  
  
## <a name="see-also"></a>参照  
 [PRINT &#40;Transact-SQL&#41;](../../t-sql/language-elements/print-transact-sql.md)   
 [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [汎用拡張ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)  
  
  
