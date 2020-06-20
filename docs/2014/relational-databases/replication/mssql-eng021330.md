---
title: MSSQL_ENG021330 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021330 error
ms.assetid: e2bb2e21-62a7-4689-b68b-bdfba3fdd985
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4d13a1139d4af61b576c00c3ec4efa42f0267ba8
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85065822"
---
# <a name="mssql_eng021330"></a>MSSQL_ENG021330
    
## <a name="message-details"></a>メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|21330|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|レプリケーション作業ディレクトリにサブディレクトリを作成できませんでした。(%ls)|  
  
## <a name="explanation"></a>説明  
 このエラーは、サブスクリプションが手動で初期化され、レプリケーション スクリプトを保存するディレクトリの作成で問題があった場合に発生する可能性があります。 このエラーは、権限に関する問題によって発生する可能性があります。サブスクリプションがスナップショットを使用しないで初期化される場合、パブリッシャーで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスの実行に使用されるアカウントは、ディストリビューターのスナップショット フォルダーに対する書き込み権限を持つ必要があります。  
  
## <a name="user-action"></a>ユーザーの操作  
 スナップショット フォルダーに対して正しいパスが指定されていること、およびパブリッシャーで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスの実行に使用されるアカウントが十分な権限を持っていることを確認します。  
  
## <a name="see-also"></a>参照  
 [既定のスナップショットの場所の指定](snapshot-options.md#snapshot-folder-locations)   
 [エラーとイベントのリファレンス &#40;レプリケーション&#41;](errors-and-events-reference-replication.md)   
 [スナップショットを使用しないトランザクション サブスクリプションの初期化](initialize-a-transactional-subscription-without-a-snapshot.md)  
  
  
