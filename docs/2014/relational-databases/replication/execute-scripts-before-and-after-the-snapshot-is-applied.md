---
title: スナップショットが適用される前および後のスクリプトの実行 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], scripts
- scripts [SQL Server replication], snapshots
- snapshot replication [SQL Server], scripts
- scripts [SQL Server replication]
ms.assetid: 9a6872c2-9bed-477f-9d2f-332d640edcf2
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8c63393685e6fdd80078752ab21eb7ce81244707
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48191612"
---
# <a name="execute-scripts-before-and-after-the-snapshot-is-applied"></a>スナップショットが適用される前および後のスクリプトの実行
  スナップショットが適用される前または後に、スクリプトを指定してサブスクライバーで実行できます。 スクリプトは、各サブスクライバーでのログインの作成やスキーマ (オブジェクト所有者) の作成など、さまざまな理由で使用できます。  
  
 各スクリプトに対してファイルの場所を指定すると、スナップショットの処理が行われるたびに、スナップショット エージェントはスクリプト ファイルを現在のスナップショット フォルダーにコピーします。 ディストリビューション エージェントまたはマージ エージェントは、スナップショットを適用するときに、レプリケートされたオブジェクト スクリプトの前にプリスナップショット スクリプトを実行します。 ディストリビューション エージェントまたはマージ エージェントは、他のすべてのレプリケートされたオブジェクト スクリプトおよびデータが適用された後にポストスナップショット スクリプトを実行します。 スナップショットの適用が完了し、スクリプト ファイルが正常に実行された後、スクリプト ファイルはサブスクライバー上の作業ディレクトリから削除されます。  
  
 スクリプトは、 **sqlcmd** ユーティリティを起動することで実行されます。 スクリプトを配置する前に、 **sqlcmd** を使用して実行し、想定どおりに実行されることを確認します。 スナップショットが適用される前後に実行されるスクリプトの内容は、繰り返し使用できる必要があります。 たとえば、スクリプト内でテーブルを作成する場合、最初にテーブルの存在を確認し、そのテーブルが存在する場合に適切な動作を行う必要があります。 既にスクリプトが適用されているサブスクリプションを再初期化する必要がある場合、スクリプトは繰り返し使用できる必要があります。再初期化中に新しいスナップショットを適用すると、そのスクリプトが再度適用されるためです。  
  
 スナップショット ファイルを圧縮し、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] CAB ファイル形式にする場合は、スクリプトも圧縮され、CAB ファイルに格納されます。 圧縮スナップショット ファイルがサブスクライバーに転送され、サブスクライバー上の作業ディレクトリで圧縮解除された後は、プリスナップショット スクリプトとして指定されたスクリプトが実行されます。 同じように、ポストスナップショット スクリプトは、スナップショット適用の最後のステップとしてサブスクライバーで解凍および実行されます。  
  
 **スナップショットが適用される前および後にスクリプトを実行するには**  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: [スナップショット適用前および適用後にスクリプトを実行する方法 \(SQL Server Management Studio\)](execute-scripts-before-and-after-a-snapshot-is-applied.md)  
  
-   レプリケーション [!INCLUDE[tsql](../../includes/tsql-md.md)] プログラミング: [スナップショットのプロパティの構成 &#40;レプリケーション Transact-SQL プログラミング&#41;](publish/configure-snapshot-properties-replication-transact-sql-programming.md)  
  
## <a name="see-also"></a>参照  
 [Initialize a Subscription with a Snapshot (スナップショットを使用したサブスクリプションの初期化)](initialize-a-subscription-with-a-snapshot.md)   
 [スナップショット オプション](snapshot-options.md)  
  
  
