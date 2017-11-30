---
title: "xp_loginconfig (TRANSACT-SQL) |Microsoft ドキュメント"
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
- xp_loginconfig_TSQL
- xp_loginconfig
dev_langs: TSQL
helpviewer_keywords: xp_loginconfig
ms.assetid: d380e799-2857-408a-bcbf-5e73a8e6aa5a
caps.latest.revision: "38"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c3e070b1a6ba44a1f2a9c626745c0c7543446095
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="xploginconfig-transact-sql"></a>xp_loginconfig (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  インスタンスのログイン セキュリティ構成を報告[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
xp_loginconfig ['config_name']  
```  
  
## <a name="arguments"></a>引数  
 **'** *config_name 付きで* **'**  
 表示する構成値を指定します。 場合*config_name 付きで*が指定されていないすべての構成値が報告されます。 *config_name 付きで*は**sysname**、既定値は NULL、これらの値のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|**ログイン モード**|ログイン セキュリティ モード。 指定できる値は**Mixed**と**Windows 認証**です。<br /><br /> 次の文字列によって置き換えられました。<br /><br /> `SELECT SERVERPROPERTY('IsIntegratedSecurityOnly'); GO`|  
|**既定のログイン**|信頼関係接続が許可されているユーザー (ログイン名が照合されないユーザー) に対する、既定の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログイン ID の名前。 既定のログインは**ゲスト**です。 この値は旧バージョンとの互換性を維持するために用意されています。|  
|**既定のドメイン**|信頼関係接続が許可されているネットワーク ユーザーに対する、既定の Windows ドメインの名前。 既定のドメインは、Windows および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行しているコンピューターのドメインです。 この値は旧バージョンとの互換性を維持するために用意されています。|  
|**監査レベル**|監査レベル。 指定できる値は**none**、**成功**、**エラー**、および**すべて**です。 監査はエラー ログや Windows イベント ビューアーに書き込まれます。|  
|**一連のホスト名**|クライアントのログイン レコードのホスト名が、Windows ネットワーク ユーザー名と置き換えられるかどうかを示します。 指定できる値は**true**または**false**です。 これを設定するからの出力で、ネットワーク ユーザー名が表示されます**sp_who**です。|  
|**マップ _**|Windows の特殊文字は、有効なにマップされる[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]アンダー スコア文字 (_)。 指定できる値は**ドメインの区切り記号**(既定)、**領域**、 **null**、または任意の 1 文字です。 この値は旧バージョンとの互換性を維持するために用意されています。|  
|**マップの $**|Windows の特殊文字は、有効なにマップされる[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ドル記号 ($) の文字です。 指定できる値は**ドメインの区切り記号**、**領域**、 **null**、または任意の 1 文字です。 既定値は**領域**です。 この値は旧バージョンとの互換性を維持するために用意されています。|  
|**# をマップします。**|Windows の特殊文字は、有効なにマップされる[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]番号記号 (#)。 指定できる値は**ドメインの区切り記号**、**領域**、 **null**、または任意の 1 文字です。 既定値はハイフンです。 この値は旧バージョンとの互換性を維持するために用意されています。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|構成値。|  
|**設定値**|**sysname**|構成値の設定。|  
  
## <a name="remarks"></a>解説  
 **xp_loginconfig**構成値を設定するのには使用できません。  
  
 を設定するログイン モードと監査レベルを使用して[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]です。  
  
## <a name="permissions"></a>Permissions  
 に対する CONTROL 権限が必要です、**マスター**データベース。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-how-to-report-all-configuration-values"></a>A. すべての構成値をレポートする方法  
 次の例では、現在構成されている設定をすべて表示します。  
  
```  
EXEC xp_loginconfig;  
GO  
```  
  
### <a name="b-how-to-report-a-specific-configuration-value"></a>B. 特定の構成値をレポートする方法  
 次の例では、ログイン モードのみの設定値を表示します。  
  
```  
EXEC xp_loginconfig 'login mode';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_denylogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-denylogin-transact-sql.md)   
 [sp_grantlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sp_revokelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)   
 [xp_logininfo &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/xp-logininfo-transact-sql.md)  
  
  
