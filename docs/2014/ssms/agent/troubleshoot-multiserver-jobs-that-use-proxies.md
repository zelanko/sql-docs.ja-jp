---
title: プロキシを使用するマルチサーバー ジョブのトラブルシューティング | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- proxies [SQL Server Agent], multiserver jobs
- jobs [SQL Server Agent], multiserver jobs using proxies
ms.assetid: fc579bd3-010c-4f72-8b5c-d0cc18a1f280
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 47e3c3991bd4732d542bf1ce79e83000e738ff77
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63245423"
---
# <a name="troubleshoot-multiserver-jobs-that-use-proxies"></a>プロキシを使用するマルチサーバー ジョブのトラブルシューティング
  プロキシに関連付けられているステップがある分散ジョブは、ターゲット サーバーのプロキシ アカウントのコンテキストで実行されます。 プロキシ アカウントを使用するジョブ ステップをマスター サーバーからダウンロードする際、それらのジョブ ステップにエラーが発生した場合は、 **msdb** データベースの **sysdownloadlist** テーブルにある **error_message** 列に次のエラー メッセージが出力されていないか確認してください。  
  
-   "ジョブ ステップではプロキシ アカウントが必要ですが、ターゲット サーバーで一致するプロキシが無効です。"  
  
     このエラーを解決するには、 **\ HKEY_LOCAL_MACHINE \SOFTWARE\MICROSOFT\MICROSOFT SQL Server\MSSQL.** を設定します。>**\SQLServerAgent\AllowDownloadedJobsToMatchProxyName** _ \<n_\SQLServerAgent\AllowDownloadedJobsToMatchProxyName レジストリサブキーを**1 (true)** にします。 既定では、このサブキーは**0** (`false`) に設定されています。 MSSQL の値 **。**\< *n*> はインスタンス名です。たとえば、 **mssql. 1**または**mssql. 3**のようになります。  
  
-   "プロキシ アカウントが見つかりませんでした。"  
  
     このエラーを解決するには、ターゲット サーバー上にプロキシ アカウントが存在し、ジョブ ステップを実行するマスター サーバー プロキシ アカウントと同じ名前が付けられているかどうかを確認します。  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry-md.md)]  
  
## <a name="see-also"></a>参照  
 [マルチサーバー環境の作成](create-a-multiserver-environment.md)  
  
  
