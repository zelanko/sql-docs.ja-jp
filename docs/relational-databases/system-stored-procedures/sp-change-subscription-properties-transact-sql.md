---
title: sp_change_subscription_properties (トランザクション-SQL) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_change_subscription_properties_TSQL
- sp_change_subscription_properties
helpviewer_keywords:
- sp_change_subscription_properties
ms.assetid: cf8137f9-f346-4aa1-ae35-91a2d3c16f17
author: stevestein
ms.author: sstein
ms.openlocfilehash: e033e446fc771ad87542474edb1e90caf08faebd
ms.sourcegitcommit: 1a96abbf434dfdd467d0a9b722071a1ca1aafe52
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81528788"
---
# <a name="sp_change_subscription_properties-transact-sql"></a>sp_change_subscription_properties (トランザクション-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  プル サブスクリプションの情報を更新します。 このストアド プロシージャは、サブスクリプション データベースのサブスクライバで実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_change_subscription_properties [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'  
        , [ @property = ] 'property'  
        , [ @value = ] 'value'  
    [ , [ @publication_type = ] publication_type ]  
```  
  
## <a name="arguments"></a>引数  
`[ @publisher = ] 'publisher'`パブリッシャーの名前です。 *発行元*は**sysname**で、デフォルトはありません。  
  
`[ @publisher_db = ] 'publisher_db'`パブリッシャー データベースの名前です。 *publisher_db*は**sysname**で、デフォルトはありません。  
  
`[ @publication = ] 'publication'`パブリケーションの名前です。 *パブリケーション*は**sysname**で、デフォルトはありません。  
  
`[ @property = ] 'property'`変更するプロパティです。 *プロパティ*は**sysname です**。  
  
`[ @value = ] 'value'`プロパティの新しい値です。 *値*は**nvarchar(1000) で**、デフォルトはありません。  
  
`[ @publication_type = ] publication_type`パブリケーションのレプリケーションの種類を指定します。 *publication_type*は**int**であり、これらの値のいずれかになります。  
  
|値|パブリケーションの種類|  
|-----------|----------------------|  
|**0**|トランザクション|  
|**1**|スナップショット|  
|**2**|Merge|  
|NULL (デフォルト)|レプリケーションによってパブリケーションの種類が決定されます。 このストアド プロシージャでは複数のテーブルを検索する必要があるため、このオプションを指定すると、パブリケーションの種類を直接指定したときに比べて動作が遅くなります。|  
  
 次の表に、アーティクルのプロパティとそれらのプロパティの値を示します。  
  
|プロパティ|値|説明|  
|--------------|-----------|-----------------|  
|**alt_snapshot_folder**||スナップショットの代替フォルダーの場所を指定します。 NULL に設定すると、スナップショット ファイルは、パブリッシャーによって指定された既定の場所から選択されます。|  
|**distrib_job_login**||エージェントを実行する [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントのログイン。|  
|**distrib_job_password**||エージェントが実行される Windows アカウントのパスワード。|  
|**distributor_login**||ディストリビュータ ログイン。|  
|**distributor_password**||ディストリビューター パスワード。|  
|**distributor_security_mode**|**1**|ディストリビュータに接続するときに Windows 認証を使用します。|  
||**0**|ディス[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]トリビュータに接続する際は認証を使用します。|  
|**dts_package_name**||SQL Server 2000 データ変換サービス (DTS) パッケージの名前。 この値は、パブリケーションがトランザクションまたはスナップショットである場合にのみ指定できます。|  
|**dts_package_password**||パッケージのパスワードを指定します。 *dts_package_password*は、デフォルトの NULL の**sysname**で、パスワード・プロパティーを変更せずに残すことを指定します。<br /><br /> 注意 : DTS パッケージにはパスワードが必要です。<br /><br /> この値は、パブリケーションがトランザクションまたはスナップショットである場合にのみ指定できます。|  
|**dts_package_location**||DTS パッケージが格納される場所。 この値は、パブリケーションがトランザクションまたはスナップショットである場合にのみ指定できます。|  
|**dynamic_snapshot_location**||スナップショット ファイルが保存されるフォルダへのパスを指定します。 この値は、パブリケーションがマージ パブリケーションの場合にのみ指定できます。|  
|**ftp_address**||これは旧バージョンとの互換性のためにだけ用意されています。|  
|**ftp_login**||これは旧バージョンとの互換性のためにだけ用意されています。|  
|**ftp_password**||これは旧バージョンとの互換性のためにだけ用意されています。|  
|**ftp_port**||これは旧バージョンとの互換性のためにだけ用意されています。|  
|**ホスト**||パブリッシャに接続するときに使用するホスト名。|  
|**internet_login**||基本認証を使用して Web 同期をホストしている Web サーバーに接続するときにマージ エージェントが使用するログイン。|  
|**internet_password**||基本認証を使用して Web 同期をホストしている Web サーバーに接続するときにマージ エージェントが使用するパスワード。|  
|**internet_security_mode**|**1**|Web 同期に Windows 統合認証を使用します。 Web 同期では基本認証を使用することをお勧めします。 詳しくは、「 [Configure Web Synchronization](../../relational-databases/replication/configure-web-synchronization.md)」をご覧ください。|  
||**0**|Web 同期に基本認証を使用。<br /><br /> 注意 : Web 同期では、Web サーバーへの TLS 接続が必要です。|  
|**internet_timeout**||Web 同期要求の有効期限が切れるまでの時間 (秒単位)。|  
|**internet_url**||Web 同期のレプリケーション リスナーの場所を表す URL。|  
|**merge_job_login**||エージェントが実行される Windows アカウントのログイン。|  
|**merge_job_password**||エージェントが実行される Windows アカウントのパスワード。|  
|**publisher_login**||パブリッシャーログイン。 *publisher_login*の変更は、マージ パブリケーションのサブスクリプションでのみサポートされます。|  
|**publisher_password**||発行者のパスワード。 *publisher_password*の変更は、マージ パブリケーションのサブスクリプションでのみサポートされます。|  
|**publisher_security_mode**|**1**|パブリッシャーに接続するときに Windows 認証を使用。 *publisher_security_mode*の変更は、マージ パブリケーションのサブスクリプションでのみサポートされます。|  
||**0**|パブリッシャー[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に接続する際に認証を使用します。|  
|**use_ftp**|**true**|スナップショットを取得するには、通常のプロトコルではなく FTP を使用します。|  
||**false**|標準のプロトコルを使用してスナップショットを取得。|  
|**use_web_sync**|**true**|Web 同期を有効にします。|  
||**false**|Web 同期を無効にします。|  
|**working_directory**||スナップショット ファイルの転送にファイル転送プロトコル (FTP) を使用する場合に、パブリケーションのデータ ファイルとスキーマ ファイルを一時的に格納するために使用される作業ディレクトリの名前。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_change_subscription_properties**は、すべてのタイプのレプリケーションで使用されます。  
  
 **sp_change_subscription_properties**はプル サブスクリプションに使用されます。  
  
 Oracle パブリッシャーの場合、oracle では、サーバーのインスタンスごとに 1 つのデータベースしか許可しないため *、publisher_db*の値は無視されます。  
  
## <a name="permissions"></a>アクセス許可  
 sp_change_subscription_properties実行できるのは、固定サーバー ロールまたは固定データベース ロール**db_owner** **sysadmin**のメンバ**だけです。**  
  
## <a name="see-also"></a>参照  
 [プル サブスクリプションのプロパティの表示と変更](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [sp_addmergepullsubscription &#40;のトランザクション SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md)   
 [sp_addmergepullsubscription_agent &#40;のトランザクション SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md)   
 [sp_addpullsubscription&#40;のトランザクション SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md)   
 [sp_addpullsubscription_agent&#40;のトランザクション SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
