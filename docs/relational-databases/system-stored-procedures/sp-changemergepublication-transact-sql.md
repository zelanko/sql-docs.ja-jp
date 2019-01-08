---
title: sp_changemergepublication (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changemergepublication_TSQL
- sp_changemergepublication
helpviewer_keywords:
- sp_changemergepublication
ms.assetid: 81fe1994-7678-4852-980b-e02fedf1e796
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9eb6d52d72dec4efab7e744fd4eafd2d9a5eb612
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52788484"
---
# <a name="spchangemergepublication-transact-sql"></a>sp_changemergepublication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  マージ パブリケーションのプロパティを変更します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_changemergepublication [ @publication= ] 'publication'  
    [ , [ @property= ] 'property' ]  
    [ , [ @value= ] 'value' ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@publication=**] **'***publication***'**  
 パブリケーションの名前を指定します。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@property=**] **'***プロパティ***'**  
 指定したパブリケーションの変更対象となるプロパティを指定します。 *プロパティ*は**sysname**値のいずれかに指定できる次の表とします。  
  
 [  **@value=**] **'***値***'**  
 対象となるプロパティの新しい値を指定します。 *値*は**nvarchar (255)** 値のいずれかに指定できる次の表とします。  
  
 このテーブルには、変更でき、これらのプロパティの値に関する制限について説明するパブリケーションのプロパティについて説明します。  
  
