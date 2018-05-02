---
title: レプリケーションのチュートリアル | Microsoft Docs
ms.custom: ''
ms.date: 04/09/2018
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- tutorials [SQL Server replication]
- walkthroughs [SQL Server replication]
- replication [SQL Server], tutorials
ms.assetid: 19fbd10e-5b59-4cd0-a988-52d5d9206242
caps.latest.revision: 13
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 3900aae4e96b5490b0b65cbbee004fc66337ff63
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="replication-tutorials"></a>レプリケーションのチュートリアル
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
レプリケーションは、サーバー間でデータまたはデータのサブセットを移動するための強力なソリューションです。 トランザクション レプリケーションを使用して完全に接続されたサーバー間でデータをレプリケートすることができます。 マージ レプリケーションを使用して断続的に接続されたサーバーとクライアントの間でデータをレプリケートすることもできます。 以下に、レプリケーション用にサーバーを準備するために役立つチュートリアルを示し、トランザクション レプリケーションとマージ レプリケーションの両方を構成する方法を説明します。 
  
レプリケーションのチュートリアルでは、"パブリッシャー" はレプリケート元のデータが配置されているサーバーを指し、"サブスクライバー" はレプリケート先のサーバーを指しています。 パブリッシャーとサブスクライバーが同じ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスを共有することもできますが、これは必須条件ではありません。 詳細については、 [「レプリケーションのパブリッシング モデルの概要」](../../relational-databases/replication/publish/replication-publishing-model-overview.md)を参照してください。  

これらのチュートリアルでは、パブリッシャーとディストリビューターとして NODE1\SQL2016 を使用し、サブスクライバーとして NODE2\SQL2016 を使用します。 
  
> [!NOTE]  
> このチュートリアルで示すタスクのほとんどは、プログラムによって実行できます。 詳細については、 [「開発者ガイド (レプリケーション)」](../../relational-databases/replication/concepts/replication-developer-documentation.md)を参照してください。  
  
## <a name="replication-tutorials"></a>レプリケーションのチュートリアル  
[チュートリアル: レプリケーション用の SQL Server の準備 - パブリッシャー、ディストリビューター、サブスクライバー](../../relational-databases/replication/tutorial-preparing-the-server-for-replication.md) 
 
最小の権限でレプリケーションを実行できるようサーバーを準備する方法を学習します。 このチュートリアルは、レプリケーション関連のチュートリアルの中で最初に実行する必要があります。  
  
[チュートリアル: 2 つの常時接続サーバー間のレプリケーション (トランザクション) を構成する ](../../relational-databases/replication/tutorial-replicating-data-between-continuously-connected-servers.md)

常時接続のサーバー間でデータをレプリケートするようにトランザクション レプリケーションを構成する方法を学習します。 このチュートリアルには、いくつか基本的なエラーのトラブルシューティングの手法も含まれます。 

  
[チュートリアル: サーバーとモバイル クライアントの間のレプリケーション (マージ) を構成する](../../relational-databases/replication/tutorial-replicating-data-with-mobile-clients.md)

サーバーと、常時接続でない 1 つ以上のクライアントの間でデータを交換するようにマージ レプリケーションを構成する方法を学習します。  
  
## <a name="see-also"></a>参照  
[レプリケーションのセキュリティと保護](../../relational-databases/replication/security/security-and-protection-replication.md) 

[トランザクション レプリケーションの概要](https://docs.microsoft.com/en-us/sql/relational-databases/replication/transactional/transactional-replication) 

[マージ レプリケーションの概要](https://docs.microsoft.com/en-us/sql/relational-databases/replication/merge/merge-replication)

  