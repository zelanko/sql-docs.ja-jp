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
ms.openlocfilehash: 8dd4e6ce7800c3a0a9db51f6c1a4bddfe7a188c3
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84931693"
---
# <a name="validate-a-sql-server-installation"></a>SQL Server のインストールの検証
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の検出レポートは、コンピューターにインストールされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンおよび [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の機能を確認するために使用できます。 **インストール済み [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能の検出レポート**には、 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] ローカルサーバーにインストールされている、、、、、およびの各製品と機能のレポートが表示されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能の検出レポートは、 **インストール センターの** [ツール] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ページで利用できます。  
  
 **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能の検出レポートを実行するには**  
  
 インストールセンターを起動します。 [スタート] ボタンをクリックし、[ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] すべて** [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \<Version Name> **の**プログラム**]、[]、[**構成ツール**] の順にポイントし、[ ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストールセンター**] をクリックします。 **Start** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能の検出レポートを実行するには、**[[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール センター]** の左側のナビゲーション領域にある **[ツール]** をクリックし、**[インストール済み [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能の検出レポート]** をクリックします。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]検出レポートは、% ProgramFiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<最後のセットアップセッションに保存され \> ます。  
  
 また、コマンド ラインから検出レポートを生成することができます。 コマンドプロンプトから "Setup.exe/Action = rundiscovery" を実行します。上記のコマンドラインに "/q" を追加すると、UI は表示されませんが、レポートは% ProgramFiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<最後のセットアップセッションで作成され \> ます。  
  
## <a name="see-also"></a>参照  
 [SQL Server セットアップ ログ ファイルの表示と読み取り](view-and-read-sql-server-setup-log-files.md)  
  
  
