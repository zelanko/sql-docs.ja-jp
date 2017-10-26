---
title: "SQL Server のインストールの検証 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- setup-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- validating installations [SQL Server]
ms.assetid: 1689af50-d2b8-4aa6-8f27-cc7127157fc8
caps.latest.revision: 31
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: On Demand
ms.translationtype: HT
ms.sourcegitcommit: 1df54edd5857ac2816fa4b164d268835d9713638
ms.openlocfilehash: 94e78a2ae81545a5a3aa489fe5b3cef2c64be2e0
ms.contentlocale: ja-jp
ms.lasthandoff: 09/12/2017

---
# <a name="validate-a-sql-server-installation"></a>SQL Server のインストールの検証
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の検出レポートは、コンピューターにインストールされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンおよび [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の機能を確認するために使用できます。 **[インストール済み [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能の検出レポート]** には、ローカル サーバーにインストールされている [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]、[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]、および [!INCLUDE[ssSQL15](../../includes/sssqlv14-md.md)] の製品と機能すべてのレポートが表示されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能の検出レポートは、 **インストール センターの** [ツール] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ページで利用できます。  
  
 ## <a name="run-includessnoversionincludesssnoversion-mdmd-features-discovery-report"></a>[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能の検出レポートを実行する  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール センターを起動します。そのためには、**[スタート]** ボタンをクリックし、**[すべてのプログラム]**、**[[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \<バージョン名>]**、**[構成ツール]** の順にポイントし、**[[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール センター]** をクリックします。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能の検出レポートを実行するには、**[[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール センター]** の左側のナビゲーション領域にある **[ツール]** をクリックし、**[インストール済み [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能の検出レポート]** をクリックします。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の検出レポートは、%ProgramFiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\*nnn*\Setup Bootstrap\Log\\<最後のセットアップ セッション\> に保存されます。  
  
 また、コマンド ラインから検出レポートを生成することができます。 コマンド プロンプトで "Setup.exe /Action=RunDiscovery" を実行します。このコマンド ラインに "/q" を追加すると、UI は表示されませんが、レポートは %ProgramFiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\*nnn*\Setup Bootstrap\Log\\<最後のセットアップ\> セッションに作成されます。  
  
## <a name="see-also"></a>参照  
 [SQL Server セットアップ ログ ファイルの表示と読み取り](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
  

