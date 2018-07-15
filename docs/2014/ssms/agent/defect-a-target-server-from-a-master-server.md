---
title: マスター サーバーからの対象サーバーの参加の解除 | Microsoft Docs
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
- SQL Server Agent jobs, target servers
- target servers [SQL Server], defecting
- SQL Server Agent jobs, master servers
- master servers [SQL Server], defecting target servers
- defecting target servers
ms.assetid: a6da262b-7b38-4ce4-bfd6-6a557c6e8a84
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 35f113cfd0e038940c00b710b31f254da6343805
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37305042"
---
# <a name="defect-a-target-server-from-a-master-server"></a>Defect a Target Server from a Master Server
  このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../includes/tsql-md.md)]、または SQL Server 管理オブジェクト (SMO) を使用して、マスター サーバーから対象サーバーの参加を解除する方法について説明します。 この手順は対象サーバーから実行します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [Security](#Security)  
  
-   **マスター サーバーから対象サーバーの参加を解除するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [SMO](#PowerShellProcedure)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 このストアド プロシージャを実行するには、`sysadmin` 固定サーバー ロールのメンバーであることが必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-defect-a-target-server-from-a-master-server"></a>マスター サーバーから対象サーバーの参加を解除するには  
  
1.  **オブジェクト エクスプローラー**で、対象サーバーとして構成するサーバーを展開します。  
  
2.  **[SQL Server エージェント]** を右クリックし、 **[マルチ サーバーの管理]** をポイントして、 **[参加解除]** をクリックします。  
  
3.  **[はい]** をクリックして、マスター サーバーからこの対象サーバーの参加を解除することを確認します。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-defect-a-target-server-from-a-master-server"></a>マスター サーバーから対象サーバーの参加を解除するには  
  
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
  
  
