---
title: "対象サーバーからのマスター サーバーのポーリングの強制 | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- forcing master server polling
- polling master servers [SQL Server]
- master servers [SQL Server], polling
- target servers [SQL Server], polling the master server
ms.assetid: f1189a47-5ac3-45e2-9c5f-847810672279
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 57fe0392adfb1e290491815acd216fd356e20f3e
ms.lasthandoff: 04/11/2017

---
# <a name="force-a-target-server-to-poll-the-master-server"></a>対象サーバーからのマスター サーバーのポーリングの強制
このトピックでは、対象サーバーからマスター サーバーにポーリングさせる方法について説明します。 対象サーバーは、マスター サーバーの登録済みサーバーである必要があります。  
  
ジョブとは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントで実行される特定の一連の処理のことです。 マルチサーバー ジョブとは、1 つ以上の対象サーバーでマスター サーバーにより実行されるジョブです。 各対象サーバーは、同じジョブのインスタンスを同時に実行できます。 各対象サーバーからマスター サーバーに定期的にポーリングし、その対象サーバーに割り当てられた新しいジョブのコピーをダウンロードした後、切断します。 ダウンロードされたジョブは対象サーバーでローカルに実行され、マスター サーバーに再接続してジョブ結果状態をアップロードします。  
  
> [!NOTE]  
> 対象サーバーがジョブの状態をアップロードするときにマスター サーバーにアクセスできない場合、そのジョブの状態はマスター サーバーがアクセスできるようになるまでスプールされます。  
  
-   **作業を開始する準備:**  [制限事項と制約事項](#Restrictions)、 [セキュリティ](#Security)  
  
-   **対象サーバーからマスター サーバーにポーリングさせるために使用するもの:** [SQL Server Management Studio](#SSMS)  
  
## <a name="BeforeYouBegin"></a>はじめに  
  
### <a name="Restrictions"></a>制限事項と制約事項  
対象サーバーは、マスター サーバーの登録済みサーバーである必要があります。 このトピックに説明されている手順は、マスター サーバーから実行する必要があります。  
  
### <a name="Security"></a>セキュリティ  
詳細については、「 [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md) 」および「 [Choose the Right SQL Server Agent Service Account for Multiserver Environments](../../ssms/agent/choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md)」を参照してください。  
  
## <a name="SSMS"></a>SQL Server Management Studio の使用  
**対象サーバーからマスター サーバーにポーリングさせるには**  
  
1.  **オブジェクト エクスプローラー**で、マスター サーバーを展開します。  
  
2.  **[SQL Server エージェント]**を右クリックし、 **[マルチ サーバーの管理]**をポイントして、 **[対象サーバーの管理]**をクリックします。  
  
3.  対象サーバーをクリックし、 **[強制的にポーリング]**をクリックします。  
  

