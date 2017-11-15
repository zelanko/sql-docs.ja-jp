---
title: "[SQL Server エージェントのプロパティ] ダイアログ ボックス ([ジョブ システム] ページ) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.ag.agent.job.f1
ms.assetid: e171d13e-1302-4f0e-88be-67d656aec8d3
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ed055e6b7a9c560c0ac05c11f930c49b681de0aa
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="sql-server-agent-properties-job-system-page"></a>[SQL Server エージェントのプロパティ] ダイアログ ボックス ([ジョブ システム] ページ)
このページを使用すると、 [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービスによるジョブの管理方法を表示および変更ができます。  
  
## <a name="options"></a>オプション  
**[シャットダウン タイムアウト間隔 (秒)]**  
シャットダウンの前に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントがジョブの完了を待つ時間を秒数で指定します。 指定した時間が過ぎてもジョブが実行されている場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントによって強制的にジョブが停止されます。  
  
**[管理者以外のプロキシ アカウントを使用する]**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントに管理者以外のプロキシ アカウントを設定します。 [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)] 以降のバージョンでは複数のプロキシがサポートされるため、このオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] より前のバージョンの [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)]エージェントを管理する場合にのみ適用できます。  
  
**ユーザー名**  
管理者以外のプロキシ アカウントのユーザーの名前を入力します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] では複数のプロキシがサポートされるため、このオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] より前のバージョンの [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)]エージェントを管理する場合にのみ適用できます。  
  
**Password**  
管理者以外のプロキシ アカウントのユーザーのパスワードを入力します。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)] 以降のバージョンでは複数のプロキシがサポートされるため、このオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] より前のバージョンの [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)]エージェントを管理する場合にのみ適用できます。  
  
**[ドメイン]**  
管理者以外のプロキシ アカウントのユーザーのドメインを入力します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] では複数のプロキシがサポートされるため、このオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] より前のバージョンの [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)]エージェントを管理する場合にのみ適用できます。  
  
## <a name="see-also"></a>参照  
[ジョブの実装](../../ssms/agent/implement-jobs.md)  
  
