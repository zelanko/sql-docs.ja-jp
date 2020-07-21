---
title: '方法: Upgrade Advisor をインストールする |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- Setup [Upgrade Advisor]
- SQL Server Upgrade Advisor, installing
- Upgrade Advisor [SQL Server], installing
ms.assetid: 481b0704-ce79-4543-b141-67306128aa2b
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ac1488cd9a42a8f7e212fe533615dbb131fe7290
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059308"
---
# <a name="how-to-install-upgrade-advisor"></a>アップグレード アドバイザーをインストールする方法
  アップグレード アドバイザーでは、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 以外のサポートされているすべてのコンポーネントをリモートで分析できます。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のインスタンスをスキャンしない場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続できる任意のコンピューターにアップグレード アドバイザーをインストールできます。 コンピューターはアップグレード アドバイザーの前提条件を満たしている必要もあります。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のインスタンスをスキャンする場合は、アップグレード アドバイザーをレポート サーバーにインストールする必要があります。  
  
 詳細については、「 [Upgrade Advisor のインストール](../../../2014/sql-server/install/installing-upgrade-advisor.md)」を参照してください。  
  
### <a name="to-install-upgrade-advisor"></a>アップグレード アドバイザーをインストールするには  
  
1.  次の方法のいずれかを使用してインストールを開始します。  
  
    -   Web サイトからをインストールする場合は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [**ダウンロード**] リンクをクリックし、[**実行**] ボタンをクリックしてインストールを開始します。  
  
    -   製品メディアからインストールする場合は、 **redist**フォルダーを開き、**アップグレードアドバイザー**フォルダーを開き、[ **SQLUA.msi**] をダブルクリックします。  
  
    > [!NOTE]  
    >  アップグレード アドバイザーを使用するには、[!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 4 が必要です。 インストールされていない場合やバージョンが古い場合は、エラー メッセージが表示されます。 古いバージョンの [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] をアンインストールしてから、最新バージョンの .NET Framework 4 をインストールします。  
    >   
    >  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] Scriptdom はアップグレードアドバイザーをインストールするための前提条件で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] あり、アップグレードアドバイザーのセットアップではインストールされません。 セットアップでは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] Feature Pack から scriptdom をダウンロードしてインストールする必要があり [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ます。  
  
2.  [ ** [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Upgrade Advisor セットアップの開始**] ページで、[**次へ**] をクリックします。  
  
3.  [**使用許諾契約書**] ページで、使用許諾契約書を読みます。 同意する場合は、[**使用許諾契約書に同意**します] を選択し、[**次へ**] をクリックします。  
  
4.  [**登録情報**] ページで、名前と会社を入力します。  
  
5.  [**機能の選択**] ページで、[**インストールパス**] の値を確認します。 必要に応じて、[**参照**] ボタンを使用して場所を変更します。 **[次へ]** をクリックします。  
  
6.  [**プログラムのインストールの準備完了**] ページで、[**インストール**] をクリックしてアップグレードアドバイザーをインストールします。  
  
7.  **[完了]** をクリックして、ウィザードを終了します。  
  
## <a name="see-also"></a>参照  
 [アップグレード アドバイザーの前提条件](../../../2014/sql-server/install/upgrade-advisor-prerequisites.md)  
  
  
