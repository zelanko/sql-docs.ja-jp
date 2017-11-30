---
title: "プロキシを使用するマルチサーバー ジョブのトラブルシューティング | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- proxies [SQL Server Agent], multiserver jobs
- jobs [SQL Server Agent], multiserver jobs using proxies
ms.assetid: fc579bd3-010c-4f72-8b5c-d0cc18a1f280
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3e6b90c23f37086952748416d5462015f8ecae7c
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="troubleshoot-multiserver-jobs-that-use-proxies"></a>プロキシを使用するマルチサーバー ジョブのトラブルシューティング
プロキシに関連付けられているステップを持つ分散ジョブは、対象サーバーのプロキシ アカウントのコンテキストで実行されます。 プロキシ アカウントを使用するジョブ ステップをマスター サーバーからダウンロードする際、それらのジョブ ステップにエラーが発生した場合は、 **msdb** データベースの **sysdownloadlist** テーブルにある **error_message** 列に次のエラー メッセージが出力されていないか確認してください。  
  
-   "ジョブ ステップではプロキシ アカウントが必要ですが、対象サーバーで一致するプロキシが無効です。"  
  
    このエラーを解決するには、 **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\MSSQL.***\<n*>**\SQLServerAgent\AllowDownloadedJobsToMatchProxyName** レジストリ サブキーを **1 (true)**に設定します。 既定では、このサブキーは **0** (**false**) に設定されます。 **MSSQL.**\<*n*> の値はインスタンス名です (例: **MSSQL.1**、**MSSQL.3**)。  
  
-   "プロキシ アカウントが見つかりませんでした。"  
  
    このエラーを解決するには、対象サーバー上にプロキシ アカウントが存在し、ジョブ ステップを実行するマスター サーバー プロキシ アカウントと同じ名前が付けられているかどうかを確認します。  
  
> [!CAUTION]  
> [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry_md.md)]  
  
## <a name="see-also"></a>参照  
[マルチサーバー環境の作成](../../ssms/agent/create-a-multiserver-environment.md)  
  
