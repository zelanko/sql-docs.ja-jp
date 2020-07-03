---
title: sp_procoption (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_procoption
- sp_procoption_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_procoption
ms.assetid: 6f0221bd-70b4-4b04-b15d-722235aceb3c
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8a7a4942e3109ec244cb7a16f4ef6a513b1cdcff
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85901448"
---
# <a name="sp_procoption-transact-sql"></a>sp_procoption (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  ストアド プロシージャの自動実行を設定または解除します。 自動実行に設定されているストアドプロシージャは、のインスタンスが起動されるたびに実行され [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_procoption [ @ProcName = ] 'procedure'   
    , [ @OptionName = ] 'option'   
    , [ @OptionValue = ] 'value'   
```  
  
## <a name="arguments"></a>引数  
`[ @ProcName = ] 'procedure'`オプションを設定するプロシージャの名前を指定します。 *プロシージャ*は**nvarchar (776)**,、既定値はありません。  
  
`[ @OptionName = ] 'option'`設定するオプションの名前を指定します。 *オプション*の値は**startup**だけです。  
  
`[ @OptionValue = ] 'value'`オプションを on (**true**または**on**) に設定するか、オフ (**false**または**off**) にするかを指定します。 *値*は**varchar (12)**,、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) またはエラー番号 (失敗)  
  
## <a name="remarks"></a>注釈  
 スタートアッププロシージャは、 **master**データベースに存在する必要があり、入力パラメーターまたは出力パラメーターを含めることはできません。 ストアドプロシージャの実行は、すべてのデータベースが復旧され、"復旧が完了しました" というメッセージが起動時にログに記録されると開始されます。  
  
## <a name="permissions"></a>アクセス許可  
 **sysadmin** 固定サーバー ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>例  
 次の例は、プロシージャの自動実行を設定します。  
  
```  
EXEC sp_procoption @ProcName = N'<procedure name>'   
    , @OptionName = 'startup'   
    , @OptionValue = 'on';   
```  
  
 次の例は、プロシージャの自動実行を停止します。  
  
```  
EXEC sp_procoption @ProcName = N'<procedure name>'      
    , @OptionName = 'startup'
    , @OptionValue = 'off';   
```  
  
## <a name="see-also"></a>関連項目  
 [ストアドプロシージャの実行](../../relational-databases/stored-procedures/execute-a-stored-procedure.md)  
  
  
