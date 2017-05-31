---
title: "チュートリアル: モバイル クライアントとの間のデータのレプリケーション | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: af673514-30c7-403a-9d18-d01e1a095115
caps.latest.revision: 24
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 89f4810fae7ce3ee89b7b13f93f7f0298b93bace
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="tutorial-replicating-data-with-mobile-clients"></a>チュートリアル : モバイル クライアントとの間のデータのレプリケーション
レプリケーションは、中央のサーバーと、常時接続でないモバイル クライアントの間でデータを移動する際の問題を解決する有効なソリューションです。 レプリケーション ウィザードを使用すると、レプリケーション トポロジを簡単に設定し、管理できます。 このチュートリアルでは、モバイル クライアント用のレプリケーション トポロジを設定する方法を学習します。  
  
## <a name="what-you-will-learn"></a>学習する内容  
このチュートリアルでは、マージ レプリケーションを使用して中央のデータベースから 1 名以上のモバイル ユーザーにデータをパブリッシュし、各ユーザーが独自にフィルター選択されたデータ サブセットを取得するようにします。 最初のレッスンでは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使ってパブリケーションを作成する方法を学習し、 後のレッスンではサブスクリプションを作成および同期する方法を学習します。  
  
## <a name="requirements"></a>必要条件  
このチュートリアルは、データベースの基本的な操作は理解しているが、レプリケーション機能についてはあまり詳しくないユーザーを対象としています。 このチュートリアルを開始する前に、 [「チュートリアル: レプリケーションに備えたサーバーの準備」](../../relational-databases/replication/tutorial-preparing-the-server-for-replication.md)を完了しておく必要があります。  
  
このチュートリアルを使用するには、システムに次のコンポーネントがインストールされている必要があります。  
  
-   パブリッシャー サーバー側 (レプリケーション元) :  
  
    -   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]の任意のエディション。ただし、Express ([!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]) と [!INCLUDE[ssEW](../../includes/ssew-md.md)]は除きます。 レプリケーションのパブリッシャーとして使用できないため除きます。  
  
    -   [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル データベース。 セキュリティ強化のため、既定ではサンプル データベースがインストールされません。  
  
-   サブスクライバー サーバー側 (レプリケーション先) :  
  
    -   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]の任意のエディション。ただし、 [!INCLUDE[ssEW](../../includes/ssew-md.md)]は除きます。 [!INCLUDE[ssEW](../../includes/ssew-md.md)] は、このチュートリアルで作成するパブリケーションで使用できません。  
  
    > [!NOTE]  
    > 既定では、レプリケーションは [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]にインストールされません。  
  
> [!NOTE]  
> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]では、固定サーバー ロール sysadmin のメンバーとしてログインし、パブリッシャーとサブスクライバーに接続する必要があります。  
  
**このチュートリアルの推定所要時間: 30 分。**  
  
## <a name="lessons-in-this-tutorial"></a>このチュートリアルで行うレッスン  
  
-   [レッスン 1 : マージ レプリケーションを使用したデータのパブリッシュ](../../relational-databases/replication/lesson-1-publishing-data-using-merge-replication.md)  
  
-   [レッスン 2 : マージ パブリケーションへのサブスクリプションの作成](../../relational-databases/replication/lesson-2-creating-a-subscription-to-the-merge-publication.md)  
  
[チュートリアルを開始する](../../relational-databases/replication/lesson-1-publishing-data-using-merge-replication.md)  
  
## <a name="see-also"></a>参照  
[レプリケーションのプログラミング概念](../../relational-databases/replication/concepts/replication-programming-concepts.md)  
  
  
  

