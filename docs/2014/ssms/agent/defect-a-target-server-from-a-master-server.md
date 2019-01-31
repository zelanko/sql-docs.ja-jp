---
title: マスター サーバーからのターゲット サーバーの参加の解除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- target servers [SQL Server], defecting
- SQL Server Agent jobs, master servers
- master servers [SQL Server], defecting target servers
- defecting target servers
ms.assetid: a6da262b-7b38-4ce4-bfd6-6a557c6e8a84
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e0b39605d4c1867d166ce3b6878de47273ad2072
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52795694"
---
# <a name="defect-a-target-server-from-a-master-server"></a>マスター サーバーからのターゲット サーバーの参加の解除
  このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../includes/tsql-md.md)]、または SQL Server 管理オブジェクト (SMO) を使用して、マスター サーバーからターゲット サーバーの参加を解除する方法について説明します。 この手順はターゲット サーバーから実行します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [Security](#Security)  
  
-   **マスター サーバーから対象サーバーの参加を解除するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [SMO](#PowerShellProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 このストアド プロシージャを実行するには、`sysadmin` 固定サーバー ロールのメンバーであることが必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-defect-a-target-server-from-a-master-server"></a>マスター サーバーからターゲット サーバーの参加を解除するには  
  
1.  **オブジェクト エクスプローラー**で、対象サーバーとして構成するサーバーを展開します。  
  
2.  **[SQL Server エージェント]** を右クリックし、 **[マルチ サーバーの管理]** をポイントして、 **[参加解除]** をクリックします。  
  
3.  **[はい]** をクリックして、マスター サーバーからこの対象サーバーの参加を解除することを確認します。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-defect-a-target-server-from-a-master-server"></a>マスター サーバーからターゲット サーバーの参加を解除するには  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
```  
sp_msx_defect ;  
```  
  
 詳細については、次を参照してください。 [sp_msx_defect &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-defect-transact-sql)します。  
  
##  <a name="PowerShellProcedure"></a> SQL Server 管理オブジェクト (SMO) の使用  
 使用して、`MsxDefect Method`します。  
  
## <a name="see-also"></a>参照  
 [マルチサーバー環境の作成](create-a-multiserver-environment.md)   
 [エンタープライズ全体の管理の自動化](automated-administration-across-an-enterprise.md)   
 [マスター サーバーからの複数の対象サーバーの参加の解除](defect-multiple-target-servers-from-a-master-server.md)  
  
  
