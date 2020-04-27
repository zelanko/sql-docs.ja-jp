---
title: SQL Server のインストールの検証 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- validating installations [SQL Server]
ms.assetid: 1689af50-d2b8-4aa6-8f27-cc7127157fc8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 34e4c29cb28f76c930f1f04152528ca1a8a89dfc
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62775235"
---
# <a name="validate-a-sql-server-installation"></a>SQL Server のインストールの検証
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の検出レポートは、コンピューターにインストールされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンおよび [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の機能を確認するために使用できます。 **インストール済み[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]機能の検出レポート**には、ローカル[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]サーバー [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]にインストール[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]さ[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]れて[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]いる、 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、、、、およびの各製品と機能のレポートが表示されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能の検出レポートは、 **インストール センターの** [ツール] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ページで利用できます。  
  
 **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能の検出レポートを実行するには**  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][スタート] **メニューを使用し、** [すべてのプログラム] **、** [ **[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]バージョン名>]\<、** [構成ツール] **の順にポイントし、** [ **インストール センター][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をクリックして、** インストール センターを起動します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能の検出レポートを実行するには、 **[** インストール センター] **の左側のナビゲーション領域にある [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][ツール]** をクリックし、 **[インストール済み [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能の検出レポート]** をクリックします。  
  
 検出[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]レポート\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、% ProgramFiles% \120\Setup Bootstrap\Log\\<最後のセットアップセッション\>に保存されます。  
  
 また、コマンド ラインから検出レポートを生成することができます。 コマンドプロンプトで "setup.exe/Action = rundiscovery" を実行します。上記のコマンドラインに "/q" を追加すると、UI は表示されませんが、レポートは% ProgramFiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<最後のセットアップ\>セッションで作成されます。  
  
## <a name="see-also"></a>参照  
 [SQL Server セットアップ ログ ファイルの表示と読み取り](view-and-read-sql-server-setup-log-files.md)  
  
  
