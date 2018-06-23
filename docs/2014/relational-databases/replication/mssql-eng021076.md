---
title: MSSQL_ENG021076 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG021076 error
ms.assetid: 612e5c59-ba3e-49c3-a3df-56bac3d850a2
caps.latest.revision: 14
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 087d6edb5fcb9fb3c5a36949b5a92eb725f3d2bb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36178414"
---
# <a name="mssqleng021076"></a>MSSQL_ENG021076
    
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
 エラー MSSQL_ENG021076 は、スナップショット エージェントがスナップショットの生成を終える前にディストリビューション エージェントが開始すると発生する可能性があります。 このエラーは、パブリケーションに 1 つのアーティクルが含まれる場合にのみ発生します。 パブリケーションに複数のアーティクルがある場合は、代わりに MSSQL_ENG021075 が発生します。 詳細については、「 [MSSQL_ENG021075](mssql-eng021075.md)」を参照してください。  
  
## <a name="user-action"></a>ユーザーの操作  
 サブスクリプションが作成されてから、または最後にサブスクリプションの再初期化を選択してから、一度もパブリケーションのスナップショット エージェントが開始されていない場合は、スナップショット エージェントを開始し、完了した後でディストリビューション エージェントを開始します。 詳細については、「[スナップショットの作成および適用](create-and-apply-the-snapshot.md)」を参照してください。  
  
 スナップショット エージェントが完了しない場合は、スナップショット エージェントの履歴でエラーを確認して対応します。 レプリケーション モニターでエージェントの状態やエラーの詳細を表示する方法については、「[パブリケーションに関連付けられているエージェントの情報を表示し、タスクを実行する &#40;レプリケーション モニター&#41;](monitor/view-information-and-perform-tasks-for-publication-agents.md)」を参照してください。  
  
 エラーの発生が継続する場合は、エージェントのログ記録を増やし、ログの出力ファイルを指定します。 エラーのコンテキストによっては、エラーや他のエラー メッセージにつながる手順が示される可能性もあります。  
  
## <a name="see-also"></a>参照  
 [エラーとイベントのリファレンス &#40;レプリケーション&#41;](errors-and-events-reference-replication.md)  
  
  