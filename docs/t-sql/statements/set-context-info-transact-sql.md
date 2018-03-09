---
title: "SET CONTEXT_INFO (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET_CONTEXT_INFO_TSQL
- SET CONTEXT_INFO
dev_langs:
- TSQL
helpviewer_keywords:
- context information [SQL Server]
- CONTEXT_INFO option
- SET CONTEXT_INFO statement
ms.assetid: a0b7b9f3-dbda-4350-a274-bd9ecd5c0a74
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 4a93e9f40690f37c0c161c635aea95589d47ef1e
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="set-contextinfo-transact-sql"></a>SET CONTEXT_INFO (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  128 バイト以内のバイナリ情報を現在のセッションまたは接続に関連付けます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
SET CONTEXT_INFO { binary_str | @binary_var }  
```  
  
## <a name="arguments"></a>引数  
 *binary_str*  
 **バイナリ**定数、またはに暗黙的に変換できる定数**バイナリ**、現在のセッションまたは接続に関連付ける。  
  
 **@***binary_var*  
 **Varbinary**または**バイナリ**を現在のセッションまたは接続に関連付けるコンテキスト値を保持する変数。  
  
## <a name="remarks"></a>解説  
 現在のセッションのコンテキスト情報を取得するには、CONTEXT_INFO 関数を使用することをお勧めします。 セッション コンテキスト情報にも格納、 **context_info**次のシステム ビューの列。  
  
-   **sys.dm_exec_requests**  
  
-   **sys.dm_exec_sessions**  
  
-   **sys.sysprocesses**  
  
 SET CONTEXT_INFO は、ユーザー定義関数では指定できません。 値を保持するビューでは NULL 値が許可されないため、SET CONTEXT_INFO に NULL 値は指定できません。  
  
 SET CONTEXT_INFO には、定数または変数名以外の式を指定できません。 関数呼び出しの結果にコンテキスト情報を設定、内の関数呼び出しの結果を最初に含める必要があります、**バイナリ**または**varbinary**変数。  
  
 ストアド プロシージャまたはトリガーの中で SET CONTEXT_INFO を実行する場合は、他の SET ステートメントの場合とは異なり、コンテキスト情報に設定された新しい値がストアド プロシージャまたはトリガーの終了後も保持されます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-setting-context-information-by-using-a-constant"></a>A. 定数を使用してコンテキスト情報を設定する  
 次の例で`SET CONTEXT_INFO`を値を設定し、結果を表示します。 `sys.dm_exec_sessions` のクエリを実行するには SELECT および VIEW SERVER STATE の権限が必要ですが、CONTEXT_INFO 関数を使用するのにこれらの権限は必要ありません。  
  
```  
SET CONTEXT_INFO 0x01010101;  
GO  
SELECT context_info   
FROM sys.dm_exec_sessions  
WHERE session_id = @@SPID;  
GO  
```  
  
### <a name="b-setting-context-information-by-using-a-function"></a>B. 関数を使用してコンテキスト情報を設定する  
 次の例で、関数から値必要があります最初に配置する、コンテキスト値を設定する関数の出力を使用して、**バイナリ**変数。  
  
```  
DECLARE @BinVar varbinary(128);  
SET @BinVar = CAST(REPLICATE( 0x20, 128 ) AS varbinary(128) );  
SET CONTEXT_INFO @BinVar;  
  
SELECT CONTEXT_INFO() AS MyContextInfo;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [sys.dm_exec_requests &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)   
 [sys.dm_exec_sessions &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)   
 [CONTEXT_INFO &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/context-info-transact-sql.md)  
  
  
