---
title: "マスター サーバーへの対象サーバーの参加 | Microsoft Docs"
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
- enlisting target servers [SQL Server]
- SQL Server Agent jobs, target servers
- master servers [SQL Server], enlisting target servers
- SQL Server Agent jobs, master servers
- target servers [SQL Server], enlisting
ms.assetid: 7633adb5-d140-4e58-a8f2-5b4b50c2f95b
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 61fb82bcd0f3ac4308e023e31338f8142614488d
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="enlist-a-target-server-to-a-master-server"></a>マスター サーバーへの対象サーバーの参加
このトピックでは、マルチサーバー管理構成に対象サーバーを参加させる方法について説明します。 この手順はマスター サーバーから実行します。 [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] で、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]、 [!INCLUDE[tsql](../../includes/tsql_md.md)]、または SQL Server 管理オブジェクト (SMO) を使用します。  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービス用に使用される Windows アカウントがマルチサーバー環境に与える影響については、「 [マルチサーバー環境の作成](../../ssms/agent/create-a-multiserver-environment.md)」を参照してください。  
  
マスター サーバーと対象サーバーの間の接続では、完全な Secure Sockets Layer (SSL) 暗号化と証明書の検証が既定で有効になります。 詳しくは、「 [対象サーバーでの暗号化オプションの設定](../../ssms/agent/set-encryption-options-on-target-servers.md)」をご覧ください。  
  
**このトピックの内容**  
  
-   **対象サーバーを参加させるために使用するもの:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="SSMSProcedure"></a>SQL Server Management Studio の使用  
  
#### <a name="to-enlist-a-target-server"></a>対象サーバーを参加させるには  
  
1.  **オブジェクト エクスプローラー**で、マスター サーバーとして構成するサーバーを展開します。  
  
2.  **[SQL Server エージェント]**を右クリックし、 **[マルチ サーバーの管理]**をポイントして **[対象サーバーの追加]**をクリックします。  
  
3.  対象サーバー設定ウィザードを実行し、指示に従って操作します。  
  
## <a name="TsqlProcedure"></a>Transact-SQL の使用  
  
#### <a name="to-enlist-a-target-server"></a>対象サーバーを参加させるには  
  
1.  **sp_msx_enlist** ストアド プロシージャを使用します。  詳細については、「 [sp_msx_enlist (Transact-SQL)](http://msdn.microsoft.com/en-us/ceb3b2bc-0cc4-48d8-9bdc-6a809556e35f)」を参照してください。  
  
## <a name="see-also"></a>参照  
[エンタープライズ全体の管理の自動化](../../ssms/agent/automated-administration-across-an-enterprise.md)  
  

