---
title: '方法: アップグレード アドバイザー分析ウィザードを実行 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor Analysis Wizard
ms.assetid: d7d2a1e2-1179-4c05-9b0f-555b04dd1199
caps.latest.revision: 36
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 29aeaa20d5fed63731c84872ffb193da4bcfce27
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37282568"
---
# <a name="how-to-run-the-upgrade-advisor-analysis-wizard"></a>アップグレード アドバイザー分析ウィザードを実行する方法
  アップグレード アドバイザー分析ウィザードは、アップグレード アドバイザー開始ページから起動します。 ここでは、アップグレード アドバイザー分析ウィザードの実行方法について説明します。  
  
> [!IMPORTANT]  
>  アップグレード アドバイザー分析ウィザードを実行すると、アップグレード アドバイザーによって既定のレポート フォルダーにレポートが保存されます。 ただし、レポート ビューアーで表示されるのは、保存されている最近 5 件のレポートのみです。 レポートの既定の場所は、My Documents\\ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Upgrade advisor \110\reports です。  
  
### <a name="to-run-the-upgrade-advisor-analysis-wizard"></a>アップグレード アドバイザー分析ウィザードを実行するには  
  
1.  アップグレード アドバイザーの開始 ページで、**アップグレード アドバイザー分析ウィザードを起動**します。  
  
2.  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンポーネント** ページで、スキャン サーバーの名前を入力、**サーバー名**ボックスをクリックして**検出**します。 サーバー名については次のガイドラインに従ってください。  
  
    -   クラスター化されていないインスタンスをスキャンするには、コンピューター名を入力します。  
  
    -   クラスター化されたインスタンスをスキャンするには、仮想 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 名を入力します。  
  
    -   クラスターのノードにインストールされているクラスター化されていないコンポーネントをスキャンするには、ノード名を入力します。  
  
    > [!WARNING]  
    >  アップグレード アドバイザーは、クライアント接続に標準ポート (1433) を使用するように設定されていない [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスには接続できません。 標準ポート (1433) を使用していない [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続するには、IP アドレスとポートを使用して別名を作成します。 クライアント プロトコルの構成と別名の作成の詳細については[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスを参照してください[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md)します。  
    >   
    >  ない場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]アップグレード アドバイザーを実行しているコンピューターにインストール をクリックして**開始**、し、実行`cliconfg`します。 開き、  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント ネットワーク ユーティリティ** ダイアログ ボックス。 使用して、**エイリアス**タブは、エイリアスを作成します。  
  
3.  検出されたコンポーネントの一覧を確認に、必要に応じて、選択内容を変更してクリックして**次**します。  
  
4.  **接続パラメーター**のインスタンスを選択 ページで、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]スキャン、認証方法を選択して、必要に応じて、ユーザー名とパスワードの情報を入力し、クリックする**次**.  
  
     既定のインスタンス名は MSSQLSERVER です。  
  
5.  選択したコンポーネントに対し、必要な情報を入力します。 各ダイアログ ボックスの詳細については、次を参照してください。[アップグレード アドバイザーのユーザー インターフェイス リファレンス](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)します。  
  
6.  **アップグレード アドバイザーの設定を確認します** ページで入力した情報を確認します。 選択できる**にレポートを送信[!INCLUDE[msCoName](../../includes/msconame-md.md)]** アップグレード レポートを送信する場合。 プライバシー ポリシーを確認することもできます。  
  
7.  クリックして**実行**のインスタンスを分析する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  
  
8.  分析が完了したら、クリックして**レポートの起動**検出されたアップグレードの問題を表示します。  
  
## <a name="see-also"></a>参照  
 [方法: アップグレード アドバイザーの起動](../../../2014/sql-server/install/how-to-launch-upgrade-advisor.md)   
 [アップグレード アドバイザーを実行している&#40;ユーザー インターフェイス&#41;](../../../2014/sql-server/install/running-upgrade-advisor-user-interface.md)   
 [アップグレード アドバイザーの使用](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
