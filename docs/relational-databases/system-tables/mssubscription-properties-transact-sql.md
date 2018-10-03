---
title: MSsubscription_properties (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSsubscription_properties
- MSsubscription_properties_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscription_properties system table
ms.assetid: f96fc1ae-b798-4b05-82a7-564ae6ef23b8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ec118a8eeab5753b1b6df3f917afd26a5b375807
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47837893"
---
# <a name="mssubscriptionproperties-transact-sql"></a>MSsubscription_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSsubscription_properties**テーブルには、パラメーター情報については、サブスクライバーでレプリケーション エージェントの実行に必要な行が含まれています。 このテーブルは、プル サブスクリプションの場合はサブスクライバー側のサブスクリプション データベースに格納され、プッシュ サブスクリプションの場合はディストリビューター側のディストリビューション データベースに格納されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**パブリッシャー**|**sysname**|パブリッシャーの名前。|  
|**publisher_db**|**sysname**|パブリッシャー データベースの名前。|  
|**パブリケーション**|**sysname**|パブリケーションの名前を指定します。|  
|**publication_type**|**int**|パブリケーションの種類。<br /><br /> **0** = トランザクション。<br /><br /> **2** = マージします。|  
|**publisher_login**|**sysname**|パブリッシャーで使用されたログイン ID[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。|  
|**publisher_password**|**nvarchar (524)**|パブリッシャーで使用するパスワード (暗号化)[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。|  
|**publisher_security_mode**|**int**|パブリッシャーで実装されているセキュリティ モード。<br /><br /> **0**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQL Server 認証。<br /><br /> **1**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 認証。<br /><br /> **2**静的な同期のトリガーの使用を = **sysservers**リモート プロシージャ コール (RPC) を実行するエントリと*パブリッシャー*で定義する必要があります、 **sysservers**リモート サーバーまたはリンク サーバーとしてのテーブル。|  
|**ディストリビューター**|**sysname**|ディストリビューターの名前。|  
|**distributor_login**|**sysname**|ディストリビューターで使用する SQL Server 認証のログイン ID です。|  
|**distributor_password**|**nvarchar (524)**|場合はディストリビューターを使用するパスワード (暗号化)[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。|  
|**distributor_security_mode**|**int**|ディストリビューターで実装されているセキュリティ モード。<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。<br /><br /> **1** = Windows 認証。|  
|**ftp_address**|**sysname**|ディストリビューター用ファイル転送プロトコル (FTP) サービスのネットワーク アドレス。|  
|**ftp_port**|**int**|ディストリビューター用 FTP サービスのポート番号。|  
|**ftp_login**|**sysname**|FTP サービスへの接続に使用されるユーザー名。|  
|**ftp_password**|**nvarchar (524)**|U.User パスワードは、FTP サービスに接続するために使用します。|  
|**alt_snapshot_folder**|**nvarchar (255)**|スナップショットの代替フォルダーの場所を指定します。|  
|**working_directory**|**nvarchar (255)**|データ ファイルとスキーマ ファイルを保存するために使用される作業ディレクトリの名前。|  
|**@use_ftp**|**bit**|標準のプロトコルの代わりに FTP を使用してスナップショットを取得します。 場合**1**FTP を使用します。|  
|**dts_package_name**|**sysname**|データ変換サービス (DTS) パッケージの名前。|  
|**dts_package_password**|**nvarchar (524)**|パッケージのパスワードを指定します。|  
|**dts_package_location**|**int**|DTS パッケージが格納されている場所。|  
|**enabled_for_syncmgr**|**bit**|[!INCLUDE[msCoName](../../includes/msconame-md.md)] 同期マネージャーを介してサブスクリプションを同期化できるかどうかを示します。<br /><br /> **0** = サブスクリプションは同期マネージャーに登録されません。<br /><br /> **1** = サブスクリプションは同期マネージャーに登録および起動しなくても同期できます[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]します。|  
|**offload_agent**|**bit**|エージェントをリモートから起動できるかどうかを示します。 場合**0**エージェントをリモートでアクティブにできません。|  
|**offload_server**|**sysname**|リモートからのアクティブ化に使用するサーバーのネットワーク名。|  
|**dynamic_snapshot_location**|**nvarchar (255)**|スナップショット ファイルが保存されるフォルダーへのパス。|  
|**@use_web_sync**|**bit**|サブスクリプションが HTTP を介して同期できるかどうかを示します。 値**1**この機能が有効になっていることを意味します。|  
|**internet_url**|**nvarchar(260)**|Web 同期に対するレプリケーション リスナーの位置を表す URL。|  
|**internet_login**|**sysname**|使用して Web 同期をホストしている Web サーバーに接続するときに、マージ エージェントが使用するログインを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。|  
|**internet_password**|**nvarchar (524)**|マージ エージェントを使用して Web 同期をホストしている Web サーバーに接続するときに使用するログインのパスワード[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。|  
|**internet_security_mode**|**int**|値が、Web 同期をホストしている Web サーバーに接続するときに使用する認証モード**1** 、Windows 認証を示し、値の**0**意味[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。|  
|**internet_timeout**|**int**|Web 同期要求が期限切れとなるまでの時間の長さ (秒単位)。|  
|**ホスト名**|**sysname**|値を指定**HOST_NAME**でこの関数を使用する場合、**場所**結合フィルターまたは論理レコード リレーションシップの句。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_helppullsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md)   
 [sp_helpsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)   
 [sp_helpsubscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)  
  
  
