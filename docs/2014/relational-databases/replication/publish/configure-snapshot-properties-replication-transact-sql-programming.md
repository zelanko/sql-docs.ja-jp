---
title: スナップショットのプロパティの構成 (レプリケーション Transact-SQL プログラミング) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- snapshots [SQL Server replication], properties
ms.assetid: 978d150f-8971-458a-ab2b-3beba5937b46
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4c7dd645fed073f73132c6993f12925a885a8e0e
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85038043"
---
# <a name="configure-snapshot-properties-replication-transact-sql-programming"></a>スナップショットのプロパティの構成 (レプリケーション Transact-SQL プログラミング)
  スナップショットのプロパティは、レプリケーションのストアド プロシージャを使用し、プログラムから定義および変更できます。使用するストアド プロシージャは、パブリケーションの種類によって異なります。  
  
### <a name="to-configure-snapshot-properties-when-creating-a-snapshot-or-transactional-publication"></a>スナップショット パブリケーションまたはトランザクション パブリケーションを作成するときにスナップショットのプロパティを構成するには  
  
1.  パブリッシャーで [sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql)を実行します。 にパブリケーション名を指定し **@publication** ます。には**snapshot**または**continuous**のいずれかの値を指定し、次の **@repl_freq** スナップショット関連のパラメーターを1つ以上指定します。  
  
    -   **@alt_snapshot_folder**-このパブリケーションのスナップショットが、スナップショットの既定のフォルダーではなく、その場所からアクセスされる場合は、パスを指定します。  
  
    -   **@compress_snapshot**-代替スナップショットフォルダー内のスナップショットファイルを CAB ファイル形式で圧縮する場合は、値**true**を指定し [!INCLUDE[msCoName](../../../includes/msconame-md.md)] ます。  
  
    -   **@pre_snapshot_script**-初期スナップショットが適用される前に、初期化中にサブスクライバーで実行される **.sql**ファイルのファイル名と完全パスを指定します。  
  
    -   **@post_snapshot_script**-初期スナップショットが適用された後に、初期化中にサブスクライバーで実行される **.sql**ファイルのファイル名と完全パスを指定します。  
  
    -   **@snapshot_in_defaultfolder**-スナップショットを既定以外の場所でのみ使用できる場合は、 **false**の値を指定します。  
  
     パブリケーションの作成の詳細については、「 [Create a Publication](create-a-publication.md)」を参照してください。  
  
### <a name="to-configure-snapshot-properties-when-creating-a-merge-publication"></a>マージ パブリケーションを作成するときにスナップショットのプロパティを構成するには  
  
1.  パブリッシャーで [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)を実行します。 にパブリケーション名を指定し **@publication** ます。には**snapshot**または**continuous**のいずれかの値を指定し、次の **@repl_freq** スナップショット関連のパラメーターを1つ以上指定します。  
  
    -   **@alt_snapshot_folder**-このパブリケーションのスナップショットが、スナップショットの既定のフォルダーではなく、その場所からアクセスされる場合は、パスを指定します。  
  
    -   **@compress_snapshot**-代替スナップショットフォルダー内のスナップショットファイルを CAB ファイル形式で圧縮する場合は、値**true**を指定します。  
  
    -   **@pre_snapshot_script**-初期スナップショットが適用される前に、初期化中にサブスクライバーで実行される **.sql**ファイルのファイル名と完全パスを指定します。  
  
    -   **@post_snapshot_script**-初期スナップショットが適用された後に、初期化中にサブスクライバーで実行される **.sql**ファイルのファイル名と完全パスを指定します。  
  
    -   **@snapshot_in_defaultfolder**-スナップショットを既定以外の場所でのみ使用できる場合は、 **false**の値を指定します。  
  
2.  パブリケーションの作成の詳細については、「 [Create a Publication](create-a-publication.md)」を参照してください。  
  
### <a name="to-modify-snapshot-properties-of-an-existing-snapshot-or-transactional-publication"></a>既存のスナップショット パブリケーションまたはトランザクション パブリケーションに対してスナップショットのプロパティを変更するには  
  
