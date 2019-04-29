---
title: sp_attachsubscription (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_attachsubscription
- sp_attachsubscription_TSQL
helpviewer_keywords:
- sp_attachsubscription
ms.assetid: b9bbda36-a46a-4327-a01e-9cd632e4791b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 47e1eec1aaa8162565f481b2d82982781e1a3c8c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62996100"
---
# <a name="spattachsubscription-transact-sql"></a>sp_attachsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  既存のサブスクリプション データベースを任意のサブスクライバーにアタッチします。 このストアド プロシージャは、master データベースで新規サブスクライバーで実行されます。  
  
> [!IMPORTANT]  
>  この機能は非推奨とされており、今後のリリースでは削除されます。 新しい開発作業でこの機能を使用しない必要があります。 パラメーター化されたフィルターを使用してパーティション分割されたマージ パブリケーションでは、パーティション スナップショットの新しい機能を使用することをお勧めします。この機能を使用すると、多数のサブスクリプションの初期化を簡単に実行できます。 詳しくは、「 [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)」をご覧ください。 パーティション分割されていないパブリケーションの場合は、バックアップを使用してサブスクリプションを初期化できます。 詳細については、「[スナップショットを使用しないトランザクション サブスクリプションの初期化](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)」を参照してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_attachsubscription [ @dbname = ] 'dbname'  
        , [ @filename = ] 'filename'  
    [ , [ @subscriber_security_mode = ] 'subscriber_security_mode' ]  
    [ , [ @subscriber_login = ] 'subscriber_login' ]  
    [ , [ @subscriber_password = ] 'subscriber_password' ]  
    [ , [ @distributor_security_mode = ] distributor_security_mode ]   
    [ , [ @distributor_login = ] 'distributor_login' ]   
    [ , [ @distributor_password = ] 'distributor_password' ]   
    [ , [ @publisher_security_mode = ] publisher_security_mode ]   
    [ , [ @publisher_login = ] 'publisher_login' ]   
    [ , [ @publisher_password = ] 'publisher_password' ]   
    [ , [ @job_login = ] 'job_login' ]   
    [ , [ @job_password = ] 'job_password' ]   
    [ , [ @db_master_key_password = ] 'db_master_key_password' ]  
```  
  
## <a name="arguments"></a>引数  
`[ @dbname = ] 'dbname'` 変換先のサブスクリプション データベースを名前を指定する文字列です。 *dbname*は**sysname**、既定値はありません。  
  
`[ @filename = ] 'filename'` プライマリ mdf ファイルの物理的な場所と名前は、(**マスター**データ ファイル)。 *ファイル名*は**nvarchar (260)**、既定値はありません。  
  
`[ @subscriber_security_mode = ] 'subscriber_security_mode'` 同期するサブスクライバーに接続するときに使用するサブスクライバーのセキュリティ モードです。 *subscriber_security_mode*は**int**、既定値は NULL です。  
  
> [!NOTE]  
>  Windows 認証を使用する必要があります。 場合*subscriber_security_mode*ない**1** (Windows 認証)、エラーが返されます。  
  
`[ @subscriber_login = ] 'subscriber_login'` 同期するサブスクライバーに接続するときに使用するサブスクライバーのログイン名です。 *subscriber_login* は **sysname** 、既定値は NULL です。  
  
> [!NOTE]  
>  このパラメーターは非推奨とされました、のみ、スクリプトの下位互換性は維持されます。 場合*subscriber_security_mode*ない**1**と*subscriber_login*が指定すると、エラーが返されます。  
  
`[ @subscriber_password = ] 'subscriber_password'` サブスクライバーのパスワードです。 *@subscriber_password* は **sysname** 、既定値は NULL です。  
  
> [!NOTE]  
>  このパラメーターは非推奨とされました、のみ、スクリプトの下位互換性は維持されます。 場合*subscriber_security_mode*ない**1**と *@subscriber_password*が指定すると、エラーが返されます。  
  
`[ @distributor_security_mode = ] distributor_security_mode` 同期するときに、ディストリビューターに接続するときに使用するセキュリティ モードです。 *distributor_security_mode*は**int**、既定値は**0**します。 **0**指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。 **1** Windows 認証を指定します。 [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @distributor_login = ] 'distributor_login'` ディストリビューターに接続して同期するときに使用するディストリビューター ログインです。 *distributor_login* 場合は必須です *distributor_security_mode* に設定されている **0** します。 *distributor_login* は **sysname** 、既定値は NULL です。  
  
`[ @distributor_password = ] 'distributor_password'` ディストリビューターのパスワードです。 *distributor_password* 場合は必須です *distributor_security_mode* に設定されている **0** します。 *distributor_password* は **sysname** 、既定値は NULL です。 値*distributor_password* 120 未満の Unicode 文字にする必要があります。  
  
> [!IMPORTANT]  
>  空白のパスワードは使用しないでください。 強力なパスワードを使用してください。 可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 スクリプト ファイルに資格情報を格納する必要がある場合は、不正アクセスを防ぐために、ファイルを保護します。  
  
`[ @publisher_security_mode = ] publisher_security_mode` 同期するときに、パブリッシャーに接続するときに使用するセキュリティ モードです。 *publisher_security_mode*は**int**、既定値は**1**します。 場合**0**を指定します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。 場合**1**、Windows 認証を指定します。 [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @publisher_login = ] 'publisher_login'` パブリッシャーに接続して同期するときに使用するログインです。 *publisher_login* は **sysname** 、既定値は NULL です。  
  
`[ @publisher_password = ] 'publisher_password'` パブリッシャーに接続するときに、パスワードが使用されます。 *publisher_password* は **sysname** 、既定値は NULL です。 値*publisher_password* 120 未満の Unicode 文字にする必要があります。  
  
> [!IMPORTANT]  
>  空白のパスワードは使用しないでください。 強力なパスワードを使用してください。 可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 スクリプト ファイルに資格情報を格納する必要がある場合は、不正アクセスを防ぐために、ファイルを保護します。  
  
`[ @job_login = ] 'job_login'` エージェントを実行する Windows アカウントのログインです。 *job_login*は**nvarchar (257)**、既定値はありません。 この Windows アカウントは常に、ディストリビューターへのエージェント接続で使用します。  
  
`[ @job_password = ] 'job_password'` エージェントを実行する Windows アカウントのパスワードです。 *job_password* は **sysname** 、既定値はありません。 値*job_password* 120 未満の Unicode 文字にする必要があります。  
  
> [!IMPORTANT]  
>  可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 スクリプト ファイルに資格情報を格納する必要がある場合は、不正アクセスを防ぐために、ファイルを保護します。  
  
`[ @db_master_key_password = ] 'db_master_key_password'` ユーザー定義データベースのマスター_キーのパスワードです。 *db_master_key_password*は**nvarchar (524)** 既定値は NULL です。 場合*db_master_key_password*が指定されていない、既存のデータベース マスター _ キーを削除して再作成されます。  
  
> [!IMPORTANT]  
>  可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 スクリプト ファイルに資格情報を格納する必要がある場合は、不正アクセスを防ぐために、ファイルを保護します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_attachsubscription**はスナップショット レプリケーション、トランザクション レプリケーション、およびマージ レプリケーションで使用します。  
  
 パブリケーションの保有期間の有効期限が切れている場合、パブリケーションに対するサブスクリプションをアタッチできません。 保有期間を過ぎたサブスクリプションを指定すると、サブスクリプションが関連付けられている場合、またはが初めて同期されるときにエラーが発生します。 パブリケーションのパブリケーションの保有期間と**0** (有効期限はありません) は無視されます。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_attachsubscription**します。  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
