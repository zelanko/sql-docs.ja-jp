---
title: '[SQL Server エージェントのプロパティ] ダイアログ ボックス ([ジョブ システム] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.job.f1
ms.assetid: e171d13e-1302-4f0e-88be-67d656aec8d3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8dceeba78e639ecbe2fd81fbdb1021293e75cf8a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63246088"
---
# <a name="sql-server-agent-properties-job-system-page"></a>[SQL Server エージェントのプロパティ] ダイアログ ボックス ([ジョブ システム] ページ)
  このページを使用すると、エージェントサービス[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]がジョブを管理する方法を表示したり、変更したりできます。  
  
## <a name="options"></a>オプション  
 **[シャットダウン タイムアウト間隔 (秒)]**  
 シャットダウンの前に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントがジョブの完了を待つ時間を秒数で指定します。 指定した時間が過ぎてもジョブが実行されている場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントによって強制的にジョブが停止されます。  
  
 **[管理者以外のプロキシ アカウントを使用する]**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントに管理者以外のプロキシ アカウントを設定します。 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]以降のバージョンでは複数のプロキシがサポートされるため、この[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オプションは、より[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]前のバージョンのエージェントを管理する場合にのみ適用できます。  
  
 **ユーザー名**  
 管理者以外のプロキシ アカウントのユーザーの名前を入力します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では複数のプロキシがサポートされるため、このオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] より前のバージョンの [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]エージェントを管理する場合にのみ適用できます。  
  
 **パスワード**  
 管理者以外のプロキシ アカウントのユーザーのパスワードを入力します。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンでは複数のプロキシがサポートされるため、このオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] より前のバージョンの [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]エージェントを管理する場合にのみ適用できます。  
  
 **[ドメイン]**  
 管理者以外のプロキシ アカウントのユーザーのドメインを入力します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では複数のプロキシがサポートされるため、このオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] より前のバージョンの [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]エージェントを管理する場合にのみ適用できます。  
  
## <a name="see-also"></a>参照  
 [ジョブの実装](implement-jobs.md)  
  
  
