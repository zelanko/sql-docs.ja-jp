---
title: sp_procoption (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_procoption
- sp_procoption_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_procoption
ms.assetid: 6f0221bd-70b4-4b04-b15d-722235aceb3c
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: f5e899ab87ee7ebb6e240bb38e3330bc44f751e1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spprocoption-transact-sql"></a>sp_procoption (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ストアド プロシージャの自動実行を設定または解除します。 ストアド プロシージャは、自動実行の実行に毎回のインスタンスの設定を[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が開始します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_procoption [ @ProcName = ] 'procedure'   
    , [ @OptionName = ] 'option'   
    , [ @OptionValue = ] 'value'   
```  
  
## <a name="arguments"></a>引数  
 [  **@ProcName =** ] **'***プロシージャ***'**  
 オプションを設定する対象のプロシージャの名前です。 *プロシージャ*は**nvarchar (776)**、既定値はありません。  
  
 [  **@OptionName =** ] **'***オプション***'**  
 設定するオプションの名前です。 唯一の値*オプション*は**スタートアップ**です。  
  
 [  **@OptionValue =** ] **'***値***'**  
 オプションを設定するかどうか (**true**または**で**)] または [オフ (**false**または**オフ**)。 *値*は**varchar (12)**、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 成功した場合は 0 を、失敗した場合はエラー番号をそれぞれ返します。  
  
## <a name="remarks"></a>解説  
 スタートアップ プロシージャがである必要があります、**マスター**データベースし、入力または出力パラメーターを含めることはできません。 ストアド プロシージャの実行は、すべてのデータベースが復旧され、スタートアップ時に "復元が完了しました" というメッセージがログに記録されると開始されます。  
  
## <a name="permissions"></a>権限  
 **sysadmin** 固定サーバー ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例は、プロシージャの自動実行を設定します。  
  
```  
EXEC sp_procoption @ProcName = '<procedure name>'   
    , @OptionName = ] 'startup'   
    , @OptionValue = 'on';   
```  
  
 次の例は、プロシージャの自動実行を停止します。  
  
```  
EXEC sp_procoption @ProcName = '<procedure name>'   
    , @OptionValue = 'off';   
```  
  
## <a name="see-also"></a>参照  
 [ストアド プロシージャの実行](../../relational-databases/stored-procedures/execute-a-stored-procedure.md)  
  
  
