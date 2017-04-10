---
title: "スナップショットのプロパティの構成 (レプリケーション Transact-SQL プログラミング) | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "スナップショット [SQL Server レプリケーション], プロパティ"
ms.assetid: 978d150f-8971-458a-ab2b-3beba5937b46
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 37
---
# スナップショットのプロパティの構成 (レプリケーション Transact-SQL プログラミング)
  スナップショットのプロパティは、レプリケーションのストアド プロシージャを使用し、プログラムから定義および変更できます。使用するストアド プロシージャは、パブリケーションの種類によって異なります。  
  
### スナップショット パブリケーションまたはトランザクション パブリケーションを作成するときにスナップショットのプロパティを構成するには  
  
1.  パブリッシャーで実行 [sp_addpublication](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)します。 パブリケーション名を指定 **@publication**, 、いずれかの値 **スナップショット** または **継続的な** の **@repl_freq**, 、および 1 つ以上のスナップショットに関連する次のパラメーター。  
  
    -   **@alt_snapshot_folder** -このパブリケーションのスナップショットがスナップショットの既定のフォルダーではなく、その場所からアクセスされる場合は、パスを指定します。  
  
    -   **@compress_snapshot** -の値を指定して **true** で代替スナップショット フォルダー内のスナップショット ファイルを圧縮するかどうか、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] CAB ファイル形式です。  
  
    -   **@pre_snapshot_script** -ファイル名と完全なパスの指定、 **.sql** で実行されるサブスクライバーの初期化中に、初期スナップショットが適用される前にファイルです。  
  
    -   **@post_snapshot_script** -ファイル名と完全なパスの指定、 **.sql** は後で実行されるサブスクライバーの初期化中に、初期スナップショットが適用されるファイル。  
  
    -   **@snapshot_in_defaultfolder** -の値を指定して **false** 場合は、既定以外の場所にのみ、スナップショットは使用できません。  
  
     パブリケーションの作成の詳細については、次を参照してください。 [パブリケーションを作成](../../../relational-databases/replication/publish/create-a-publication.md)します。  
  
### マージ パブリケーションを作成するときにスナップショットのプロパティを構成するには  
  
1.  パブリッシャーで実行 [sp_addmergepublication](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)します。 パブリケーション名を指定 **@publication**, 、いずれかの値 **スナップショット** または **継続的な** の **@repl_freq**, 、および 1 つ以上のスナップショットに関連する次のパラメーター。  
  
    -   **@alt_snapshot_folder** -このパブリケーションのスナップショットがスナップショットの既定のフォルダーではなく、その場所からアクセスされる場合は、パスを指定します。  
  
    -   **@compress_snapshot** -の値を指定して **true** 代替スナップショット フォルダー内のスナップショット ファイルを CAB ファイル形式で圧縮するかどうか。  
  
    -   **@pre_snapshot_script** -ファイル名と完全なパスの指定、 **.sql** で実行されるサブスクライバーの初期化中に、初期スナップショットが適用される前にファイルです。  
  
    -   **@post_snapshot_script** -ファイル名と完全なパスの指定、 **.sql** は後で実行されるサブスクライバーの初期化中に、初期スナップショットが適用されるファイル。  
  
    -   **@snapshot_in_defaultfolder** -の値を指定して **false** 場合は、既定以外の場所にのみ、スナップショットは使用できません。  
  
2.  パブリケーションの作成の詳細については、次を参照してください。 [パブリケーションを作成](../../../relational-databases/replication/publish/create-a-publication.md)します。  
  