1.  パブリッシャー側のパブリケーション データベースに対して [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)を実行します。 に**1**を指定し、 **@force_invalidate_snapshot** に次のいずれかの値を指定し **@property** ます。  
  
    -   **alt_snapshot_folder** -の代替スナップショットフォルダーへの新しいパスも指定し **@value** ます。  
  
    -   **compress_snapshot** -代替スナップショットフォルダー内のスナップショットファイルを**false** **true** **@value** CAB ファイル形式で圧縮するかどうかを示す true または false のいずれかの値を指定します。  
  
    -   **pre_snapshot_script** - **@value** 初期スナップショットが適用される前に、初期化時にサブスクライバーで実行される **.sql**ファイルのファイル名と完全パスを指定します。  
  
    -   **post_snapshot_script** - **@value** 初期スナップショットが適用された後に、初期化時にサブスクライバーで実行される **.sql**ファイルのファイル名と完全パスを指定します。  
  
    -   **snapshot_in_defaultfolder** - スナップショットを既定の場所に格納するかどうかを **true** または **false** で指定します。  
  
2.  (省略可) パブリッシャーのパブリケーション データベースで [sp_changepublication_snapshot](/sql/relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql)を実行します。 を指定し、 **@publication** 1 つまたは複数のスケジュールまたはセキュリティ資格情報のパラメーターを変更します。  
  
    > [!IMPORTANT]  
    >  可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 スクリプト ファイルに資格情報を格納する必要がある場合は、不正アクセスを防ぐために、ファイルを保護します。  
  
3.  コマンド プロンプトから [Replication Snapshot Agent](../agents/replication-snapshot-agent.md) を実行するか、スナップショット エージェント ジョブを起動して新しいスナップショットを生成します。 詳しくは、「 [初期スナップショットの作成および適用](../create-and-apply-the-initial-snapshot.md)」をご覧ください。  
  
### <a name="to-modify-snapshot-properties-of-an-existing-merge-publication"></a>既存のマージ パブリケーションに対してスナップショットのプロパティを変更するには  
  
1.  パブリッシャー側のパブリケーション データベースに対して [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)を実行します。 に**1**を指定し、 **@force_invalidate_snapshot** に次のいずれかの値を指定し **@property** ます。  
  
    -   **alt_snapshot_folder** -の代替スナップショットフォルダーへの新しいパスも指定し **@value** ます。  
  
    -   **compress_snapshot** -代替スナップショットフォルダー内のスナップショットファイルを**false** **true** **@value** CAB ファイル形式で圧縮するかどうかを示す true または false のいずれかの値を指定します。  
  
    -   **pre_snapshot_script** - **@value** 初期スナップショットが適用される前に、初期化時にサブスクライバーで実行される **.sql**ファイルのファイル名と完全パスを指定します。  
  
    -   **post_snapshot_script** - **@value** 初期スナップショットが適用された後に、初期化時にサブスクライバーで実行される **.sql**ファイルのファイル名と完全パスを指定します。  
  
    -   **snapshot_in_defaultfolder** - スナップショットを既定の場所に格納するかどうかを **true** または **false** で指定します。  
  
2.  コマンド プロンプトから [Replication Snapshot Agent](../agents/replication-snapshot-agent.md) を実行するか、スナップショット エージェント ジョブを起動して新しいスナップショットを生成します。 詳しくは、「 [初期スナップショットの作成および適用](../create-and-apply-the-initial-snapshot.md)」をご覧ください。  
  
## <a name="example"></a>例  
 次の例では、代替スナップショット フォルダーと圧縮スナップショットを使用したパブリケーションを作成します。  
  
 [!code-sql[HowTo#sp_mergealtsnapshot](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepubaltsnapshot.sql#sp_mergealtsnapshot)]  
  
## <a name="see-also"></a>参照  
 [代替スナップショットフォルダーの場所](../alternate-snapshot-folder-locations.md)   
 [圧縮されたスナップショット](../compressed-snapshots.md)   
 [スナップショットが適用される前および後のスクリプトの実行](../snapshot-options.md#execute-scripts-before-and-after-snapshot-is-applied)   
 [Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md)   
 [FTP によるスナップショットの転送](../transfer-snapshots-through-ftp.md)   
 [パブリケーションおよびアーティクルのプロパティの変更](change-publication-and-article-properties.md)  
  
  
