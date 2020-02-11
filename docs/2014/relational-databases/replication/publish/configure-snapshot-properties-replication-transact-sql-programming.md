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
manager: craigg
ms.openlocfilehash: b03dd7f886cee5816d591034d1be63ece45d8d1d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63021335"
---
# <a name="configure-snapshot-properties-replication-transact-sql-programming"></a>スナップショットのプロパティの構成 (レプリケーション Transact-SQL プログラミング)
  スナップショットのプロパティは、レプリケーションのストアド プロシージャを使用し、プログラムから定義および変更できます。使用するストアド プロシージャは、パブリケーションの種類によって異なります。  
  
### <a name="to-configure-snapshot-properties-when-creating-a-snapshot-or-transactional-publication"></a>スナップショット パブリケーションまたはトランザクション パブリケーションを作成するときにスナップショットのプロパティを構成するには  
  
1.  パブリッシャーで [sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql)を実行します。 に**@publication**パブリケーション名を指定します。には**snapshot**または**continuous** **@repl_freq**のいずれかの値を指定し、次のスナップショット関連のパラメーターを1つ以上指定します。  
  
    -   **@alt_snapshot_folder**-このパブリケーションのスナップショットが、スナップショットの既定のフォルダーではなく、その場所からアクセスされる場合は、パスを指定します。  
  
    -   **@compress_snapshot**-代替スナップショットフォルダー内**** のスナップショットファイルを[!INCLUDE[msCoName](../../../includes/msconame-md.md)] CAB ファイル形式で圧縮する場合は、値 true を指定します。  
  
    -   **@pre_snapshot_script**-初期スナップショットが適用される前に、初期化中にサブスクライバーで実行される **.sql**ファイルのファイル名と完全パスを指定します。  
  
    -   **@post_snapshot_script**-初期スナップショットが適用された後に、初期化中にサブスクライバーで実行される **.sql**ファイルのファイル名と完全パスを指定します。  
  
    -   **@snapshot_in_defaultfolder**-スナップショットを既定以外の場所でのみ使用できる場合は、 **false**の値を指定します。  
  
     パブリケーションの作成の詳細については、「 [Create a Publication](create-a-publication.md)」を参照してください。  
  
### <a name="to-configure-snapshot-properties-when-creating-a-merge-publication"></a>マージ パブリケーションを作成するときにスナップショットのプロパティを構成するには  
  
1.  パブリッシャーで [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)を実行します。 に**@publication**パブリケーション名を指定します。には**snapshot**または**continuous** **@repl_freq**のいずれかの値を指定し、次のスナップショット関連のパラメーターを1つ以上指定します。  
  
    -   **@alt_snapshot_folder**-このパブリケーションのスナップショットが、スナップショットの既定のフォルダーではなく、その場所からアクセスされる場合は、パスを指定します。  
  
    -   **@compress_snapshot**-代替スナップショットフォルダー内のスナップショットファイルを CAB ファイル形式で圧縮する場合は、値**true**を指定します。  
  
    -   **@pre_snapshot_script**-初期スナップショットが適用される前に、初期化中にサブスクライバーで実行される **.sql**ファイルのファイル名と完全パスを指定します。  
  
    -   **@post_snapshot_script**-初期スナップショットが適用された後に、初期化中にサブスクライバーで実行される **.sql**ファイルのファイル名と完全パスを指定します。  
  
    -   **@snapshot_in_defaultfolder**-スナップショットを既定以外の場所でのみ使用できる場合は、 **false**の値を指定します。  
  
2.  パブリケーションの作成の詳細については、「 [Create a Publication](create-a-publication.md)」を参照してください。  
  
### <a name="to-modify-snapshot-properties-of-an-existing-snapshot-or-transactional-publication"></a>既存のスナップショット パブリケーションまたはトランザクション パブリケーションに対してスナップショットのプロパティを変更するには  
  
1.  パブリッシャー側のパブリケーション データベースに対して [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)を実行します。 に**@force_invalidate_snapshot** **@property** **1**を指定し、に次のいずれかの値を指定します。  
  
    -   **alt_snapshot_folder** -の代替スナップショットフォルダーへの**@value**新しいパスも指定します。  
  
    -   **compress_snapshot** -代替スナップショットフォルダー内のスナップショットファイルを CAB ファイル**@value**形式で圧縮するかどうかを示す**true**または**false**のいずれかの値を指定します。  
  
    -   **pre_snapshot_script** -初期スナップショット**@value**が適用される前に、初期化時にサブスクライバーで実行される **.sql**ファイルのファイル名と完全パスを指定します。  
  
    -   **post_snapshot_script** -初期スナップショット**@value**が適用された後に、初期化時にサブスクライバーで実行される **.sql**ファイルのファイル名と完全パスを指定します。  
  
    -   **snapshot_in_defaultfolder** -スナップショットを既定以外の場所でのみ使用可能にするかどうかを示す**true**または**false**の値も指定します。  
  
2.  (省略可) パブリッシャーのパブリケーション データベースで [sp_changepublication_snapshot](/sql/relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql)を実行します。 を**@publication**指定し、1つまたは複数のスケジュールまたはセキュリティ資格情報のパラメーターを変更します。  
  
    > [!IMPORTANT]  
    >  可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 スクリプト ファイルに資格情報を格納する必要がある場合は、不正アクセスを防ぐために、ファイルを保護します。  
  
3.  コマンド プロンプトから [Replication Snapshot Agent](../agents/replication-snapshot-agent.md) を実行するか、スナップショット エージェント ジョブを起動して新しいスナップショットを生成します。 詳しくは、「 [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md)」をご覧ください。  
  
### <a name="to-modify-snapshot-properties-of-an-existing-merge-publication"></a>既存のマージ パブリケーションに対してスナップショットのプロパティを変更するには  
  
1.  パブリッシャー側のパブリケーション データベースに対して [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)を実行します。 に**@force_invalidate_snapshot** **@property** **1**を指定し、に次のいずれかの値を指定します。  
  
    -   **alt_snapshot_folder** -の代替スナップショットフォルダーへの**@value**新しいパスも指定します。  
  
    -   **compress_snapshot** -代替スナップショットフォルダー内のスナップショットファイルを CAB ファイル**@value**形式で圧縮するかどうかを示す**true**または**false**のいずれかの値を指定します。  
  
    -   **pre_snapshot_script** -初期スナップショット**@value**が適用される前に、初期化時にサブスクライバーで実行される **.sql**ファイルのファイル名と完全パスを指定します。  
  
    -   **post_snapshot_script** -初期スナップショット**@value**が適用された後に、初期化時にサブスクライバーで実行される **.sql**ファイルのファイル名と完全パスを指定します。  
  
    -   **snapshot_in_defaultfolder** -スナップショットを既定以外の場所でのみ使用可能にするかどうかを示す**true**または**false**の値も指定します。  
  
2.  コマンド プロンプトから [Replication Snapshot Agent](../agents/replication-snapshot-agent.md) を実行するか、スナップショット エージェント ジョブを起動して新しいスナップショットを生成します。 詳しくは、「 [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md)」をご覧ください。  
  
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
  
  
