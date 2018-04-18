---
title: SQL Server エラー ログ (Always On 可用性グループ) (SQL Server) | Microsoft Docs
ms.custom: ag-guide
ms.date: 06/13/2017
ms.prod: sql-server-2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39d0c98d-75af-4dd1-b908-30d31af56f2a
caps.latest.revision: 4
author: rothja
ms.author: jroth
manager: jhubbard
ms.openlocfilehash: 535e8612c3b569a7dfcd9bbe88572e0fdc8c1f29
ms.sourcegitcommit: 8b332c12850c283ae413e0b04b2b290ac2edb672
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/05/2018
---
# <a name="sql-server-error-log-always-on-availability-groups"></a>SQL Server エラー ログ (Always On 可用性グループ)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  SQL Server エラー ログでは、次のような Always On 可用性グループに影響するイベントを報告します。  
  
-   Windows Server フェールオーバー クラスタリング (WSFC) クラスターとの通信  
  
-   可用性レプリカの状態遷移  
  
-   可用性データベースの状態遷移  
  
-   プライマリ レプリカとセカンダリ レプリカの間での可用性データベースの接続状態  
  
-   可用性グループのエンドポイントの状態  
  
-   可用性グループのリスナーの状態  
  
-   SQL Server リソース DLL (WSFC クラスターで実行されている) と SQL Server インスタンスの間のリース ステータス (詳細については、「[How It Works: SQL Server Always On lease timeout](http://blogs.msdn.com/b/psssql/archive/2012/09/07/how-it-works-sql-server-alwayson-lease-timeout.aspx)」(動作方法: SQL Server Always On のリース タイムアウト) を参照してください)。  
  
-   可用性グループのエラー イベント  


次の現象は、SQL Server エラー ログで確認する必要があります。  

-   可用性データベースにアクセスできない  
  
-   可用性グループの予期しないフェールオーバー  
  
-   予期しない解決状態の可用性グループ  
  
-   不確定な状態の可用性グループ  
  
詳細については、「[SQL Server エラー ログの表示 &#40;SQL Server Management Studio&#41;](~/relational-databases/performance/view-the-sql-server-error-log-sql-server-management-studio.md)」を参照してください。  
  
  