---
title: 同期中のスクリプトの実行 (レプリケーション Transact-SQL プログラミング) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- synchronization [SQL Server replication], scripts
- scripts [SQL Server replication], synchronization and
- sp_addscriptexec
ms.assetid: b58a0877-4e43-4fab-a281-24e6022d3fb1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4bc217ad160a0238cc4247600d65eb32f156071f
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85010701"
---
# <a name="execute-scripts-during-synchronization-replication-transact-sql-programming"></a>同期中のスクリプトの実行 (レプリケーション Transact-SQL プログラミング)
  レプリケーションでは、トランザクション パブリケーションおよびマージ パブリケーションのサブスクライバーに対し、要求時にスクリプトを実行できます。 スクリプトはレプリケーションの作業ディレクトリにコピーされ、サブスクライバー側で **sqlcmd** を使って適用されます。 トランザクション パブリケーションのサブスクリプションに対してスクリプトを適用しているときにエラーが発生した場合、既定では、ディストリビューション エージェントの実行が停止します。 レプリケーションのストアド プロシージャを使用すると、指定した [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトをプログラムから実行できます。  
  
### <a name="to-specify-a-script-to-run-for-all-subscribers-to-a-snapshot-transactional-or-merge-publication"></a>スナップショット、トランザクション、マージ パブリケーションのすべてのサブスクライバーに対して実行するスクリプトを指定するには  
  
1.  要求時に実行する [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトを作成およびテストします。  
  
2.  スクリプト ファイルを、パブリケーションのスナップショット エージェントがアクセスできる場所に保存します。  
  
3.  パブリッシャー側のパブリケーション データベースに対して、[sp_addscriptexec &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addscriptexec-transact-sql) を実行します。 [ ** \@ パブリケーション**] を指定し、 ** \@ scriptfile**に手順 2. で作成した完全な UNC パスを含むスクリプトファイルの名前と、 ** \@ skiperror**に次の値のいずれかを指定します。  
  
    -   **0** - エラーが発生した場合、エージェントがスクリプトの実行を停止します。  
  
    -   **1** - エラーが発生した場合、エージェントによってエラー ログが記録され、スクリプトの実行が継続されます。  
  
4.  指定したスクリプトは、エージェントが次にサブスクリプションを同期するときに、各サブスクライバーで実行されます。  
  
## <a name="see-also"></a>参照  
 [データの同期](synchronize-data.md)  
  
  
