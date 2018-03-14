---
title: "チュートリアル : レプリケーションに備えたサーバーの準備 | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: ce30a095-2975-4387-9377-94a461ac78ee
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 3f7055cc15673a5dfd4564f26c4d314ccc0f5180
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="tutorial-preparing-the-server-for-replication"></a>チュートリアル : レプリケーションに備えたサーバーの準備
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
レプリケーション トポロジを構成するには、事前にセキュリティ計画を立てることが重要です。 このチュートリアルでは、レプリケーション トポロジのセキュリティを向上する方法と、データのレプリケートで最初のステップとなるディストリビューションの構成方法を学習します。 他のチュートリアルを行う前に、まずこのチュートリアルを実行してください。  
  
> [!NOTE]  
> サーバー間でデータを安全にレプリケートするには、「 [レプリケーション セキュリティの推奨事項](../../relational-databases/replication/security/replication-security-best-practices.md)」の推奨事項をすべて実践してください。  
  
## <a name="what-you-will-learn"></a>学習する内容  
このチュートリアルでは、サーバーを準備し、レプリケーションを最小の特権で安全に実行できるようにする方法を学習します。 最初のレッスンでは、レプリケーション エージェントの実行に使用する Windows サービス アカウントの作成方法を学習します。 2 番目のレッスンでは、パブリケーション スナップショットの生成と保存に使用するフォルダーの構成方法を学習します。 3 番目のレッスンでは、ディストリビューションの構成方法と権限の設定方法を学習します。  
  
## <a name="requirements"></a>必要条件  
このチュートリアルは、データベースの基本的な操作は理解しているが、レプリケーション機能についてはあまり詳しくないユーザーを対象としています。  
  
このチュートリアルを使用するには、システムに次のコンポーネントがインストールされている必要があります。  
  
-   [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] と [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベース。  
  
**このチュートリアルの推定所要時間: 30 分。**  
  
## <a name="lessons-in-this-tutorial"></a>このチュートリアルで行うレッスン  
  
-   [レッスン 1 : レプリケーション用の Windows アカウントの作成](../../relational-databases/replication/lesson-1-creating-windows-accounts-for-replication.md)  
  
-   [レッスン 2 : スナップショット フォルダーの準備](../../relational-databases/replication/lesson-2-preparing-the-snapshot-folder.md)  
  
-   [レッスン 3 : ディストリビューションの構成](../../relational-databases/replication/lesson-3-configuring-distribution.md)  
  
[チュートリアルを開始する](../../relational-databases/replication/lesson-1-creating-windows-accounts-for-replication.md)  
  
## <a name="see-also"></a>参照  
[ディストリビューションの構成](../../relational-databases/replication/configure-distribution.md)  
[セキュリティと保護 &#40;レプリケーション&#41;](../../relational-databases/replication/security/security-and-protection-replication.md)  
  
  
  