### 既存のスナップショット パブリケーションまたはトランザクション パブリケーションに対してスナップショットのプロパティを変更するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md)します。 値を指定して **1** の **@force_invalidate_snapshot** し、次のいずれかの値を **@property**:  
  
    -   **alt_snapshot_folder** -の代替スナップショット フォルダーへの新しいパスを指定しても **@value**します。  
  
    -   **compress_snapshot** のいずれかの値も指定する **true** または **false** の **@value** 代替スナップショット フォルダー内のスナップショット ファイルを CAB ファイル形式で圧縮するかどうかを示すためにします。  
  
    -   **pre_snapshot_script** - **@value** の完全なパスとファイルの名前を指定する **.sql** で実行されるサブスクライバーの初期化中に、初期スナップショットが適用される前にファイルです。  
  
    -   **post_snapshot_script** - **@value** ファイル名と完全なパスの指定、 **.sql** は後で実行されるサブスクライバーの初期化中に、初期スナップショットが適用されるファイル。  
  
    -   **snapshot_in_defaultfolder** のいずれかの値も指定する **true** または **false** 既定以外の場所にのみ、スナップショットが使用できるかどうかを示す。  
  
2.  (省略可能)パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_changepublication_snapshot](../../../relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql.md)します。 指定 **@publication** と 1 つ以上のスケジュール設定やセキュリティ資格情報パラメーターを変更します。  
  
    > [!IMPORTANT]  
    >  可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 スクリプト ファイルに資格情報を格納する必要がある場合は、不正アクセスを防ぐために、ファイルを保護します。  
  
3.  実行、 [レプリケーション スナップショット エージェント](../../../relational-databases/replication/agents/replication-snapshot-agent.md) からコマンド プロンプト] または [新しいスナップショットを生成するスナップショット エージェント ジョブを開始します。 詳細については、「 [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)」を参照してください。  
  
### 既存のマージ パブリケーションに対してスナップショットのプロパティを変更するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md)します。 値を指定して **1** の **@force_invalidate_snapshot** し、次のいずれかの値を **@property**:  
  
    -   **alt_snapshot_folder** -の代替スナップショット フォルダーへの新しいパスを指定しても **@value**します。  
  
    -   **compress_snapshot** のいずれかの値も指定する **true** または **false** の **@value** 代替スナップショット フォルダー内のスナップショット ファイルを CAB ファイル形式で圧縮するかどうかを示すためにします。  
  
    -   **pre_snapshot_script** - **@value** の完全なパスとファイルの名前を指定する **.sql** で実行されるサブスクライバーの初期化中に、初期スナップショットが適用される前にファイルです。  
  
    -   **post_snapshot_script** - **@value** ファイル名と完全なパスの指定、 **.sql** は後で実行されるサブスクライバーの初期化中に、初期スナップショットが適用されるファイル。  
  
    -   **snapshot_in_defaultfolder** のいずれかの値も指定する **true** または **false** 既定以外の場所にのみ、スナップショットが使用できるかどうかを示す。  
  
2.  実行、 [レプリケーション スナップショット エージェント](../../../relational-databases/replication/agents/replication-snapshot-agent.md) からコマンド プロンプト] または [新しいスナップショットを生成するスナップショット エージェント ジョブを開始します。 詳細については、「 [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)」を参照してください。  
  
## 例  
 次の例では、代替スナップショット フォルダーと圧縮スナップショットを使用したパブリケーションを作成します。  
  
 [!code-sql[HowTo#sp_mergealtsnapshot](../../../relational-databases/replication/codesnippet/tsql/configure-snapshot-prope_1.sql)]  
  
## 参照  
 [スナップショット フォルダーの代替位置](../../../relational-databases/replication/alternate-snapshot-folder-locations.md)   
 [圧縮スナップショット](../../../relational-databases/replication/compressed-snapshots.md)   
 [スナップショットが適用される前および後のスクリプトの実行](../../../relational-databases/replication/execute-scripts-before-and-after-the-snapshot-is-applied.md)   
 [レプリケーション システム ストアド プロシージャの概念](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [FTP によるスナップショットの転送](../../../relational-databases/replication/transfer-snapshots-through-ftp.md)   
 [パブリケーションおよびアーティクルのプロパティの変更](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)  
  
  