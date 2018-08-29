---
title: xp_logininfo (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- xp_logininfo_TSQL
- xp_logininfo
dev_langs:
- TSQL
helpviewer_keywords:
- xp_logininfo
ms.assetid: ee7162b5-e11f-4a0e-a09c-1878814dbbbd
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: c10a914bc69b60b1cfd6cd3e88cae97a73f9aa0e
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43033528"
---
# <a name="xplogininfo-transact-sql"></a>xp_logininfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Windows ユーザーおよび Windows グループに関する情報を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
xp_logininfo [ [ @acctname = ] 'account_name' ]   
     [ , [ @option = ] 'all' | 'members' ]   
     [ , [ @privilege = ] variable_name OUTPUT]  
```  
  
## <a name="arguments"></a>引数  
 [  **@acctname =** ] **'***account_name***'**  
 Windows ユーザーまたはグループへのアクセス許可の名前は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 *account_name*は**sysname**、既定値は NULL です。 場合*account_name*が指定されていない、すべての Windows グループと明示的に設定されている Windows ユーザー ログイン権限が与え報告されます。 *account_name*完全修飾である必要があります。 たとえば、「ADVWKS4\macraes」または「BUILTIN\Administrators」のように指定します。  
  
 **'all'** | **'members'**  
 アカウントに対するすべての権限のパスに関する情報をレポートするのか、または Windows のグループのメンバーに関する情報をレポートするのかを指定します。 **@option** **varchar (10)**、既定値は NULL です。 しない限り、**すべて**を指定すると、最初の権限のパスのみが表示されます。  
  
 [  **@privilege =** ] *variable_name*  
 指定した Windows アカウントの特権レベルを返す出力パラメーターを指定します。 *variable_name*は**varchar (10)**、既定値は 'Not wanted' です。 特権レベルが返される**ユーザー**、**管理者**、または**null**します。  
  
 OUTPUT  
 指定した場合、配置*variable_name*出力パラメーター。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**アカウント名**|**sysname**|Windows アカウントの完全修飾名。|  
|**type**|**char (8)**|Windows アカウントの種類。 有効な値は**ユーザー**または**グループ**します。|  
|**特権**|**char(9)**|に対するアクセス権限[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 有効な値は**管理者**、**ユーザー**、または**null**します。|  
|**マップされたログイン名**|**sysname**|ユーザーの権限のあるユーザー アカウントの**ログイン名をマップ**マップされたログイン名を示します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]前にドメイン名にマップされている規則を使用して、このアカウントでログインが追加されたときに使用しようとしています。|  
|**アクセス許可のパス**|**sysname**|アカウントのアクセスを許可したグループのメンバーシップ。|  
  
## <a name="remarks"></a>コメント  
 場合*account_name*が指定されている**xp_logininfo**指定した Windows ユーザーまたはグループの最上位の特権レベルを報告します。 Windows ユーザーに、システム管理者とドメイン ユーザーの両方のアクセス権限がある場合は、システム管理者としてレポートされます。 最初にされたグループのみがアクセス許可、ユーザーが同じ権限レベルの複数の Windows グループのメンバーである場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が報告されます。  
  
 場合*account_name*は有効な Windows ユーザーまたはグループが関連付けられていないを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログイン、空の結果セットが返されます。 場合*account_name*識別できない有効な Windows ユーザーまたはグループは、エラー メッセージが返されます。  
  
 場合*account_name*と**すべて**は指定すると、Windows ユーザーまたはグループのすべての権限のパスが返されます。 場合*account_name*へのアクセスが許可されたすべての複数のグループのメンバーである[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、複数の行が返されます。 **管理者**特権の行が前に返される、**ユーザー**特権の行と順序で同じ特権レベルの行が返されない、対応する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインが作成されました。  
  
 場合*account_name*と**メンバー**は指定するには、次のレベル グループのメンバーの一覧が返されます。 場合*account_name*ローカル グループは、一覧は、ローカル ユーザー、ドメインのユーザーとグループを含めることができます。 場合*account_name*ドメイン アカウント、ドメイン ユーザーの一覧から成ます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではドメイン コントローラーに接続してグループのメンバーシップ情報を取得する必要があります。 サーバーがドメイン コントローラーと通信できない場合、情報は返されません。  
  
 **xp_logininfo** Active Director グローバル グループ、ユニバーサルいないグループからのみ情報を返します。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーシップが必要です、 **sysadmin**固定サーバー ロールのメンバーシップまたは、**パブリック**固定データベース ロール、**マスター** EXECUTE 権限を持つデータベース。  
  
## <a name="examples"></a>使用例  
 次の例では、に関する情報を表示、 `BUILTIN\Administrators` Windows グループ。  
  
```  
EXEC xp_logininfo 'BUILTIN\Administrators';  
```  
  
## <a name="see-also"></a>参照  
 [sp_denylogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-denylogin-transact-sql.md)   
 [sp_grantlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [sp_revokelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [汎用拡張ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)  
  
  
