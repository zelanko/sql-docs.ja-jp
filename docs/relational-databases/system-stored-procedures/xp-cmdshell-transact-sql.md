---
title: xp_cmdshell (トランザクション-SQL) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/30/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- xp_cmdshell
- xp_cmdshell_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- xp_cmdshell
ms.assetid: 18935cf4-b320-4954-b6c1-e007fcefe358
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2ce32fc31373077418e77d31ce064d60e23f1b24
ms.sourcegitcommit: fc5b757bb27048a71bb39755648d5cefe25a8bc6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2020
ms.locfileid: "80402689"
---
# <a name="xp_cmdshell-transact-sql"></a>xp_cmdshell (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Windows のコマンド シェルを起動し、実行用の文字列に渡します。 出力は、テキストの行として返されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
xp_cmdshell { 'command_string' } [ , no_output ]  
```  
  
## <a name="arguments"></a>引数  
 **'** *command_string* **'**  
 オペレーティング システムに渡されるコマンドを含む文字列です。 *command_string*は、デフォルト値を指定しない**varchar(8000)** または**nvarchar(4000) です**。 *command_stringは*、二重引用符のセットを複数含めることはできません。 *command_string*で参照されるファイル パスまたはプログラム名にスペースが含まれている場合は、単一引用符が必要です。 埋め込みスペースで問題が発生する場合は、回避策として FAT 8.3 ファイル名の使用を検討してください。  
  
 **no_output**  
 クライアントに出力を返さないことを指定する省略可能なパラメーターです。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 次の `xp_cmdshell` ステートメントを実行すると、現在のディレクトリの一覧が返されます。  
  
```  
EXEC xp_cmdshell 'dir *.exe';  
GO  
```  
  
 行は**nvarchar(255)** 列に返されます。 **no_output**オプションを使用すると、次の項目だけが返されます。  
  
```  
The command(s) completed successfully.  
```  
  
## <a name="remarks"></a>解説  
 **xp_cmdshell**によって生成された Windows プロセスは、サービス アカウントと同[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]じセキュリティ権限を持ちます。  
  
 **xp_cmdshell**は同期的に動作します。 コマンド シェル コマンドが完了するまで、制御は呼び出し元に返されません。  
  
 **xp_cmdshell**は、 ポリシー ベースの管理を使用するか、**または sp_configure**を実行して有効または無効にできます。 詳細については、「[セキュリティ上の構成](../../relational-databases/security/surface-area-configuration.md)と[xp_cmdshellサーバー構成オプション](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md)」を参照してください。  
  
> [!IMPORTANT]
>  **xp_cmdshell**がバッチ内で実行され、エラーが返された場合、バッチは失敗します。
  
## <a name="xp_cmdshell-proxy-account"></a>プロキシ アカウントxp_cmdshell  
 **sysadmin**固定サーバー ロールのメンバではないユーザーによって呼び出された場合 **、xp_cmdshell**は **、##xp_cmdshell_proxy_account##** という名前の資格情報に格納されているアカウント名とパスワードを使用して Windows に接続します。 このプロキシ資格情報が存在しない場合 **、xp_cmdshell**は失敗します。  
  
 プロキシ アカウントの資格情報は、 **sp_xp_cmdshell_proxy_account**を実行して作成できます。 このストアド プロシージャは、Windows のユーザー名とパスワードを引数にとります。 たとえば、次のコマンドは、Windows パスワード`SHIPPING\KobeR``sdfh%dkc93vcMt0`を持つ Windows ドメイン ユーザーのプロキシ資格情報を作成します。  
  
```  
EXEC sp_xp_cmdshell_proxy_account 'SHIPPING\KobeR','sdfh%dkc93vcMt0';  
```  
  
 詳細については、「 [&#40;sql&#41;のsp_xp_cmdshell_proxy_account ](../../relational-databases/system-stored-procedures/sp-xp-cmdshell-proxy-account-transact-sql.md)」を参照してください。  
  
## <a name="permissions"></a>アクセス許可  
 悪意のあるユーザーは**xp_cmdshell**を使用して特権を昇格しようとする場合があるため **、既定ではxp_cmdshell**は無効になっています。 **sp_configure**または**ポリシーベースの管理**を使用して有効にします。 詳細については、「 [xp_cmdshell サーバー構成オプション](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md)」を参照してください。  
  
 最初に有効にした場合 **、xp_cmdshell**実行するには CONTROL SERVER アクセス許可が必要であり **、xp_cmdshell**によって作成された[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Windows プロセスはサービス アカウントと同じセキュリティ コンテキストを持ちます。 多[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]くの場合、サービス アカウントには、 によって作成されたプロセスによって実行される作業に必要なアクセス許可よりも多くのアクセス許可**xp_cmdshell。** セキュリティを強化するには **、xp_cmdshell**へのアクセスを、高い特権を持つユーザーに制限する必要があります。  
  
 管理者以外のユーザーが**xp_cmdshell**を使用できるようにし[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、権限の低いアカウントのセキュリティ トークンを使用して子プロセスを作成できるようにするには、次の手順を実行します。  
  
1.  プロセスで必要な権限が最も少ない Windows ローカル ユーザー アカウントまたはドメイン アカウントを作成およびカスタマイズします。  
  
2.  **sp_xp_cmdshell_proxy_account**システム プロシージャを使用して、その最小特権アカウントを使用するように**xp_cmdshell**を構成します。  
  
    > [!NOTE]  
    >  オブジェクト エクスプローラーでサーバー名の[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**[プロパティ]** を右クリックし、[**セキュリティ**] タブの [サーバー プロキシ アカウント] セクションを確認して、この**プロキシ アカウント**を構成することもできます。  
  
3.  では[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]、 master データベースを使用して`GRANT exec ON xp_cmdshell TO N'<some_user>';`ステートメントを実行し、特定の非**sysadmin**ユーザーに**xp_cmdshell**を実行する機能を提供します。 指定したユーザーは、master データベースに存在している必要があります。  
  
 管理者以外のユーザーは **、xp_cmdshell**を使用してオペレーティング システム プロセスを起動でき、これらのプロセスは、構成したプロキシ アカウントのアクセス許可で実行されます。 CONTROL SERVER 権限を持つユーザー **(sysadmin**固定サーバー ロールのメンバ) は[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**、xp_cmdshell**によって起動された子プロセスに対するサービス アカウントのアクセス許可を引き続き受け取ります。  
  
 オペレーティング システム プロセスを起動するときに**xp_cmdshell**によって使用される Windows アカウントを確認するには、次のステートメントを実行します。  
  
```  
xp_cmdshell 'whoami.exe'  
  
