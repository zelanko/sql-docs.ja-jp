---
title: "sp_addlinkedsrvlogin (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_addlinkedsrvlogin_TSQL
- sp_addlinkedsrvlogin
dev_langs: TSQL
helpviewer_keywords: sp_addlinkedsrvlogin
ms.assetid: eb69f303-1adf-4602-b6ab-f62e028ed9f6
caps.latest.revision: "41"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: a4a55d2128cdba654ce9e753ac1cdcebd8f0ad8d
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="spaddlinkedsrvlogin-transact-sql"></a>sp_addlinkedsrvlogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  作成または更新のローカル インスタンス上のログインの間のマッピング[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]とリモート サーバー上のセキュリティ アカウント。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_addlinkedsrvlogin [ @rmtsrvname = ] 'rmtsrvname'   
     [ , [ @useself = ] 'TRUE' | 'FALSE' | NULL ]   
     [ , [ @locallogin = ] 'locallogin' ]   
     [ , [ @rmtuser = ] 'rmtuser' ]   
     [ , [ @rmtpassword = ] 'rmtpassword' ]   
```  
  
## <a name="arguments"></a>引数  
 [ @rmtsrvname  **=**  ] **'***rmtsrvname***'**  
 ログイン マッピングの対象となるリンク サーバーの名前を指定します。 *rmtsrvname*は**sysname**、既定値はありません。  
  
 [ @useself  **=**  ] **'**TRUE**'** |'FALSE' |' NULL'  
 接続するかどうかを判断*rmtsrvname*のローカル ログインの権限を借用または明示的にログインとパスワードを送信します。 データ型は**varchar (**8**)**、既定値は TRUE です。  
  
 TRUE の値は、ログインがへの接続に自身の資格情報を使用することを指定します*rmtsrvname*で、 *rmtuser*と*rmtpassword*引数は無視されます。 FALSE を指定する、 *rmtuser*と*rmtpassword*引数がへの接続に使用される*rmtsrvname* 、指定された*locallogin*. 場合*rmtuser*と*rmtpassword*も、NULL でないログインまたはパスワードに設定が、リンク サーバーへの接続に使用します。  
  
 [ @locallogin  **=**  ] **'***locallogin***'**  
 ローカル サーバー上のログインを指定します。 *locallogin*は**sysname**、既定値は NULL です。 NULL では、このエントリに接続するすべてのローカル ログインに適用されることを示す*rmtsrvname*です。 NULL 以外の場合*locallogin*できます、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインまたは Windows ログインします。 Windows ログインが与えられているへのアクセス[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]いずれかを直接または Windows グループのメンバーシップを介してアクセスを許可します。  
  
 [ @rmtuser  **=**  ] **'***rmtuser***'**  
 接続に使用するリモート ログイン*rmtsrvname*とき@useselfは FALSE です。 インスタンスがリモート サーバーの場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Windows 認証を使用しない*rmtuser*は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインします。 *rmtuser*は**sysname**、既定値は NULL です。  
  
 [ @rmtpassword  **=**  ] **'***rmtpassword***'**  
 パスワードに関連付けられている*rmtuser*です。 *rmtpassword*は**sysname**、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 ユーザーがローカル サーバーにログインして、リンク サーバー上のテーブルにアクセスする分散クエリを実行する場合、ローカル サーバーは、目的のテーブルにアクセスするために、ユーザーの代理でリンク サーバーにログインする必要があります。 sp_addlinkedsrvlogin を使用して、ローカル サーバーがリンク サーバーへのログインに使用するログイン資格情報を指定します。  
  
> [!NOTE]  
>  リンク サーバー上のテーブルを使用するときに最善のクエリ プランを作成するには、クエリ プロセッサがリンク サーバーからデータ分布統計情報を取得する必要があります。 テーブルの列に対するユーザーの権限が制限されていると、必要な統計情報を取得できるだけの十分な権限がないためにクエリ プランが非効率になり、高いパフォーマンスが得られない場合があります。 リンク サーバーが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスである場合、利用可能な統計情報をすべて取得するには、ユーザーがテーブルを所有しているか、リンク サーバーの固定サーバー ロール sysadmin、固定データベース ロール db_owner、または固定データベース ロール db_ddladmin のメンバーである必要があります。 SQL Server 2012 SP1 では、統計を取得するための権限の制限が変更され、SELECT 権限を持つユーザーは DBCC SHOW_STATISTICS で入手可能な統計にアクセスできます。 詳細については、アクセス許可のセクションを参照してください。 [DBCC SHOW_STATISTICS &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md).  
  
 sp_addlinkedserver を実行することにより、ローカル サーバー上のすべてのログインとリンク サーバー上のリモート ログインとの間の既定のマッピングが自動的に作成されます。 既定のマッピングでは、ことを示す[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインの代わりに、リンク サーバーに接続するときに、ローカル ログインのユーザーの資格情報を使用します。 これで sp_addlinkedsrvlogin を実行する@useselfに設定**true**リンク サーバーをローカル ユーザー名を指定せずにします。 既定のマッピングを変更するときや、特定のローカル ログインに対応する新しいマッピングを追加するときだけ sp_addlinkedsrvlogin を使用します。 既定のマッピングまたはその他のマッピングを削除するには、sp_droplinkedsrvlogin を使用します。  
  
 次のすべての条件が成立する場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、sp_addlinkedsrvlogin を使用してあらかじめ決められたログイン マッピングを作成する代わりに、クエリを実行するユーザーの Windows セキュリティ資格情報 (Windows のログイン名とパスワード) を自動的に使用して、リンク サーバーに接続できます。  
  
-   ユーザーが接続されている[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Windows 認証モードを使用します。  
  
-   クライアントと送信側サーバーで、セキュリティ アカウント委任が利用可能になっている。  
  
-   たとえば Windows 上で実行されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のように、プロバイダーが Windows 認証モードをサポートしている。  
  
> [!NOTE]  
>  委任は、単一ホップのシナリオでは有効にする必要はありませんが、複数ホップのシナリオでは有効にする必要があります。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカル インスタンス上で sp_addlinkedsrvlogin を実行して定義されたマッピングを、リンク サーバーが使用して認証を行った後は、ローカル サーバーではなく、リンク サーバーがリモート データベース内の個々のオブジェクトに対する権限を規定します。  
  
 ユーザー定義のトランザクション内から sp_addlinkedsrvlogin を実行することはできません。  
  
## <a name="permissions"></a>Permissions  
 サーバーに対する ALTER ANY LOGIN 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-connecting-all-local-logins-to-the-linked-server-by-using-their-own-user-credentials"></a>A. ログイン自身のユーザー資格情報を使用してすべてのローカル ログインをリンク サーバーに接続する  
 次の例では、ローカル サーバーにすべてのログインがリンク サーバーに接続を通じてことを確認へのマッピングを`Accounts`自身のユーザー資格情報を使用しています。  
  
```  
EXEC sp_addlinkedsrvlogin 'Accounts';  
```  
  
 または  
  
```  
EXEC sp_addlinkedsrvlogin 'Accounts', 'true';  
```  
  
> [!NOTE]  
>  個々のログイン用に作成された明示的なマッピングがある場合、それらのマッピングは、リンク サーバーに存在する可能性のあるどのグローバル マッピングよりも優先されます。  
  
### <a name="b-connecting-a-specific-login-to-the-linked-server-by-using-different-user-credentials"></a>B. 別のユーザー資格情報を使用して特定のログインをリンク サーバーに接続する  
 次の例は、ことを確認して、マッピングを作成した Windows ユーザー `Domain\Mary` 、リンク サーバーに接続`Accounts`、ログインを使用して`MaryP`とパスワード`d89q3w4u`です。  
  
```  
EXEC sp_addlinkedsrvlogin 'Accounts', 'false', 'Domain\Mary', 'MaryP', 'd89q3w4u';  
```  
  
> [!IMPORTANT]  
>  この例では、Windows 認証は使用されていません。 したがって、パスワードは暗号化されずに送信されます。 パスワードは、ディスク、バックアップ、およびログファイルに保存されたデータ ソース定義やスクリプトで参照できます。 この種類の接続では、システム管理者のパスワードを使用しないでください。 特定のユーザー環境のセキュリティについては、ネットワーク管理者に相談してください。  
  
## <a name="see-also"></a>参照  
 [リンク サーバーのカタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/linked-servers-catalog-views-transact-sql.md)   
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_droplinkedsrvlogin &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-droplinkedsrvlogin-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
