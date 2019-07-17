---
title: sp_getapplock (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_getapplock_TSQL
- sp_getapplock
dev_langs:
- TSQL
helpviewer_keywords:
- application locks
- sp_getapplock
ms.assetid: e1e85908-9f31-47cf-8af6-88c77e6f24c9
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f87a62e744bcd6032c58cdb3b327b747e5343d2a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68124016"
---
# <a name="spgetapplock-transact-sql"></a>sp_getapplock (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  アプリケーション リソースのロックを配置します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_getapplock [ @Resource = ] 'resource_name' ,  
     [ @LockMode = ] 'lock_mode'   
     [ , [ @LockOwner = ] 'lock_owner' ]   
     [ , [ @LockTimeout = ] 'value' ]  
     [ , [ @DbPrincipal = ] 'database_principal' ]  
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 [ @Resource=] '*resource_name*'  
 ロック リソースを識別する名前を指定する文字列。 アプリケーション側では、リソース名が一意になるよう管理されている必要があります。 指定した名前は内部的にハッシュされ、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ロック マネージャーに格納できる値に変換されます。 *resource_name*は**nvarchar (255)** 既定値はありません。 リソース文字列がより長い場合**nvarchar (255)** に切り捨てられます**nvarchar (255)** します。  
  
 *resource_name*はバイナリ比較し、つまり現在のデータベースの照合順序の設定に関係なく大文字小文字を区別します。  
  
> [!NOTE]  
>  アプリケーション ロックが取得されると、プレーン テキストで抽出できるのは最初の 32 文字のみとなり、残りの部分はハッシュされます。  
  
 [ @LockMode=] '*lock_mode*'  
 特定のリソースに対して取得されるロック モードです。 *lock_mode* は **nvarchar (32)** 、既定値はありません。 値には、次のいずれかを指定できます。**共有**、 **Update**、 **IntentShared**、 **IntentExclusive**、または**排他**します。  
  
 [ @LockOwner=] '*lock_owner*'  
 ロックの所有者を指定します。これはロックが要求されたときの *lock_owner* 値です。 *lock_owner* は **nvarchar (32)** です。 この値は **Transaction** (既定値) または **Session** のいずれかです。 ときに、 *lock_owner*値は**トランザクション**により、既定または明示的に指定すると、sp_getapplock 必要がありますから実行するトランザクション内で。  
  
 [ @LockTimeout=] '*値*'  
 ロックのタイムアウト値 (ミリ秒単位) です。 既定値はによって返される値と同じ@LOCK_TIMEOUTします。 要求をすぐに許可できない場合に、ロック要求がロックの待機ではなく-1 を返すコードを返す必要がありますかを示す、0 を指定します。  
  
 [ @DbPrincipal=] '*database_principal*'  
 ユーザー、ロール、またはデータベース内のオブジェクトへのアクセス許可を持つアプリケーション ロールです。 関数の呼び出し元のメンバーである必要があります*database_principal*dbo、または、db_owner 固定データベース ロールの関数を呼び出します。 既定値はパブリックです。  
  
## <a name="return-code-values"></a>リターン コードの値  
 \>= 0 (成功) または < 0 (失敗)  
  
|[値]|結果|  
|-----------|------------|  
|0|ロックが同時に許可されました。|  
|1|互換性のない他のロックが解放されるのを待機してから、ロックが許可されました。|  
|-1|ロック要求がタイムアウトしました。|  
|-2|ロック要求が取り消されました。|  
|-3|ロック要求がデッドロックの対象になりました。|  
|-999 =|パラメーターの検証またはその他の呼び出しエラーを示します。|  
  
## <a name="remarks"></a>コメント  
 リソースに設定されたロックは、現在のトランザクションまたは現在のセッションに関連付けられます。 現在のトランザクションに関連付けられたロックは、トランザクションがコミットまたはロールバックされるときに解放されます。 セッションがログアウトしたときに、セッションに関連付けられたロックは解放されます。サーバーが何らかの理由でシャット ダウンすると、すべてのロックが解放されます。  
  
 Sp_getapplock によって作成されるロック リソースは、セッションの現在のデータベースに作成されます。 各ロック リソースは、値の組み合わせによって識別されます。  
  
-   ロック リソースを含むデータベースのデータベース ID。  
  
-   @DbPrincipal パラメーターで指定されるデータベース プリンシパル  
  
-   指定されるロック名、@Resourceパラメーター。  
  
 @DbPrincipal パラメーターで指定されるデータベース プリンシパルのメンバーだけが、そのプリンシパルを指定しているアプリケーション ロックを取得できます。 Dbo および db_owner ロールのメンバーは、暗黙的にすべてのロールのメンバーと見なされます。  
  
 ロックは、sp_releaseapplock で明示的に解放できます。 アプリケーションで、同じロック リソースに対して sp_getapplock が複数回呼び出される場合は、同じ回数だけ sp_releaseapplock を呼び出して、ロックを解放する必要があります。  ロックを開いたときに、`Transaction`ロックの所有者、トランザクションがコミットまたはロールバック時にロックが解放されます。
  
 sp_getapplock が同じロック リソースに対して複数回呼び出されても、その要求で指定されるロック モードが既存のモードと異なる場合、リソースでは 2 つのロック モードが混在することになります。 このため、ロック モードは多くの場合、既存のモードと新しく要求されたモードのうち、より強力なモードに昇格します。 この強力なロック モードは、その時点より前にロックの解放呼び出しが行われた場合でも、ロックが最終的に解放されるまで保持されます。 たとえば、呼び出しの次の順序でリソースに保持されて`Exclusive`モードではなく`Shared`モード。  
  
```  
USE AdventureWorks2012;  
GO  
BEGIN TRANSACTION;  
DECLARE @result int;  
EXEC @result = sp_getapplock @Resource = 'Form1',   
               @LockMode = 'Shared';  
EXEC @result = sp_getapplock @Resource = 'Form1',   
               @LockMode = 'Exclusive';  
EXEC @result = sp_releaseapplock @Resource = 'Form1';  
COMMIT TRANSACTION;  
GO  
```  
  
 アプリケーション ロック時にデッドロックが発生すると、アプリケーション ロックを要求したトランザクションはロールバックされません。 戻り値の結果として必要になる任意のロールバックを手動で行う必要があります。 したがって、ある特定の値 (たとえば -3) が返された場合に ROLLBACK TRANSACTION または代替の操作が開始できるように、コードにはエラー チェックを含めることをお勧めします。  
  
 以下に例を示します。  
  
```  
USE AdventureWorks2012;  
GO  
BEGIN TRANSACTION;  
DECLARE @result int;  
EXEC @result = sp_getapplock @Resource = 'Form1',   
               @LockMode = 'Exclusive';  
IF @result = -3  
BEGIN  
    ROLLBACK TRANSACTION;  
END  
ELSE  
BEGIN  
    EXEC @result = sp_releaseapplock @Resource = 'Form1';  
    COMMIT TRANSACTION;  
END;  
GO  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、現在のデータベース ID によってリソースが限定されます。 そのため、別のデータベースで同じパラメーター値を使用しても、sp_getapplock を実行している場合、異なるリソースに個別のロックとなります。  
  
 sys.dm_tran_locks 動的管理ビューまたは sp_lock システム ストアド プロシージャを使ってロック情報を検証するか、[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使ってロックを監視してください。  
  
## <a name="permissions"></a>アクセス許可  
 public ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、現在のトランザクションに関連付けられている共有ロックを、`Form1` データベースのリソース `AdventureWorks2012` に設定します。  
  
```  
USE AdventureWorks2012;  
GO  
BEGIN TRAN;  
DECLARE @result int;  
EXEC @result = sp_getapplock @Resource = 'Form1',   
               @LockMode = 'Shared';  
COMMIT TRAN;  
GO  
```  
  
 次の例を示す`dbo`as データベース プリンシパル。  
  
```  
BEGIN TRAN;  
EXEC sp_getapplock @DbPrincipal = 'dbo', @Resource = 'AdventureWorks2012',   
     @LockMode = 'Shared';  
COMMIT TRAN;  
GO  
```  
  
## <a name="see-also"></a>関連項目  
 [APPLOCK_MODE &#40;TRANSACT-SQL&#41;](../../t-sql/functions/applock-mode-transact-sql.md)   
 [APPLOCK_TEST &#40;TRANSACT-SQL&#41;](../../t-sql/functions/applock-test-transact-sql.md)   
 [sp_releaseapplock &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-releaseapplock-transact-sql.md)  
  
  
