---
title: SQL Server 2014 サービス更新プログラムのインストール |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 7d6c962b-c8d0-49f7-a2ac-00ad8dca930a
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 07f438f86a22b866351a0b83ee7634338f3ad2cd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62775345"
---
# <a name="install-sql-server-2014-servicing-updates"></a>SQL Server 2014 サービス更新プログラムのインストール
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]の更新プログラムのインストールについて説明します。 このセクションでは、次の項目について説明します。  
  
-   新規インストール時に [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の更新プログラムをインストールする  
  
-   既にインストールされている [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の更新プログラムをインストールする  
  
 常に最新のセキュリティ更新プログラムがインストールされた状態になるように、適切なタイミングで最新の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 更新プログラムを評価してインストールすることをお勧めします。  
  
## <a name="installing-updates-for-includesscurrentincludessscurrent-mdmd-during-a-new-installation"></a>新規インストール時に [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の更新プログラムをインストールする  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップでは、メインの製品とそれに適用可能な更新プログラムが同時にインストールされるように、最新の製品の更新プログラムとメインの製品のインストールが統合されています。 製品の更新プログラムでは、次の場所から適用可能な更新プログラムが検索されます。  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update  
  
-   Windows Server Update Services (WSUS)  
  
-   ローカル フォルダー  
  
-   ネットワーク共有  
  
 セットアップで最新バージョンの適用可能な更新プログラムが検出されると、ダウンロードが実行されて、現在の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のセットアップ プロセスと統合されます。 製品の更新プログラムには、累積更新プログラム、サービス パック、またはサービス パックと累積更新プログラムが含まれる場合があります。 製品の更新プログラム機能は、PCU1 で[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]提供されていた[スリップストリーム機能](https://go.microsoft.com/fwlink/?LinkId=219945)を拡張したものです。  
  
## <a name="installing-updates-for-includesscurrentincludessscurrent-mdmd-after-it-has-already-been-installed"></a>既にインストールされている [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の更新プログラムをインストールする  
 のインストール済みインスタンスで[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]は、利用可能なすべての更新プログラム (一般配布リリース (GDR-security/critical updates)、Service PACK (SP)、および使用可能な最新の累積的な更新プログラム (CU)) を適用することをお勧めします。  
  
 サービスリリースの種類に応じて、SQL Server の更新プログラムは、Microsoft Update (MU)、Microsoft ダウンロードセンター、またはカスタマーサポートサービス修正プログラムサーバーを通じて入手できます。 SQL Server のセキュリティ更新プログラムと重要な更新プログラムは、Microsoft Update によって自動的に提供されます (MU にオプトインするために必要なこれらの更新プログラムをコントロールパネルの Windows Update で確認できるようにするため)。 Service Pack は、MU のダウンロードセンターだけでなく、オプション/重要ダウンロードとしても利用できます。 累積更新プログラムは、CU サポート技術情報の記事に記載されている Microsoft 修正プログラムダウンロードサーバーから入手できます。  
  
## <a name="see-also"></a>参照  
 [インストールウィザード &#40;セットアップから SQL Server 2014 をインストール&#41;](install-sql-server-from-the-installation-wizard-setup.md)   
 [コマンドプロンプトから更新プログラムをインストール](installing-updates-from-the-command-prompt.md)[する SQL Server 2014 &#40;セットアップのインスタンスに機能を追加&#41;](add-features-to-an-instance-of-sql-server-setup.md)   
 [SQL Server 2014 のインストールの削除](repair-a-failed-sql-server-installation.md)  
  
  
