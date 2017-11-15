---
title: "マスター サーバーからの対象サーバーの参加の解除 | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- target servers [SQL Server], defecting
- SQL Server Agent jobs, master servers
- master servers [SQL Server], defecting target servers
- defecting target servers
ms.assetid: a6da262b-7b38-4ce4-bfd6-6a557c6e8a84
caps.latest.revision: "5"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7ff02e4d5b98ef7a17956d401b3a40882cc6cc15
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="defect-a-target-server-from-a-master-server"></a>Defect a Target Server from a Master Server
このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]、 [!INCLUDE[tsql](../../includes/tsql_md.md)]、または SQL Server 管理オブジェクト (SMO) を使用して、マスター サーバーから対象サーバーの参加を解除する方法について説明します。 この手順は対象サーバーから実行します。  
  
**このトピックの内容**  
  
-   **作業を開始する準備:**  
  
    [Security](#Security)  
  
-   **マスター サーバーから対象サーバーの参加を解除するために使用するもの:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
    [SMO](#PowerShellProcedure)  
  
## <a name="BeforeYouBegin"></a>はじめに  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
このストアド プロシージャを実行するには、 **sysadmin** 固定サーバー ロールのメンバーであることが必要です。  
  
## <a name="SSMSProcedure"></a>SQL Server Management Studio の使用  
  
#### <a name="to-defect-a-target-server-from-a-master-server"></a>マスター サーバーから対象サーバーの参加を解除するには  
  
1.  **オブジェクト エクスプローラー**で、対象サーバーとして構成するサーバーを展開します。  
  
2.  **[SQL Server エージェント]**を右クリックし、 **[マルチ サーバーの管理]**をポイントして、 **[参加解除]**をクリックします。  
  
3.  **[はい]** をクリックして、マスター サーバーからこの対象サーバーの参加を解除することを確認します。  
  
## <a name="TsqlProcedure"></a>Transact-SQL の使用  
  
#### <a name="to-defect-a-target-server-from-a-master-server"></a>マスター サーバーから対象サーバーの参加を解除するには  
  
1.  [!INCLUDE[ssDE](../../includes/ssde_md.md)]に接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。  
  
```  
sp_msx_defect ;  
```  
  
詳細については、「 [sp_msx_defect (Transact-SQL)](http://msdn.microsoft.com/en-us/0dfd963a-3bc5-4b58-94f7-aec976da2883)」を参照してください。  
  
## <a name="PowerShellProcedure"></a>SQL Server 管理オブジェクト (SMO) の使用  
**MsxDefect メソッド**を使用します。  
  
## <a name="see-also"></a>参照  
[マルチサーバー環境の作成](../../ssms/agent/create-a-multiserver-environment.md)  
[エンタープライズ全体の管理の自動化](../../ssms/agent/automated-administration-across-an-enterprise.md)  
[マスター サーバーからの複数の対象サーバーの参加の解除](../../ssms/agent/defect-multiple-target-servers-from-a-master-server.md)  
  
