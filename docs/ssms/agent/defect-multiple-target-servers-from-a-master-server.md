---
title: "マスター サーバーからの複数の対象サーバーの参加の解除 | Microsoft Docs"
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
- SQL Server Agent jobs, target servers
- target servers [SQL Server], defecting
- SQL Server Agent jobs, master servers
- master servers [SQL Server], defecting target servers
- defecting target servers
- multiple target server defections
ms.assetid: 61a3713b-403a-4806-bfc4-66db72ca1156
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: d24f986e0274592b8984c9bf5d493261781b8f77
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="defect-multiple-target-servers-from-a-master-server"></a>マスター サーバーからの複数の対象サーバーの参加の解除
このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]を使用して、マルチサーバー管理構成から複数の対象サーバーの参加を解除する方法について説明します。 この手順はマスター サーバーから実行します。  
  
## <a name="SSMSProcedure"></a>SQL Server Management Studio の使用  
  
#### <a name="to-defect-multiple-target-servers-from-a-master-server"></a>マスター サーバーから複数の対象サーバーの参加を解除するには  
  
1.  **オブジェクト エクスプローラー**で、マスター サーバーとして構成するサーバーを展開します。  
  
2.  **[SQL Server エージェント]**を右クリックし、 **[マルチ サーバーの管理]**をポイントして、 **[対象サーバーの管理]**をクリックします。  
  
3.  **[命令を通知]**をクリックし、 **[命令の種類]** ボックスの一覧の **[参加解除]**をクリックします。  
  
4.  **[受信者]**で、次のいずれかの操作を行います。  
  
    -   このマスター サーバーのすべての対象サーバーの参加を解除するには、 **[すべての対象サーバー]** をクリックします。 このオプションは、現在のマルチサーバー管理構成を完全にアンインストールする場合に使用します。  
  
    -   このマスター サーバーから一部の対象サーバーだけを参加解除するには、 **[特定の対象サーバー]**をクリックし、参加を解除するサーバーの **[選択]** ボックスをクリックします。  
  
## <a name="see-also"></a>参照  
[マルチサーバー環境の作成](../../ssms/agent/create-a-multiserver-environment.md)  
[エンタープライズ全体の管理の自動化](../../ssms/agent/automated-administration-across-an-enterprise.md)  
[Defect a Target Server from a Master Server](../../ssms/agent/defect-a-target-server-from-a-master-server.md)  
  

