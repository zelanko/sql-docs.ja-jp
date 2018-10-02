---
title: SQL Server のインストールの検証 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- validating installations [SQL Server]
ms.assetid: 1689af50-d2b8-4aa6-8f27-cc7127157fc8
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
manager: craigg
ms.openlocfilehash: 3d223ce438087e4fdc017f09b9cdcabfde4a7fc1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47599142"
---
# <a name="validate-a-sql-server-installation"></a>SQL Server のインストールの検証

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の検出レポートは、コンピューターにインストールされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンおよび [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の機能を確認するために使用できます。 **[インストール済み [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能の検出レポート]** には、ローカル サーバーにインストールされている [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]、[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]、および [!INCLUDE[ssSQL15](../../includes/sssqlv14-md.md)] の製品と機能すべてのレポートが表示されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能の検出レポートは、 **インストール センターの** [ツール] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ページで利用できます。  
  
 ## <a name="run-includessnoversionincludesssnoversion-mdmd-features-discovery-report"></a>[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能の検出レポートを実行する  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール センターを起動します。そのためには、**[スタート]** ボタンをクリックし、**[すべてのプログラム]**、**[[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \<バージョン名>]**、**[構成ツール]** の順にポイントし、**[[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール センター]** をクリックします。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能の検出レポートを実行するには、**[[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール センター]** の左側のナビゲーション領域にある **[ツール]** をクリックし、**[インストール済み [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能の検出レポート]** をクリックします。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の検出レポートは、%ProgramFiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\*nnn*\Setup Bootstrap\Log\\<最後のセットアップ セッション\> に保存されます。  
  
 また、コマンド ラインから検出レポートを生成することができます。 コマンド プロンプトで "Setup.exe /Action=RunDiscovery" を実行します。このコマンド ラインに "/q" を追加すると、UI は表示されませんが、レポートは %ProgramFiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\*nnn*\Setup Bootstrap\Log\\<最後のセットアップ セッション\> に作成されます。  
  
## <a name="see-also"></a>参照  
 [SQL Server セットアップ ログ ファイルの表示と読み取り](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
  
