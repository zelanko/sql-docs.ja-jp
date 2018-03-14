---
title: "レプリケーションのチュートリアル | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- tutorials [SQL Server replication]
- walkthroughs [SQL Server replication]
- replication [SQL Server], tutorials
ms.assetid: 19fbd10e-5b59-4cd0-a988-52d5d9206242
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: bdd9595c58147cc654f389232589e4ab664caf98
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="replication-tutorials"></a>レプリケーションのチュートリアル
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
レプリケーションには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でレプリケーション トポロジをセットアップし、それを実行する方法を学習できるチュートリアルが用意されています。  
  
レプリケーションのチュートリアルでは、"パブリッシャー" はレプリケート元のデータが配置されているサーバーを指し、"サブスクライバー" はレプリケート先のサーバーを指しています。 パブリッシャーとサブスクライバーが同じ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスを共有することもできますが、これは必須条件ではありません。 詳細については、 [「レプリケーションのパブリッシング モデルの概要」](../../relational-databases/replication/publish/replication-publishing-model-overview.md)を参照してください。  
  
> [!NOTE]  
> このチュートリアルで示すタスクのほとんどは、プログラムによって実行できます。 詳細については、 [「開発者ガイド (レプリケーション)」](../../relational-databases/replication/concepts/replication-developer-documentation.md)を参照してください。  
  
## <a name="replication-tutorials"></a>レプリケーションのチュートリアル  
[レプリケーションに備えたサーバーの準備](../../relational-databases/replication/tutorial-preparing-the-server-for-replication.md)  
最小の権限でレプリケーションを実行できるようサーバーを準備する方法を学習します。 このチュートリアルは、レプリケーション関連のチュートリアルの中で最初に実行する必要があります。  
  
[常時接続サーバー間でのデータのレプリケーション](../../relational-databases/replication/tutorial-replicating-data-between-continuously-connected-servers.md)  
トランザクション レプリケーションを使用して、常時接続のサーバー間でデータをレプリケートする方法を学習します。  
  
[モバイル クライアントとの間のデータのレプリケーション](../../relational-databases/replication/tutorial-replicating-data-with-mobile-clients.md)  
マージ レプリケーションを使用して、サーバーと、常時接続でない 1 つ以上のクライアントの間でデータを交換する方法を学習します。  
  
## <a name="see-also"></a>参照  
[セキュリティと保護 (レプリケーション)](../../relational-databases/replication/security/security-and-protection-replication.md)  
  
  
  
