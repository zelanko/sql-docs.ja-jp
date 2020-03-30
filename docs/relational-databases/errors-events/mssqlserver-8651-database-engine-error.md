---
title: MSSQLSERVER_8651 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 8651 (Database Engine error)
ms.assetid: 4cc3498d-5449-4c4e-b1f9-3271831c725a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 01573bcf745efcdc1f4865ac9157c71ef65cb9bf
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2020
ms.locfileid: "72907701"
---
# <a name="mssqlserver_8651"></a>MSSQLSERVER_8651
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|8651|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|MEMGRANT_ERR|  
|メッセージ テキスト|最小クエリ メモリが使用できないので、要求された操作を実行できませんでした。 'min memory per query' サーバー構成オプションの設定値を減らしてください。|  
  
## <a name="explanation"></a>説明  
他のプロセスによってサーバー メモリが消費されています (サーバーにメモリ負荷がかかっています)。  
  
## <a name="user-action"></a>ユーザーの操作  
'min memory per query' サーバー構成オプションの設定値を小さくするか、サーバーに対するクエリ負荷を軽減します。  
  
メモリ エラーのトラブルシューティングに役立つ一般的な手順の概略を次に示します。  
  
1.  このサーバー上で、他のアプリケーションやサービスによってメモリが消費されていないか確認します。 重要度の低いアプリケーションやサービスのメモリ消費量が少なくなるように、構成を変更します。  
  
2.  **SQL Server: Buffer Manager** および **SQL Server: Memory Manager** のパフォーマンス モニター カウンターを確認します。  
  
3.  次に示す [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] メモリ構成パラメーターを確認します。  
  
    -   **max server memory**  
  
    -   **min server memory**  
  
    -   **min memory per query**  
  
    通常とは異なる設定がないか確認します。 必要に応じて、これらを修正します。 既定の設定については、SQL Server オンライン ブックの「サーバー構成オプションの設定」を参照してください。  
  
4.  ワークロード (同時セッション数や現在実行中のクエリ数など) をチェックします。  

次のアクションを実行すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で使用できるメモリを増やせる可能性があります。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のアプリケーションがリソースを消費している場合は、そのアプリケーションの実行を停止するか、別のサーバーで実行することを検討します。 これにより、外部的なメモリ負荷を軽減できます。  
  
-   **max server memory** を構成した場合は、設定値を大きくします。  
  
次の DBCC コマンドを実行して、いくつかの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] メモリ キャッシュを解放します。  
  
-   DBCC FREESYSTEMCACHE  
  
-   DBCC FREESESSIONCACHE  
  
-   DBCC FREEPROCCACHE  
  
問題が解決しない場合は、さらに調査します。ワークロードの軽減が必要になる場合もあります。  
  
## <a name="see-also"></a>参照  
[DBCC FREESYSTEMCACHE &#40;Transact-SQL&#41;](~/t-sql/database-console-commands/dbcc-freesystemcache-transact-sql.md)  
[DBCC FREESESSIONCACHE &#40;Transact-SQL&#41;](~/t-sql/database-console-commands/dbcc-freesessioncache-transact-sql.md)  
[DBCC FREEPROCCACHE &#40;Transact-SQL&#41;](~/t-sql/database-console-commands/dbcc-freeproccache-transact-sql.md)  
[サーバー構成オプション &#40;SQL Server&#41;](~/database-engine/configure-windows/server-configuration-options-sql-server.md)  
[SQL Server の Buffer Manager オブジェクト](~/relational-databases/performance-monitor/sql-server-buffer-manager-object.md)  
[SQL Server の Memory Manager オブジェクト](~/relational-databases/performance-monitor/sql-server-memory-manager-object.md)  
  