|プロパティ|値|説明|  
|--------------|-----------|-----------------|  
|**allow_anonymous**|**true**|匿名サブスクリプションを許可します。|  
||**false**|匿名サブスクリプションを許可しません。|  
|**allow_partition_realignment**|**true**|削除がサブスクライバーに送信されることにより、サブスクライバーのパーティションの一部ではなくなったデータの削除による、パーティション変更の結果が反映されます。 これは既定の動作です。|  
||**false**|古いパーティションのデータはサブスクライバー側に残ります。パブリッシャーでこのデータに変更を加えてもこのサブスクライバーにはレプリケートされません。 サブスクライバーで加えた変更はパブリッシャーにレプリケートされます。 これは、履歴を参照する目的でデータにアクセスできるようにするために、サブスクリプションで古いパーティションのデータを残しておく場合に使用します。|  
|**allow_pull**|**true**|指定したパブリケーションに対してプル サブスクリプションを許可します。|  
||**false**|指定したパブリケーションに対してプル サブスクリプションを許可しません。|  
|**allow_push**|**true**|指定したパブリケーションに対してプッシュ サブスクリプションを許可します。|  
||**false**|指定したパブリケーションに対してプッシュ サブスクリプションを許可しません。|  
|**@allow_subscriber_initiated_snapshot**|**true**|サブスクライバーはスナップショット処理を開始できます。|  
||**false**|サブスクライバーはスナップショット処理を開始できません。|  
|**allow_subscription_copy**|**true**|このパブリケーションをサブスクライブするサブスクリプション データベースをコピーすることができます。|  
||**false**|このパブリケーションをサブスクライブするサブスクリプション データベースをコピーすることはできません。|  
|**allow_synctoalternate**|**true**|代替同期パートナーがこのパブリッシャーと同期できるようにします。|  
||**false**|代替同期パートナーがこのパブリッシャーと同期できないようにします。|  
|**allow_web_synchronization**|**true**|サブスクリプションは HTTPS 上で同期できます。|  
||**false**|サブスクリプションは HTTPS 上で同期できません。|  
|**alt_snapshot_folder**||スナップショットの代替フォルダーの場所を示します。|  
|**automatic_reinitialization_policy**|**1**|サブスクライバーから変更をアップロードしてからサブスクリプションを再初期化します。|  
||**0**|最初に変更をアップロードせずにサブスクリプションを再初期化します。|  
|**centralized_conflicts**|**true**|すべての競合レコードはパブリッシャーに保存されます。 このプロパティを変更する場合は、既存のサブスクライバーを再初期化する必要があります。|  
||**false**|競合の解決で優先されなかった競合レコードはサーバーに保存されます。 このプロパティを変更する場合は、既存のサブスクライバーを再初期化する必要があります。|  
|**compress_snapshot**|**true**|代替スナップショット フォルダー内のスナップショットは CAB 形式に圧縮されます。 既定のスナップショット フォルダー内のスナップショットは圧縮できません。 このプロパティを変更するには、新しいスナップショットが必要です。|  
||**false**|既定では、スナップショットは圧縮されません。 このプロパティを変更するには、新しいスナップショットが必要です。|  
|**conflict_logging**|**パブリッシャー**|競合レコードはパブリッシャーに保存されます。|  
||**サブスクライバー**|競合レコードは、競合の原因となったサブスクライバーに保存されます。 サポートされていません[!INCLUDE[ssEW](../../includes/ssew-md.md)]サブスクライバー*します。*|  
||**両方**|競合レコードは、パブリッシャーとサブスクライバーの両方に保存されます。|  
|**conflict_retention**||**Int**競合を保有する日数で、保有期間を指定します。 設定*conflict_retention*に**0**競合のクリーンアップが必要ないことを意味します。|  
|**description**||パブリケーションの説明。|  
|**dynamic_filters**|**true**|パブリケーションは動的な句に基づいてフィルター選択されます。|  
||**false**|パブリケーションは動的にフィルター選択されません。|  
|**enabled_for_internet**|**true**|パブリケーションはインターネットに対応しています。 ファイル転送プロトコル (FTP) を使用して、スナップショット ファイルをサブスクライバーに転送できます。 パブリケーションの同期ファイルは、C:\Program Files\Microsoft SQL Server\MSSQL\Repldata\ftp ディレクトリに格納されます。|  
||**false**|パブリケーションはインターネットに対応していません。|  
|**ftp_address**||ディストリビューター用 FTP サービスのネットワーク アドレス。 パブリケーションのスナップショット ファイルを格納する場所を指定します。|  
|**ftp_login**||FTP サービスへの接続に使用されるユーザー名。|  
|**ftp_password**||FTP サービスに接続するときに使用するパスワードです。|  
|**ftp_port**||ディストリビューター用 FTP サービスのポート番号。 パブリケーションのスナップショット ファイルが格納される FTP サイトの TCP ポート番号を指定します。|  
|**ftp_subdirectory**||パブリケーションで FTP を使用したスナップショットの配布がサポートされている場合に、スナップショット ファイルが作成される場所を指定します。|  
|**generation_leveling_threshold**|**int**|1 回の生成に含まれる変更の数です。 生成とは、パブリッシャーまたはサブスクライバーに配信される変更のコレクションです。|  
|**keep_partition_changes**|**true**|同期は最適化され、変更されたパーティションの行を持つサブスクライバーだけに反映されます。 このプロパティを変更するには、新しいスナップショットが必要です。|  
||**false**|同期は最適化されず、サブスクライバーに送信されるパーティションは、1 つのパーティションでデータが変更されると確認されます。 このプロパティを変更するには、新しいスナップショットが必要です。|  
|**達した**||これは、 **int**パブリケーションに対して実行できる同時マージ処理の最大数を表します。 0 の場合、制限はありません。ここで指定した数を超えるマージ処理が同時に実行されるようにスケジュールすると、超過したジョブはキューに保存されて、現在実行中のマージ処理が終了するまで待機します。|  
|**max_concurrent_dynamic_snapshots**||これは、 **int**パラメーター化された行フィルターのことを表します、スナップショットの最大数をフィルター選択されたデータを生成するスナップショットのセッションを使用するマージ パブリケーションに対して同時に実行することができます。 場合**0**制限はありません。 ここで指定した数を超えるスナップショット処理が同時に実行されるようにスケジュールすると、超過したジョブはキューに保存されて、現在実行中のマージ処理が終了するまで待機します。|  
|**post_snapshot_script**||ポインターを指定します、 **.sql**ファイルの場所。 ディストリビューション エージェントまたはマージ エージェントは、初期同期で他のすべてのレプリケートされたオブジェクト スクリプトおよびデータが適用された後にポストスナップショット スクリプトを実行します。 このプロパティを変更するには、新しいスナップショットが必要です。|  
|**pre_snapshot_script**||ポインターを指定します、 **.sql**ファイルの場所。 マージ エージェントは、サブスクライバーでスナップショットを適用するときに、レプリケートされたオブジェクト スクリプトの前に、プリスナップ ショット スクリプトを実行します。 このプロパティを変更するには、新しいスナップショットが必要です。|  
|**publication_compatibility_level**|**100 RTM**|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|  
||**90 RTM**|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|  
|**publish_to_activedirectory**|**true**|このパラメーターは、旧バージョンのスクリプトとの互換性を保つために用意されており、非推奨とされます。 現在、Active Directory にはパブリケーション情報を追加できません。|  
||**false**|Active Directory からパブリケーション情報を削除します。|  
|**replicate_ddl**|**1**|パブリッシャーで実行されるデータ定義言語 (DDL) ステートメントがレプリケートされます。|  
||**0**|DDL ステートメントはレプリケートされません。|  
|**保有期間**||これは、 **int**の数を表す*retention_period_unit*単位を指定したパブリケーションに対する変更を保存します。 保有期間内にサブスクリプションが同期されず、受信した保留中の変更がディストリビューター側でクリーンアップ操作によって削除された場合、サブスクリプションは有効期限切れとなり、再初期化する必要があります。 最大許容保有期間は、現在の日付から 9999 年 12 月 31 日までの日数です。<br /><br /> 注:マージ パブリケーションの保有期間は、サブスクライバーの異なるタイム ゾーンに対応する 24 時間の猶予期間です。|  
|**retention_period_unit**|**day**|保有期間は、日単位で指定されます。|  
||**week**|保有期間は、週単位で指定されます。|  
||**month**|保有期間は、月単位で指定されます。|  
||**year**|保有期間は、年単位で指定されます。|  
|**snapshot_in_defaultfolder**|**true**|スナップショット ファイルは既定のスナップショット フォルダーに格納されます。|  
||**false**|指定されている別の場所にスナップショット ファイルが格納されている*alt_snapshot_folder*します。 このパラメーターの組み合わせを指定すると、スナップショット ファイルは、既定のフォルダーと代替位置の両方に格納されます。|  
|**snapshot_ready**|**true**|パブリケーションのスナップショットが使用可能になります。|  
||**false**|パブリケーションのスナップショットが使用できなくなります。|  
|**status**|**アクティブ**|パブリケーションはアクティブな状態です。|  
||**非アクティブ**|パブリケーションは非アクティブな状態です。|  
|**sync_mode**|**ネイティブ**または<br /><br /> **ネイティブ bcp**|初期スナップショットに対してすべてのテーブルのネイティブ モードの一括コピー プログラム出力が使用されます。|  
||**character**<br /><br /> または**bcp 文字**|初期スナップショットに対してすべてのテーブルの文字モードの一括コピー プログラム出力が使用されます。これは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のサブスクライバーで必要です。|  
|**use_partition_groups**<br /><br /> 注:場合に、partition_groups を使用した後を使用する元に戻す**setupbelongs**、設定と**use_partition_groups = false**で**changemergearticle**、正しく限りませんスナップショットが作成した後に反映されます。 スナップショットが生成するトリガーはパーティション グループに準拠します。<br /><br /> このシナリオを回避する状態を非アクティブに設定を変更するには、 **use_partition_groups**、し、状態をアクティブに設定します。|**true**|パブリケーションは事前計算済みパーティションを使用します。|  
||**false**|パブリケーションは事前計算済みパーティションを使用しません。|  
|**validate_subscriber_info**||サブスクライバー情報の取得に使用する関数を一覧表示します。 次に、情報のパーティション分割が一貫性を保っていることをサブスクライバーが確認するときに使用する動的フィルター選択の基準の妥当性を検証します。|  
|**web_synchronization_url**||Web 同期に使用されるインターネット URL の既定値です。|  
|NULL (既定値)||サポートされている値の一覧を返します*プロパティ*します。|  
  
 [ **@force_invalidate_snapshot =** ]*更によって*  
 このストアド プロシージャが実行する操作が既存のスナップショットが無効になることを確認します。 *更によって*は、**ビット**、既定値は**0**します。  
  
 **0**こと、パブリケーションの変更を無効にしない、スナップショットを指定します。 ストアド プロシージャで、変更に新しいスナップショットが必要であることが検出されると、エラーが発生し、変更は加えられません。  
  
 **1**パブリケーションを変更すると、スナップショットと、設定が可能性がありますを指定します。 既存のサブスクリプションで新しいスナップショットが必要な場合、この値を指定すると、既存のスナップショットを古いスナップショットとしてマークし新しいスナップショットを生成することができます。  
  
 プロパティは、「解説」を参照してください。 つまり、変更されたときには、新しいスナップショットを生成する必要があります。  
  
 [  **@force_reinit_subscription =** ]*更によって*  
 このストアド プロシージャが実行されるアクションでは、既存のサブスクリプションの再初期化される場合がありますかを確認します。 *更によって*は、**ビット**、既定値は**0**します。  
  
 **0**パブリケーションを変更する必要がないことのサブスクリプションが再初期化することを指定します。 変更に既存のサブスクリプションの再初期化が必要であることをストアド プロシージャが検出すると、エラーが発生し、変更は加えられません。  
  
 **1**の変更と、既存のサブスクリプションが初期化されることをパブリケーションとサブスクリプションの再初期化を許可を指定します。  
  
 変更によって既存のサブスクリプションの再初期化が必要になるプロパティについては、「解説」を参照してください。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_changemergepublication**はマージ レプリケーションで使用します。  
  
 次のプロパティを変更するには、新しいスナップショットを生成する必要があります。 値を指定する必要があります**1**の*更によって*パラメーター。  
  
