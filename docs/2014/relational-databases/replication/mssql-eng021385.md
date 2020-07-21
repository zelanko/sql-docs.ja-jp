---
title: MSSQL_ENG021385 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021385 error
ms.assetid: a2c0444f-d97b-4760-8905-3574791c2e26
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2d137fceaed44ebe79ca1e5d3735681539e3a462
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85010080"
---
# <a name="mssql_eng021385"></a>MSSQL_ENG021385
    
## <a name="message-details"></a>メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|21385|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|スナップショットはパブリケーション '%s' の処理に失敗しました。 アクティブなスキーマ変更または新しいアーティクルが追加されたことが原因の可能性があります。|  
  
## <a name="explanation"></a>説明  
 このエラーは、アーティクルの追加や削除、パブリッシュされたオブジェクトへのスキーマ変更の実行など、パブリケーション データベースに対する変更が実行中のときに、スナップショット エージェントが起動されると発生します。  
  
## <a name="user-action"></a>ユーザーの操作  
 パブリケーション データベースに対する変更が完了した後に、スナップショット エージェントを再起動します。 詳細については、「[レプリケーション エージェントを起動および停止する &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)」および「[レプリケーション エージェント実行可能ファイルの概念](concepts/replication-agent-executables-concepts.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [エラーとイベントのリファレンス &#40;レプリケーション&#41;](errors-and-events-reference-replication.md)  
  
  
