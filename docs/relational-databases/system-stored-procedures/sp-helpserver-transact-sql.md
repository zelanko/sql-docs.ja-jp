---
title: "sp_helpserver (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sp_helpserver
- sp_helpserver_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_helpserver
ms.assetid: e8f42de7-c738-41c3-8bf5-dbd559dc7184
caps.latest.revision: "21"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8f211b282456e1fa94f16c8eafdd758d41a72280
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="sphelpserver-transact-sql"></a>sp_helpserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  特定のリモート サーバーまたはレプリケーション サーバー、あるいはすべてのリモート サーバーとレプリケーション サーバーに関する情報をレポートします。 サーバー名、サーバーのネットワーク名、サーバーのレプリケーションの状態、サーバーの識別番号、照合順序名がレポートされます。 また、リンク サーバーに対する接続やクエリのタイムアウト値もレポートされます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helpserver [ [ @server = ] 'server' ]   
  [ , [ @optname = ] 'option' ]   
  [ , [ @show_topology = ] 'show_topology' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@server =** ] **'***サーバー***'**  
 レポート対象のサーバーを指定します。 ときに*サーバー*が指定されていないすべてのサーバーに関するレポート**master.sys.servers**です。 *サーバー*は**sysname**、既定値は NULL です。  
  
 [  **@optname =** ] **'***オプション***'**  
 サーバーを説明するオプションを指定します。 *オプション*は**varchar (**35**)**、既定値は NULL、これらの値のいずれかを指定する必要があります。  
  
|値|Description|  
|-----------|-----------------|  
|**互換性のある照合順序**|リンク サーバーに対するディストリビュートされたクエリの実行に影響します。 このオプションを true に設定した場合、|  
|**データ アクセス**|分散クエリ アクセスに対してリンク サーバーを有効または無効にします。|  
|**dist**|ディストリビューターです。|  
|**dpub**|ディストリビューターへのリモート パブリッシャーです。|  
|**限定的なスキーマの検証**|クエリ開始時のリモート テーブルのスキーマ チェックをスキップします。|  
|**pub**|パブリッシャーです。|  
|**rpc**|指定されたサーバーからの RPC を有効にします。|  
|**[rpc 出力]**|指定されたサーバーへの RPC を有効にします。|  
|**sub**|サブスクライバーです。|  
|**システム**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**リモート照合順序を使用します。**|ローカル サーバーの照合順序ではなく、リモート列の照合順序を使用します。|  
  
 [  **@show_topology =** ] **'***show_topology***'**  
 指定したサーバーと他のサーバーとの関係を指定します。 *show_topology*は**varchar (**1**)**、既定値は NULL です。 場合*show_topology*は等しくありません**t**が NULL の場合、または**sp_helpserver**結果セット セクションに示されている列を返します。 場合*show_topology*と等しい**t**、結果セットに示されている列だけでなく**sp_helpserver**も返します**topx**と**topy**情報。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|サーバー名。|  
|**network_name**|**sysname**|サーバーのネットワーク名|  
|**ステータス**|**varchar (**70**)**|サーバーの状態|  
|**id**|**char (**4**)**|サーバーの識別番号|  
|**collation_name**|**sysname**|サーバーの照合順序です。|  
|**connect_timeout**|**int**|リンク サーバーへの接続のタイムアウト値|  
|**query_timeout**|**int**|リンク サーバーに対するクエリのタイムアウト値|  
  
## <a name="remarks"></a>解説  
 1 つのサーバーについて複数の状態値が返されることもあります。  
  
## <a name="permissions"></a>Permissions  
 権限は確認されません。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-displaying-information-about-all-servers"></a>A. すべてのサーバーに関する情報を表示する  
 次の例では、パラメーターを指定せずに `sp_helpserver` を使用して、すべてのサーバーに関する情報を表示します。  
  
```  
USE master;  
GO  
EXEC sp_helpserver;  
```  
  
### <a name="b-displaying-information-about-a-specific-server"></a>B. 特定のサーバーに関する情報を表示する  
 次の例では、すべての情報を表示について、`SEATTLE2`サーバー。  
  
```  
USE master;  
GO  
EXEC sp_helpserver 'SEATTLE2';  
```  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sp_adddistpublisher &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_addserver &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)   
 [sp_addsubscriber &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addsubscriber-transact-sql.md)   
 [sp_changesubscriber &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-changesubscriber-transact-sql.md)   
 [sp_dropserver &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-dropserver-transact-sql.md)   
 [sp_dropsubscriber &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-dropsubscriber-transact-sql.md)   
 [sp_helpdistributor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql.md)   
 [sp_helpremotelogin &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helpremotelogin-transact-sql.md)   
 [sp_helpsubscriberinfo &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql.md)   
 [sp_serveroption &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-serveroption-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
