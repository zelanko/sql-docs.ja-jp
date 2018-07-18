---
title: 対象サーバーからのマスター サーバーのポーリングの強制 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- forcing master server polling
- polling master servers [SQL Server]
- master servers [SQL Server], polling
- target servers [SQL Server], polling the master server
ms.assetid: f1189a47-5ac3-45e2-9c5f-847810672279
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5b48a9cbf311d66751cd0e1285eb03626e278779
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37289948"
---
# <a name="force-a-target-server-to-poll-the-master-server"></a>対象サーバーからのマスター サーバーのポーリングの強制
  このトピックでは、対象サーバーからマスター サーバーにポーリングさせる方法について説明します。 対象サーバーは、マスター サーバーの登録済みサーバーである必要があります。  
  
 ジョブとは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントで実行される特定の一連の処理のことです。 マルチサーバー ジョブとは、1 つ以上の対象サーバーでマスター サーバーにより実行されるジョブです。 各対象サーバーは、同じジョブのインスタンスを同時に実行できます。 各対象サーバーからマスター サーバーに定期的にポーリングし、その対象サーバーに割り当てられた新しいジョブのコピーをダウンロードした後、切断します。 ダウンロードされたジョブは対象サーバーでローカルに実行され、マスター サーバーに再接続してジョブ結果状態をアップロードします。  
  
> [!NOTE]  
>  対象サーバーがジョブの状態をアップロードするときにマスター サーバーにアクセスできない場合、そのジョブの状態はマスター サーバーがアクセスできるようになるまでスプールされます。  
  
-   **作業を開始する準備:**  [制限事項と制約事項](#Restrictions)、 [セキュリティ](#Security)  
  
-   **ターゲット サーバーからマスター サーバーにポーリングさせるのにを使用して:**[SQL Server Management Studio  ](#SSMS)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
 対象サーバーは、マスター サーバーの登録済みサーバーである必要があります。 このトピックに説明されている手順は、マスター サーバーから実行する必要があります。  
  
###  <a name="Security"></a> セキュリティ  
 詳細については、「 [Implement SQL Server Agent Security](implement-sql-server-agent-security.md) 」および「 [マルチサーバー環境に適した SQL Server エージェント サービス アカウントの選択](choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md)」を参照してください。  
  
##  <a name="SSMS"></a> SQL Server Management Studio の使用  
 **対象サーバーからマスター サーバーにポーリングさせるには**  
  
1.  **オブジェクト エクスプローラー**で、マスター サーバーを展開します。  
  
2.  **[SQL Server エージェント]** を右クリックし、 **[マルチ サーバーの管理]** をポイントして、 **[対象サーバーの管理]** をクリックします。  
  
3.  対象サーバーをクリックし、 **[強制的にポーリング]** をクリックします。  
  
  
