---
title: "レプリケーション開発者のドキュメント | Microsoft Docs"
ms.custom:
- rickbyh
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- developer's guide [SQL Server replication]
- programming [SQL Server replication]
- replication [SQL Server], development
ms.assetid: 7ee134ae-1cab-4a35-8017-8ac6d8fc64b6
caps.latest.revision: 40
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: b44693e1193670ee6b8f50f6fd7bd8a94181e2be
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="replication-developer-documentation"></a>レプリケーション開発者のドキュメント
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  レプリケーション トポロジをプログラムから構成、保守、監視できれば、繰り返し行うレプリケーション タスクを効率化できるという開発者側のメリットに加え、レプリケーション ベースのアプリケーションを快適に使用できるというユーザー側のメリットも生まれます。 レプリケーションをプログラミングすることにより、レプリケーションのストアド プロシージャやレプリケーション エージェントの実行可能ファイルに関する知識がないエンド ユーザーに、[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] に実装されているレプリケーション ユーザー インターフェイスの使用を強要することなく、カスタマイズされたレプリケーション機能を提供できます。  
  
 プログラムからレプリケーション サービスにアクセスすることによって効果が期待できるアプリケーション開発のシナリオを次に示します。  
  
-   既存のエンド ユーザー アプリケーションにレプリケーション機能を追加する (ユーザーがボタンをクリックするとプル サブスクリプションが同期されるなど)。  
  
-   レプリケーションをリモートから管理するための Web ベースのユーザー インターフェイスを作成する。  
  
-   カスタム ユーザー インターフェイスを作成する (一部の管理機能だけを公開する、複数のレプリケーション トポロジをリモートから一元管理できるようにする、管理機能と同期機能を組み合わせるなど)。  
  
-   既存の監視ツールを強化する (パブリケーションやサブスクリプションの状態をディストリビューター側で監視する機能を追加するなど)。  
  
-   Oracle パブリッシャーのサブスクリプションを管理または同期するカスタム アプリケーションを作成する。  
  
-   マージ サブスクリプションの同期時に実行されるビジネス ルールを独自に作成する。  
  
-   新しいサブスクライバーを構成する際に繰り返し実行することのできる [!INCLUDE[tsql](../../../includes/tsql-md.md)] スクリプトを生成する。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、レプリケーション エージェントを制御したり、レプリケーション トポロジを管理、監視する作業をプログラムから行うことができます。 レプリケーションのプログラミングの詳細については、「[レプリケーションのプログラミング概念](../../../relational-databases/replication/concepts/replication-programming-concepts.md)」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [レプリケーションのプログラミング概念](../../../relational-databases/replication/concepts/replication-programming-concepts.md)  
 レプリケーションを使ったアプリケーション開発の計画手順について説明します。  
  
 [レプリケーション システム ストアド プロシージャの概念](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)  
 システム ストアド プロシージャを使用した、レプリケーション トポロジのプログラム アクセスの方法を説明します。  
  
 [レプリケーション管理オブジェクトの概念](../../../relational-databases/replication/concepts/replication-management-objects-concepts.md)  
 レプリケーション管理オブジェクト (RMO) を使用するための概念について説明します。 これは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のレプリケーション機能をカプセル化するマネージ コード アセンブリです。  
  
 [レプリケーション エージェント実行可能ファイルの概念](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)  
 レプリケーション エージェントの実行可能ファイルの使用について説明します。  
  
 [開発者ガイド: 操作方法に関するトピック &#40;レプリケーション&#41;](../../../relational-databases/replication/concepts/developer-s-guide-how-to-topics-replication.md)  
 レプリケーションに関連した操作方法のトピック一覧を示します。  
  
  

