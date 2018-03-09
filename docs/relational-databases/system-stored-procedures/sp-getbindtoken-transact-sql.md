---
title: "sp_getbindtoken (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_getbindtoken
- sp_getbindtoken_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_getbindtoken
ms.assetid: 5db87d77-85fa-45a3-a23a-3ea500f9a5ac
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 58c73d303ac8fdcd8e9d4acf9f937538c3df816c
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="spgetbindtoken-transact-sql"></a>sp_getbindtoken (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  トランザクションの一意識別子を返します。 この一意識別子は、sp_bindsession を使用してセッションをバインドするために使用する文字列です。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]代わりに、複数のアクティブな結果セット (MARS) または分散トランザクションを使用してください。 詳細については、次を参照してください。[複数のアクティブな結果セットの使用 &#40;です。MARS &#41;](../../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md).  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_getbindtoken [@out_token =] 'return_value' OUTPUT   
```  
  
## <a name="arguments"></a>引数  
 [@out_token=]'*return_value*'  
 セッションのバインドに使用するトークンです。 *return_value*は**varchar (255)**既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 なし  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 アクティブなトランザクション内部ストアド プロシージャが実行される場合にのみ、sp_getbindtoken は有効なトークンを返します。 それ以外の場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)]エラー メッセージが返されます。 例:  
  
```  
-- Declare a variable to hold the bind token.  
-- No active transaction.  
DECLARE @bind_token varchar(255);  
-- Trying to get the bind token returns an error 3921.  
EXECUTE sp_getbindtoken @bind_token OUTPUT;  
Server: Msg 3921, Level 16, State 1, Procedure sp_getbindtoken, Line 4  
Cannot get a transaction token if there is no transaction active.  
Reissue the statement after a transaction has been started.  
```  
  
 Sp_getbindtoken を使用して、開いているトランザクション内の分散トランザクションの接続を参加させるときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]同じトークンを返します。 例:  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @bind_token varchar(255);  
  
BEGIN TRAN;  
  
EXECUTE sp_getbindtoken @bind_token OUTPUT;  
SELECT @bind_token AS Token;  
  
BEGIN DISTRIBUTED TRAN;  
  
EXECUTE sp_getbindtoken @bind_token OUTPUT;  
SELECT @bind_token AS Token;  
```  
  
 両方`SELECT`ステートメントは、同じトークンを返します。  
  
```  
Token  
-----  
PKb'gN5<9aGEedk_16>8U=5---/5G=--  
(1 row(s_) affected)  
  
Token  
-----  
PKb'gN5<9aGEedk_16>8U=5---/5G=--  
(1 row(s_) affected)  
```  
  
 sp_bindsession でバインド トークンを使用して、新規セッションを同じトランザクションにバインドできます。 バインド トークンが有効での各インスタンス内でローカルにのみ、[!INCLUDE[ssDE](../../includes/ssde-md.md)]複数のインスタンス間で共有することはできません。  
  
 バインド トークンを取得して渡すには、sp_getbindtoken を実行してから sp_bindsession を実行して、同じロック領域を共有します。 バインド トークンの取得後は、sp_bindsession を正常に実行できます。  
  
> [!NOTE]  
>  拡張ストアド プロシージャからバインド トークンを取得するときは、srv_getbindtoken オープン データ サービス API を使用することをお勧めします。  
  
## <a name="permissions"></a>Permissions  
 public ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 この例では、バインド トークンを取得し、そのバインド トークンの名前を表示します。  
  
```  
DECLARE @bind_token varchar(255);  
BEGIN TRAN;  
EXECUTE sp_getbindtoken @bind_token OUTPUT;  
SELECT @bind_token AS Token;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Token`  
  
 `----------------------------------------------------------`  
  
 `\0]---5^PJK51bP<1F<-7U-]ANZ`  
  
## <a name="see-also"></a>参照  
 [sp_bindsession &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-bindsession-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [srv_getbindtoken &#40;です。拡張ストアド プロシージャ API &#41;](../../relational-databases/extended-stored-procedures-reference/srv-getbindtoken-extended-stored-procedure-api.md)  
  
  
