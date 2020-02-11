---
title: パブリケーション情報、[エージェント] (トランザクション パブリケーション) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.downlevelagents.tran.f1
ms.assetid: 38ef2f54-53bb-4053-876d-86f8f06a4519
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7a4542370eff5ad631701f0bf988929ad56e8799
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63021808"
---
# <a name="publication-information-agents-transactional-publication"></a>パブリケーション情報、[エージェント] \(トランザクション パブリケーション)
  
  **[エージェント]** タブには、選択したパブリケーションにおけるエージェントの要約情報が表示されます。 すべてのトランザクション パブリケーションのスナップショット エージェントとログ リーダー エージェントの情報が表示されます。 キュー更新サブスクリプション用に有効になっているトランザクション パブリケーションについては、キュー リーダー エージェントに関する情報が表示されます。  
  
## <a name="options"></a>オプション  
 エージェントに関する詳細情報やタスクを調べるには、そのエージェントの行を右クリックし、ショートカット メニューのオプションをクリックします。 グリッドにデータを表示する方法を変更するには、グリッドを右クリックし、次のいずれかのオプションをクリックします。  
  
-   **Sort**: [**列の並べ替え**] ダイアログボックス内の1つまたは複数の列を基準にして並べ替えを行います。  
  
-   表示**する列の選択**: 表示する列と、[**列の選択**] ダイアログボックスで表示する順序を選択します。  
  
-   [**フィルター**]: [**フィルターの設定**] ダイアログボックスの列の値に基づいて、グリッド内の行をフィルター処理します。  
  
-   [**フィルターのクリア**]: グリッドのフィルター設定をすべてクリアします。  
  
 フィルター設定は各グリッドに固有です。 列の選択と並べ替えは、各パブリッシャーのパブリケーション グリッドなど、同じ種類のすべてのグリッドに適用されます。  
  
 **状態**  
 パブリケーションに関連付けられている、各レプリケーション エージェントの状態です。 表示される状態の種類を、次に示します。  
  
-   エラー  
  
-   [失敗したコマンドの再試行]  
  
-   [実行されていません]  
  
-   実行中  
  
-   Completed  
  
 **エージェント**  
 パブリケーションに関連付けられている、各レプリケーション エージェントの名前です。 ディストリビューション エージェントは、このパブリケーションに対するサブスクリプションに関連付けられます。 詳細については、「[レプリケーションモニターを使用して情報を表示し、タスクを実行する](monitor/view-information-and-perform-tasks-replication-monitor.md)」を参照してください。  
  
 **前回の開始時刻**  
 エージェントが最後に起動された時刻です。  
  
 **Duration**  
 エージェントが実行された時間の長さです。 この時間は、エージェントが現在実行中の場合は経過時間、エージェントが以前に実行されている場合は合計時間を表します。  
  
 **最後の操作**  
 エージェントが最後に実行されたときに最後に実行されたアクションです。  
  
## <a name="see-also"></a>参照  
 [レプリケーション モニターの開始](monitor/start-the-replication-monitor.md)   
 [レプリケーションモニターを使用して情報を表示し、タスクを実行する](monitor/view-information-and-perform-tasks-replication-monitor.md)   
 [レプリケーションの監視](monitoring-replication.md)  
  
  
