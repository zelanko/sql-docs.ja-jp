---
title: Transact-SQL スクリプトの再生 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], replaying
- scripts [SQL Server], traces
- replaying traces
ms.assetid: 9c0eb222-e6e3-4bc1-a25f-a41e962d361b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6570eeacfe7da346cc0d41352888f5acc57baf2b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68211064"
---
# <a name="replay-a-transact-sql-script-sql-server-profiler"></a>Transact-SQL スクリプトの再生 (SQL Server Profiler)
  パフォーマンスの問題に対して考えられる解決策をテストする場合、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用して [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトを再生し、変更を加える前と加えた後のパフォーマンスを比較します。  
  
### <a name="to-replay-a-transact-sql-script"></a>Transact-SQL スクリプトを再生するには  
  
1.  **[ファイル]** メニューの **[開く]** をポイントし、 **[スクリプト ファイル]** をクリックします。  
  
2.  [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト ファイルを選択して開きます。 再生に必要なイベントが [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトに含まれていることを確認してください。 詳細については、「 [再生を実行するための必要条件](replay-requirements.md)」を参照してください。  
  
3.  **[再生]** メニューの **[開始]** をクリックし、スクリプトを再生するサーバーに接続します。  
  
4.  **[構成の再生]** ダイアログ ボックスで設定を確認し、 **[OK]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [トレースの再生](replay-traces.md)   
 [SQL Server Profiler](sql-server-profiler.md)  
  
  