-   **alt_snapshot_folder**  
  
-   **compress_snapshot**  
  
-   **dynamic_filters**  
  
-   **ftp_address**  
  
-   **ftp_login**  
  
-   **ftp_password**  
  
-   **ftp_port**  
  
-   **ftp_subdirectory**  
  
-   **post_snapshot_script**  
  
-   **publication_compatibility_level** (に**80sp3 以下**のみ)  
  
-   **pre_snapshot_script**  
  
-   **snapshot_in_defaultfolder**  
  
-   **sync_mode**  
  
-   **use_partition_groups**  
  
 次のプロパティを変更するには、既存のサブスクリプションを再初期化する必要があります。 値を指定する必要があります**1**の*更によって*パラメーター。  
  
-   **dynamic_filters**  
  
-   **validate_subscriber_info**  
  
 使用して Active directory パブリケーション オブジェクトの一覧に、 *publish_to_active_directory*、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オブジェクトは、Active Directory で既に作成する必要があります。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_changemergepublication](../../relational-databases/replication/codesnippet/tsql/sp-changemergepublicatio_1.sql)]  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_changemergepublication**します。  
  
## <a name="see-also"></a>参照  
 [パブリケーション プロパティの表示および変更](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [パブリケーションとアーティクルのプロパティの変更](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [sp_addmergepublication &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)   
 [sp_dropmergepublication &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepublication-transact-sql.md)   
 [sp_helpmergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
