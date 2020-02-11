---
title: '[スナップショット エージェント](パブリケーションの新規作成ウィザード) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.configuresnapshotagent.f1
ms.assetid: 0257d4ee-1f7b-49fd-b4ef-65bfc1ef6951
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 20e4e015064dcf0e472c2f3c56ecabf4100e6fe7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62676577"
---
# <a name="snapshot-agent-new-publication-wizard"></a>[スナップショット エージェント] \(パブリケーションの新規作成ウィザード)
  [スナップショット エージェント] では、新しいサブスクリプションの初期化に使用されるパブリケーション スキーマおよびデータを含んでいるファイルを作成します。 既定では、スナップショット エージェントは、パブリケーションの新規作成ウィザードでパブリケーションが作成されるとすぐに実行されます。 続いて、エージェントが指定したスケジュールに従って実行されます。 エージェントが実行されるたびに新しいスナップショット ファイルが作成されるかどうかは、選択したレプリケーションおよびオプションの種類によって異なります。 詳細については、「[スナップショットの作成および適用](create-and-apply-the-snapshot.md)」を参照してください。  
  
 パラメーター化されたフィルターを使用するマージ パブリケーションでは、パブリケーション スナップショットの完了後、データの各パーティションのスナップショットを作成する必要があります。 詳しくは、「 [Snapshots for Merge Publications with Parameterized Filters](snapshots-for-merge-publications-with-parameterized-filters.md)」をご覧ください。  
  
## <a name="options"></a>オプション  
 **直ちにスナップショットを作成**する (マージレプリケーション) または**スナップショットをすぐに作成して、サブスクリプションを初期化できるようにスナップショットを保持する**(トランザクションレプリケーション)  
 パブリケーションの新規作成ウィザードが完了した後、すぐにスナップショットを作成する場合は、このチェック ボックスを選択します。 スナップショットが生成される前に **[パブリケーションのプロパティ]** ダイアログ ボックスでスナップショットのプロパティを変更する場合、またはスナップショットを使用せずにサブスクライバーを初期化する場合は、このチェック ボックスをオフにします。 詳細については、「 [Initialize a Transactional Subscription Without a Snapshot](initialize-a-transactional-subscription-without-a-snapshot.md)を使用して、サブスクリプションを手動で初期化する方法について説明します。  
  
> [!NOTE]  
>  ディストリビューション エージェントまたはマージ エージェントの適切なジョブを開始するために、ウィザードによりディストリビューターへの接続が要求される場合があります。  
  
 **スナップショットエージェントを次の時刻に実行するようにスケジュールする**  
 スナップショット エージェントを実行する既定のスケジュールを受け入れるか、 **[変更]** をクリックしてスケジュールを指定します。  
  
## <a name="see-also"></a>参照  
 [パブリケーションを作成する](publish/create-a-publication.md)   
 [初期スナップショットを作成して適用する](create-and-apply-the-initial-snapshot.md)   
 [パブリケーションのプロパティの表示および変更](publish/view-and-modify-publication-properties.md)   
 [スナップショットを使用したサブスクリプションの初期化](initialize-a-subscription-with-a-snapshot.md)   
 [データとデータベースオブジェクトのパブリッシュ](publish/publish-data-and-database-objects.md)   
 [レプリケーションエージェントの概要](agents/replication-agents-overview.md)  
  
  
