---
title: MSSQL_ENG021076 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021076 error
ms.assetid: 612e5c59-ba3e-49c3-a3df-56bac3d850a2
caps.latest.revision: 15
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 070d6161cd12414f924da5afcd5a2b9a3d48fedb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32959387"
---
# <a name="mssqleng021076"></a>MSSQL_ENG021076
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|21076|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|アーティクル '%s' の初期スナップショットはまだ使用できません。|  
  
## <a name="explanation"></a>説明  
 エラー MSSQL_ENG021076 は、スナップショット エージェントがスナップショットの生成を終える前にディストリビューション エージェントが開始すると発生する可能性があります。 このエラーは、パブリケーションに 1 つのアーティクルが含まれる場合にのみ発生します。 パブリケーションに複数のアーティクルがある場合は、代わりに MSSQL_ENG021075 が発生します。 詳細については、「 [MSSQL_ENG021075](../../relational-databases/replication/mssql-eng021075.md)」を参照してください。  
  
## <a name="user-action"></a>ユーザーの操作  
 サブスクリプションが作成されてから、または最後にサブスクリプションの再初期化を選択してから、一度もパブリケーションのスナップショット エージェントが開始されていない場合は、スナップショット エージェントを開始し、完了した後でディストリビューション エージェントを開始します。 詳細については、「[スナップショットの作成および適用](../../relational-databases/replication/create-and-apply-the-snapshot.md)」を参照してください。  
  
 スナップショット エージェントが完了しない場合は、スナップショット エージェントの履歴でエラーを確認して対応します。 レプリケーション モニターでエージェントの状態やエラーの詳細を表示する方法については、「[パブリケーションに関連付けられているエージェントの情報を表示し、タスクを実行する &#40;レプリケーション モニター&#41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-publication-agents.md)」を参照してください。  
  
 エラーの発生が継続する場合は、エージェントのログ記録を増やし、ログの出力ファイルを指定します。 エラーのコンテキストによっては、エラーや他のエラー メッセージにつながる手順が示される可能性もあります。  
  
## <a name="see-also"></a>参照  
 [エラーとイベントのリファレンス &#40;レプリケーション&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
