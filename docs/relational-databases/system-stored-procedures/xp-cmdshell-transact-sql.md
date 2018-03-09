---
title: "xp_cmdshell (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
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
- xp_cmdshell
- xp_cmdshell_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- xp_cmdshell
ms.assetid: 18935cf4-b320-4954-b6c1-e007fcefe358
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: bb3fcd3cba2be225c4c45514b2dcbc021683c0db
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="xpcmdshell-transact-sql"></a>xp_cmdshell (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Windows のコマンド シェルを起動し、実行用の文字列に渡します。 出力は、テキストの行として返されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
xp_cmdshell { 'command_string' } [ , no_output ]  
```  
  
## <a name="arguments"></a>引数  
 **'** *command_string* **'**  
 オペレーティング システムに渡すコマンドを含む文字列を指定します。 *command_string*は**varchar (8000)**または**nvarchar (4000)**、既定値はありません。 *command_string*二重引用符の 1 つ以上のセットを含めることはできません。 スペースをすべてのファイル パスに存在またはプログラムの名前で参照されている場合は、引用符の 1 つのペアが必要*command_string*です。 ファイル パスやファイル名に埋め込まれたスペースに関する問題が発生する場合は、その問題への対処方法として FAT 8.3 ファイル名の使用を検討してください。  
  
 **no_output**  
 クライアントに出力を返す必要がないことを指定します (省略可能)。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 次の `xp_cmdshell` ステートメントを実行すると、現在のディレクトリの一覧が返されます。  
  
```  
EXEC xp_cmdshell 'dir *.exe';  
GO  
```  
  
 行が返されます、 **nvarchar (255)**列です。 場合、 **no_output**オプションを使用すると、次のオプションのみが返されます。  
  
```  
The command(s) completed successfully.  
```  
  
## <a name="remarks"></a>解説  
 によって生成される Windows プロセス**xp_cmdshell**として同じセキュリティ権限を持つ、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サービス アカウント。  
  
 **xp_cmdshell**同期的に動作します。 制御は、コマンド シェルのコマンドが完了するまで呼び出し元に返されません。  
  
 **xp_cmdshell**有効になっているし、ポリシー ベースの管理を使用するか、実行することによって無効になっていることができます**sp_configure**です。 詳細については、次を参照してください。 [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md)と[xp_cmdshell サーバー構成オプション](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md)です。  
  
> [!IMPORTANT]  
>  場合**xp_cmdshell**バッチ内で実行され、エラーを返します、バッチは失敗します。 これは新しい動作です。 以前のバージョンの[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]バッチは実行を続行します。  
  
## <a name="xpcmdshell-proxy-account"></a>xp_cmdshell プロキシ アカウント  
 メンバーではないユーザーによって呼び出されたとき、 **sysadmin**固定サーバー ロール、 **xp_cmdshell**アカウント名と名前付き資格情報に格納されているパスワードを使用して Windows への接続**##xp_cmdshell_proxy_account ##**です。 このプロキシ資格情報が存在しない場合**xp_cmdshell**は失敗します。  
  
 プロキシ アカウントの資格情報を実行して作成できる**sp_xp_cmdshell_proxy_account**です。 このストアド プロシージャは、Windows のユーザー名とパスワードを引数にとります。 次のコマンドが Windows ドメイン ユーザーの資格情報をプロキシを作成するなど、 `SHIPPING\KobeR` Windows パスワードを持つ`sdfh%dkc93vcMt0`します。  
  
```  
EXEC sp_xp_cmdshell_proxy_account 'SHIPPING\KobeR','sdfh%dkc93vcMt0';  
```  
  
 詳細については、次を参照してください。 [sp_xp_cmdshell_proxy_account &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-xp-cmdshell-proxy-account-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 悪意のあるユーザーが場合がありますを使用して、特権の昇格を試行するため**xp_cmdshell**、 **xp_cmdshell**は既定で無効になります。 使用して**sp_configure**または**ポリシー ベースの管理**有効にします。 詳細については、「 [xp_cmdshell サーバー構成オプション](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md)」を参照してください。  
  
 最初に有効な場合、 **xp_cmdshell**を実行する、CONTROL SERVER 権限とによって作成される Windows プロセスが必要です**xp_cmdshell**と同じセキュリティ コンテキストを持つ、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サービス アカウント。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サービス アカウントは多くの場合、によって作成されるプロセスで実行される作業のために必要な以上のアクセス許可を持っている**xp_cmdshell**です。 アクセスをセキュリティ強化のため、 **xp_cmdshell**高い特権を持つユーザーに制限する必要があります。  
  
 管理者以外のユーザーが使用できるように**xp_cmdshell**、でき、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に低い特権のアカウントのセキュリティ トークンを使用して子プロセスを作成するに次の手順に従います。  
  
1.  プロセスに必要な最低限の特権を持つ Windows ローカル ユーザー アカウントまたはドメイン アカウントを作成およびカスタマイズします。  
  
2.  使用して、 **sp_xp_cmdshell_proxy_account**を構成するシステム プロシージャ**xp_cmdshell**最小特権アカウントを使用します。  
  
    > [!NOTE]  
    >  このプロキシを使用してアカウントを構成することも[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を右クリックして**プロパティ**サーバーには、オブジェクト エクスプ ローラーで、名前し、を見て、**セキュリティ**タブに移動して、**サーバープロキシ アカウント**セクションです。  
  
3.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]、Master データベースを使用して、実行、`GRANT exec ON xp_cmdshell TO '<somelogin>'`ステートメント以外の特定の提供を**sysadmin**ユーザーを実行できる**xp_cmdshell**です。 指定したログインが master データベース内のユーザーにマップされている必要があります。  
  
 これで、管理者以外のユーザーは、オペレーティング システム プロセスを起動できます**xp_cmdshell**し、それらのプロセスが構成されているプロキシ アカウントのアクセス許可で実行します。 CONTROL SERVER 権限を持つユーザー (のメンバー、 **sysadmin**固定サーバー ロール) の権限が与えは引き続き、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]によって起動された子プロセス用のサービス アカウント**xp_cmdshell**.  
  
 によって使用されている Windows アカウントを特定する**xp_cmdshell**オペレーティング システム プロセスを起動するときに、次のステートメントを実行します。  
  
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
EXEC master..xp_cmdshell 'dir *.exe''  
```  
  
### <a name="b-returning-no-output"></a>B. 出力を返さない  
 次の例では`xp_cmdshell`をクライアントに出力を返さずにコマンド文字列を実行します。  
  
```  
USE master;  
  
EXEC xp_cmdshell 'copy c:\SQLbcks\AdvWorks.bck  
    \\server2\backups\SQLbcks, NO_OUTPUT';  
GO  
```  
  
### <a name="c-using-return-status"></a>C. 戻りステータスを使用する  
 次の例で、`xp_cmdshell`拡張ストアド プロシージャも、返されたステータス。 リターン コード値が変数に格納されている`@result`です。  
  
```  
DECLARE @result int;  
EXEC @result = xp_cmdshell 'dir *.exe';  
IF (@result = 0)  
   PRINT 'Success'  
ELSE  
   PRINT 'Failure';  
```  
  
### <a name="d-writing-variable-contents-to-a-file"></a>D. さまざまな内容をファイルに書き込む  
 次の例では、`@var` 変数の内容を、現在のサーバー ディレクトリにある `var_out.txt` というファイルに書き込みます。  
  
```  
DECLARE @cmd sysname, @var sysname;  
SET @var = 'Hello world';  
SET @cmd = 'echo ' + @var + ' > var_out.txt';  
EXEC master..xp_cmdshell @cmd;  
```  
  
### <a name="e-capturing-the-result-of-a-command-to-a-file"></a>E. コマンドの結果をファイルにキャプチャする  
 次の例では、現在のディレクトリの内容をという名前のファイルに書き込みます`dir_out.txt`現在のサーバー ディレクトリにします。  
  
```  
DECLARE @cmd sysname, @var sysname;  
SET @var = 'dir/p';  
SET @cmd = @var + ' > dir_out.txt';  
EXEC master..xp_cmdshell @cmd;  
```  
  
## <a name="see-also"></a>参照  
 [汎用拡張ストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)   
 [xp_cmdshell サーバー構成オプション](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md)   
 [セキュリティ構成](../../relational-databases/security/surface-area-configuration.md)   
 [sp_xp_cmdshell_proxy_account &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-xp-cmdshell-proxy-account-transact-sql.md)  
  
  