```  
  
 別のログインのセキュリティ コンテキストを確認するには、次のコマンドを実行します。  
  
```  
EXECUTE AS LOGIN = '<other_login>' ;  
GO  
xp_cmdshell 'whoami.exe' ;  
REVERT ;  
  
```  
  
## <a name="examples"></a>使用例  
  
### <a name="a-returning-a-list-of-executable-files"></a>A. 実行可能ファイルの一覧を返す  
 次の例では、ディレクトリ コマンドを実行する `xp_cmdshell` 拡張ストアド プロシージャを示します。  
  
```  
EXEC master..xp_cmdshell 'dir *.exe'  
```  
  
### <a name="b-returning-no-output"></a>B. 出力を返さない  
 次の例では`xp_cmdshell`、出力をクライアントに返さずにコマンド文字列を実行します。  
  
```  
USE master;  
  
EXEC xp_cmdshell 'copy c:\SQLbcks\AdvWorks.bck  
    \\server2\backups\SQLbcks', NO_OUTPUT;  
GO  
```  
  
### <a name="c-using-return-status"></a>C. 返品ステータスの使用  
 次の例では、`xp_cmdshell`拡張ストアド プロシージャは、戻りステータスも提案します。 戻りコード値は 変数`@result`に格納されます。  
  
```  
DECLARE @result int;  
EXEC @result = xp_cmdshell 'dir *.exe';  
IF (@result = 0)  
   PRINT 'Success'  
ELSE  
   PRINT 'Failure';  
```  
  
### <a name="d-writing-variable-contents-to-a-file"></a>D. 変数の内容をファイルに書き込む  
 次の例では、`@var` 変数の内容を、現在のサーバー ディレクトリにある `var_out.txt` というファイルに書き込みます。  
  
```  
DECLARE @cmd sysname, @var sysname;  
SET @var = 'Hello world';  
SET @cmd = 'echo ' + @var + ' > var_out.txt';  
EXEC master..xp_cmdshell @cmd;  
```  
  
### <a name="e-capturing-the-result-of-a-command-to-a-file"></a>E. コマンドの結果をファイルにキャプチャする  
 次の例では、現在のディレクトリの内容を、現在の`dir_out.txt`サーバー ディレクトリ内のファイルに書き込みます。  
  
```  
DECLARE @cmd sysname, @var sysname;  
SET @var = 'dir/p';  
SET @cmd = @var + ' > dir_out.txt';  
EXEC master..xp_cmdshell @cmd;  
```  
  
## <a name="see-also"></a>関連項目  
 [汎用拡張ストアド プロシージャ&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)   
 [xp_cmdshellサーバー構成オプション](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md)   
 [大域構成](../../relational-databases/security/surface-area-configuration.md)   
 [sp_xp_cmdshell_proxy_account&#40;のトランザクション SQL&#41;](../../relational-databases/system-stored-procedures/sp-xp-cmdshell-proxy-account-transact-sql.md)  
  
  
