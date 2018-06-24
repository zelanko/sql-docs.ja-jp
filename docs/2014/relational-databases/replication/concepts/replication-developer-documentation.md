---
title: 開発者&#39;ガイド (レプリケーション) |Microsoft ドキュメント
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- replication
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- developer's guide [SQL Server replication]
- programming [SQL Server replication]
- replication [SQL Server], development
ms.assetid: 7ee134ae-1cab-4a35-8017-8ac6d8fc64b6
caps.latest.revision: 39
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: fb0ffaba9b07a24c6d3ae27e442c4b4e41d8f255
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36075260"
---
# <a name="developer39s-guide-replication"></a>開発者&#39;ガイド (レプリケーション)
  レプリケーション トポロジをプログラムから構成、保守、監視できれば、繰り返し行うレプリケーション タスクを効率化できるという開発者側のメリットに加え、レプリケーション ベースのアプリケーションを快適に使用できるというユーザー側のメリットも生まれます。 レプリケーションをプログラミングすることにより、レプリケーションのストアド プロシージャやレプリケーション エージェントの実行可能ファイルに関する知識がないエンド ユーザーに、[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] に実装されているレプリケーション ユーザー インターフェイスの使用を強要することなく、カスタマイズされたレプリケーション機能を提供できます。  
  
 プログラムからレプリケーション サービスにアクセスすることによって効果が期待できるアプリケーション開発のシナリオを次に示します。  
  
-   既存のエンド ユーザー アプリケーションにレプリケーション機能を追加する (ユーザーがボタンをクリックするとプル サブスクリプションが同期されるなど)。  
  
-   レプリケーションをリモートから管理するための Web ベースのユーザー インターフェイスを作成する。  
  
-   カスタム ユーザー インターフェイスを作成する (一部の管理機能だけを公開する、複数のレプリケーション トポロジをリモートから一元管理できるようにする、管理機能と同期機能を組み合わせるなど)。  
  
-   既存の監視ツールを強化する (パブリケーションやサブスクリプションの状態をディストリビューター側で監視する機能を追加するなど)。  
  
-   Oracle パブリッシャーのサブスクリプションを管理または同期するカスタム アプリケーションを作成する。  
  
-   マージ サブスクリプションの同期時に実行されるビジネス ルールを独自に作成する。  
  
-   新しいサブスクライバーを構成する際に繰り返し実行することのできる [!INCLUDE[tsql](../../../includes/tsql-md.md)] スクリプトを生成する。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、レプリケーション エージェントを制御したり、レプリケーション トポロジを管理、監視する作業をプログラムから行うことができます。 レプリケーションのプログラミングの詳細については、「[レプリケーションのプログラミング概念](replication-programming-concepts.md)」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [レプリケーションのプログラミング概念](replication-programming-concepts.md)  
 レプリケーションを使ったアプリケーション開発の計画手順について説明します。  
  
 [Replication System Stored Procedures Concepts](replication-system-stored-procedures-concepts.md)  
 システム ストアド プロシージャを使用した、レプリケーション トポロジのプログラム アクセスの方法を説明します。  
  
 [レプリケーション管理オブジェクトの概念](replication-management-objects-concepts.md)  
 レプリケーション管理オブジェクト (RMO) を使用するための概念について説明します。 これは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のレプリケーション機能をカプセル化するマネージ コード アセンブリです。  
  
 [レプリケーション エージェント実行可能ファイルの概念](replication-agent-executables-concepts.md)  
 レプリケーション エージェントの実行可能ファイルの使用について説明します。  
  
 [開発者ガイド: 操作方法に関するトピック &#40;レプリケーション&#41;](../developer-s-guide-how-to-topics-replication.md)  
 レプリケーションに関連した操作方法のトピック一覧を示します。  
  
  