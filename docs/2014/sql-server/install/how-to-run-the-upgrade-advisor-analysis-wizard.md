---
title: '方法: アップグレード アドバイザー分析ウィザードを実行 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Upgrade Advisor Analysis Wizard
ms.assetid: d7d2a1e2-1179-4c05-9b0f-555b04dd1199
caps.latest.revision: 36
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 5ff92f0bb0cbf15e61895307d799415639a89eab
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36175881"
---
# <a name="how-to-run-the-upgrade-advisor-analysis-wizard"></a>アップグレード アドバイザー分析ウィザードを実行する方法
  アップグレード アドバイザー分析ウィザードは、アップグレード アドバイザー開始ページから起動します。 ここでは、アップグレード アドバイザー分析ウィザードの実行方法について説明します。  
  
> [!IMPORTANT]  
>  アップグレード アドバイザー分析ウィザードを実行すると、アップグレード アドバイザーによって既定のレポート フォルダーにレポートが保存されます。 ただし、レポート ビューアーで表示されるのは、保存されている最近 5 件のレポートのみです。 レポートの既定の場所を My Documents\\ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Upgrade advisor \110\reports です。  
  
### <a name="to-run-the-upgrade-advisor-analysis-wizard"></a>アップグレード アドバイザー分析ウィザードを実行するには  
  
1.  アップグレード アドバイザーの開始 ページで、**アップグレード アドバイザー分析ウィザードを起動して**です。  
  
2.  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンポーネント** ページで、スキャン サーバーの名前を入力、**サーバー名**ボックスをクリックして**検出**です。 サーバー名については次のガイドラインに従ってください。  
  
    -   クラスター化されていないインスタンスをスキャンするには、コンピューター名を入力します。  
  
    -   クラスター化されたインスタンスをスキャンするには、仮想 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 名を入力します。  
  
    -   クラスターのノードにインストールされているクラスター化されていないコンポーネントをスキャンするには、ノード名を入力します。  
  
    > [!WARNING]  
    >  アップグレード アドバイザーは、クライアント接続に標準ポート (1433) を使用するように設定されていない [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスには接続できません。 標準ポート (1433) を使用していない [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続するには、IP アドレスとポートを使用して別名を作成します。 クライアント プロトコルの構成と別名の作成の詳細については[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスを参照してください[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md)です。  
    >   
    >  ない場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をクリックしてアップグレード アドバイザーを実行しているコンピューターにインストールされて、**開始**、し、実行`cliconfg`です。 開き、  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント ネットワーク ユーティリティ** ダイアログ ボックス。 使用して、**エイリアス**タブは、別名を作成します。  
  
3.  検出されたコンポーネントの一覧を確認して、必要に応じて、選択内容を変更、およびをクリックして**次**です。  
  
4.  **接続パラメーター**のインスタンスの選択 ページで、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]スキャン、認証方法を選択して、必要に応じて、ユーザー名とパスワード情報を入力し、をクリックする**次**.  
  
     既定のインスタンス名は MSSQLSERVER です。  
  
5.  選択したコンポーネントに対し、必要な情報を入力します。 個々 のダイアログ ボックスの詳細については、次を参照してください。[アップグレード アドバイザーのユーザー インターフェイス リファレンス](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)です。  
  
6.  **アップグレード アドバイザーの設定を確認** ページで入力した情報を確認します。 選択できる**にレポートを送信[!INCLUDE[msCoName](../../includes/msconame-md.md)]** アップグレード レポートを送信する場合。 プライバシー ポリシーを確認することもできます。  
  
7.  をクリックして**実行**のインスタンスを分析する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
8.  分析が完了したら、をクリックして**レポートの起動**検出されたアップグレードの問題を表示します。  
  
## <a name="see-also"></a>参照  
 [方法: アップグレード アドバイザーを起動](../../../2014/sql-server/install/how-to-launch-upgrade-advisor.md)   
 [アップグレード アドバイザーを実行している&#40;ユーザー インターフェイス&#41;](../../../2014/sql-server/install/running-upgrade-advisor-user-interface.md)   
 [アップグレード アドバイザーの使用](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  