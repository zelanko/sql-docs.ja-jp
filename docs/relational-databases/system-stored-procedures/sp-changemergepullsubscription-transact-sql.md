---
title: sp_changemergepullsubscription (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_changemergepullsubscription
- sp_changemergepullsubscription_TSQL
helpviewer_keywords:
- sp_changemergepullsubscription
ms.assetid: 5e0d04f2-6175-44a2-ad96-a8e2986ce4c9
caps.latest.revision: 29
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c195541281667574fb7283b368f91fc1e02bb4d8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="spchangemergepullsubscription-transact-sql"></a>sp_changemergepullsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  マージ プル サブスクリプションのプロパティを変更します。 このストアド プロシージャは、サブスクライバー側でサブスクリプション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_changemergepullsubscription [ [ @publication= ] 'publication' ]  
    [ , [ @publisher= ] 'publisher' ]  
    [ , [ @publisher_db= ] 'publisher_db' ]  
    [ , [ @property= ] 'property' ]  
    [ , [ @value= ] 'value' ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@publication=**] **'***publication***'**  
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値は % です。  
  
 [ **@publisher=**] **'***publisher***'**  
 パブリッシャーの名前です。 *パブリッシャー*は**sysname**、既定値は % です。  
  
 [ **@publisher_db=**] **'***publisher_db***'**  
 パブリッシャー データベースの名前です。 *publisher_db*は**sysname**、既定値は % です。  
  
 [  **@property=**] **'***プロパティ***'**  
 変更するプロパティの名前を指定します。 *プロパティ*は**sysname**テーブル内の値のいずれかを指定できます。  
  
 [  **@value=**] **'***値***'**  
 指定したプロパティの新しい値です。 *値*は**nvarchar (255)**テーブル内の値のいずれかを指定できます。  
  
|プロパティ|値|Description|  
|--------------|-----------|-----------------|  
|**alt_snapshot_folder**||スナップショット フォルダーが既定の場所以外、または既定の場所に加えて保存されている場合の格納場所です。|  
|**説明**||このマージ プル サブスクリプションの説明です。|  
|**ディストリビューター**||ディストリビューターの名前です。|  
|**distributor_login**||場合はディストリビューターで使用されたログイン ID[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証|  
|**distributor_password**||場合はディストリビューターで使用するパスワード (暗号化)[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。|  
|**distributor_security_mode**|**1**|ディストリビューターに接続するときに Windows 認証を使用。|  
||**0**|使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ディストリビューターに接続するときに認証します。|  
|**dynamic_snapshot_location**||スナップショット ファイルが保存されるフォルダーへのパスです。|  
|**ftp_address**||旧バージョンとの互換性を保つのために利用できます。 ディストリビューター用ファイル転送プロトコル (FTP) サービスのネットワーク アドレスです。|  
|**ftp_login**||旧バージョンとの互換性を保つのために利用できます。 FTP サービスに接続するときに使用するユーザー名です。|  
|**ftp_password**||旧バージョンとの互換性を保つのために利用できます。 FTP サービスに接続するときに使用するユーザー パスワードです。|  
|**ftp_port**||旧バージョンとの互換性を保つのために利用できます。 ディストリビューター用の FTP サービスのポート番号です。|  
|**ホスト名**||HOST_NAME() 関数を結合フィルターまたは論理レコードのリレーションシップの WHERE 句で使用するときの、この関数の値を指定します。|  
|**internet_login**||基本認証を使用して Web 同期をホストしている Web サーバーに接続するときにマージ エージェントが使用するログインです。|  
|**internet_password**||基本認証を使用して Web 同期をホストしている Web サーバーに接続するときにマージ エージェントが使用するログインのパスワードです。|  
|**internet_security_mode**|**1**|Web 同期をホストしている Web サーバーに接続するときに、Windows 認証を使用します。|  
||**0**|Web 同期をホストしている Web サーバーに接続するときに、基本認証を使用します。|  
|**internet_timeout**||Web 同期要求が期限切れとなるまでの時間 (秒単位)。|  
|**internet_url**||Web 同期中にレプリケーション リスナーの位置を表す URL です。|  
|**merge_job_login**||エージェントを実行する Windows アカウントのログイン。|  
|**merge_job_password**||エージェントを実行する Windows アカウントのパスワード。|  
|**priority**||旧バージョンとの互換性だけです。実行[sp_changemergesubscription](../../relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql.md)パブリッシャー側で代わりに、サブスクリプションの優先度を変更します。|  
|**publisher_login**||パブリッシャーで使用されたログイン ID[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。|  
|**publisher_password**||パブリッシャーで使用する (暗号化) パスワード[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。|  
|**publisher_security_mode**|**0**|使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーに接続するときに認証します。|  
||**1**|パブリッシャーに接続するときに Windows 認証を使用。|  
||**2**|同期トリガーが、静的なを使用して**sysservers**でリモート プロシージャ コール (RPC)、およびパブリッシャーを実行するエントリを定義する必要があります、 **sysservers**リモート サーバーまたはリンク サーバーとしてのテーブルです。|  
|**sync_type**|**自動**|パブリッシュされたテーブルのスキーマと初期データが、最初にサブスクライバーに転送されます。|  
||**[なし]**|サブスクライバーには、パブリッシュされたテーブルに関するスキーマと初期データがあります。システム テーブルとデータが常に転送されます。|  
|**@use_ftp**|**true**|通常のプロトコルの代わりに FTP を使用してスナップショットを取得します。|  
||**false**|通常のプロトコルを使用してスナップショットを取得します。|  
|**@use_web_sync**|**true**|サブスクリプションは HTTP 上で同期できます。|  
||**false**|サブスクリプションは HTTP 上で同期できません。|  
|**use_interactive_resolver**|**true**|調整時にインタラクティブ競合回避モジュールを使用します。|  
||**false**|インタラクティブ競合回避モジュールを使用しません。|  
|**working_directory**||該当するオプションが指定され、FTP を使ってスナップショット ファイルを転送する場合の、転送先のディレクトリの完全修飾パスです。|  
|NULL (既定値)||サポートされる値の一覧を返します*プロパティ*です。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_changemergepullsubscription**はマージ レプリケーションで使用します。  
  
 現在のサーバーがサブスクライバー、現在のデータベースがサブスクライバー データベースであると解釈されます。  
  
 エージェントのログインまたはパスワードを変更した後、変更を有効にするには、エージェントを停止して再起動する必要があります。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_changemergepullsubscription**です。  
  
## <a name="see-also"></a>参照  
 [表示および変更のプル サブスクリプションのプロパティ](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [sp_addmergepullsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md)   
 [sp_dropmergepullsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql.md)   
 [sp_helpmergepullsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
