---
title: "スナップショットを使用したサブスクリプションの初期化 | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- snapshots [SQL Server replication], initializing subscriptions
- initializing subscriptions [SQL Server replication], snapshots
ms.assetid: 77a9ade2-cdc0-4ae9-a02d-6e29d7c2ada0
caps.latest.revision: 32
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 85768c39b282ccfda1df1e68d42a1f6b3985bc46
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="initialize-a-subscription-with-a-snapshot"></a>スナップショットを使用したサブスクリプションの初期化
  パブリケーションを作成すると、通常は初期スナップショットが作成され、スナップショット フォルダーにコピーされます (この動作は、パブリケーションの新規作成ウィザードを使用して作成されたマージ パブリケーションに対して既定で実行されます)。 その後スナップショットは、サブスクリプションの最初の同期時に、ディストリビューション エージェント (トランザクション パブリケーションおよびスナップショット パブリケーションの場合) またはマージ エージェント (マージ パブリケーションの場合) によってサブスクライバーに適用されます。 スナップショット処理は、パブリケーションの種類によって変わります。  
  
-   パラメーター化されたフィルターを使用しないスナップショット パブリケーション、トランザクション パブリケーション、またはマージ パブリケーションに対するスナップショットの場合、スナップショットにはスキーマとデータが含まれ、一括コピー プログラム (bcp) ファイルとして作成されます。また、レプリケーションで必要な制約、拡張プロパティ、インデックス、トリガー、およびシステム テーブルも含まれます。 スナップショットの作成と適用の詳細については、「[Create and Apply the Snapshot](../../relational-databases/replication/create-and-apply-the-snapshot.md)」(スナップショットの作成と適用) を参照してください。  
  
-   パラメーター化されたフィルターを使用するマージ パブリケーションに対するスナップショットの場合は、2 段階の処理でスナップショットが作成されます。 まず、パブリッシュされたオブジェクトのレプリケーション スクリプトとスキーマが含まれるスキーマ スナップショットが作成されます。ただしデータは含まれません。 次に、スキーマ スナップショットからコピーしたスクリプトとスキーマが含まれるスナップショットと、サブスクリプションのパーティションに属するデータを使用して、各サブスクリプションが初期化されます。 詳細については、「 [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md)」を参照してください。  
  
 スナップショットは、レプリケーションの種類やパブリケーションのアーティクルに応じて異なるファイルで構成されます。 これらのファイルは、ディストリビューターの構成時に指定した既定のスナップショット フォルダーか、パブリケーションを作成する際に指定した代替スナップショット フォルダーにコピーされます。  
  
|レプリケーションの種類|通常のスナップショット ファイル|  
|-------------------------|---------------------------|  
|スナップショット レプリケーションまたはトランザクション レプリケーション|スキーマ (.sch)、データ (.bcp)、制約とインデックス (.dri)、制約 (.idx)、トリガー (.trg) (サブスクライバーの更新専用)、圧縮スナップショットファイル (.cab)|  
|マージ レプリケーション|スキーマ (.sch)、データ (.bcp)、制約とインデックス (.dri)、トリガー (.trg)、システム テーブル データ (.sys)、競合テーブル (.cft)、圧縮スナップショットファイル (.cab)|  
  
 ある時点でスナップショットの転送が中断された場合、転送は自動的に再開され、既に転送が完了したファイルは再送されません。 スナップショット エージェントの配信単位は、各パブリケーション アーティクルに対する bcp ファイルであるため、部分的に配信されたファイルは再度全体を配信する必要があります。 しかし、スナップショットの再開機能を使うことで、転送されるデータ量が大幅に削減され、接続が不安定な場合でもタイムリーにスナップショットを配信できます。  
  
## <a name="snapshot-options"></a>スナップショット オプション  
 スナップショットを使用してサブスクリプションを初期化する際には、いくつかのオプションがあります。 可能な代替手段としては以下の方法があります。  
  
-   既定のスナップショット フォルダーを代替または追加する場所として、代替スナップショット フォルダーの場所を指定できます。 詳細については、「 [Alternate Snapshot Folder Locations](../../relational-databases/replication/alternate-snapshot-folder-locations.md)」を参照してください。  
  
-   リムーバブル メディア上に格納するためや低速なネットワーク上で転送するための圧縮スナップショットを使用できます。 詳細については、「 [Compressed Snapshots](../../relational-databases/replication/compressed-snapshots.md)」を参照してください。  
  
-   スナップショットを適用する前または後に Transact-SQL スクリプトを実行できます。 詳細については、「[スナップショットが適用される前および後のスクリプトの実行](../../relational-databases/replication/execute-scripts-before-and-after-the-snapshot-is-applied.md)」を参照してください。  
  
-   ファイル転送プロトコル (FTP) を使用してスナップショット ファイルを転送できます。 詳細については、「[FTP によるスナップショットの転送](../../relational-databases/replication/transfer-snapshots-through-ftp.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [サブスクリプションの初期化](../../relational-databases/replication/initialize-a-subscription.md)   
 [スナップショット フォルダーのセキュリティ保護](../../relational-databases/replication/security/secure-the-snapshot-folder.md)  
  
  
