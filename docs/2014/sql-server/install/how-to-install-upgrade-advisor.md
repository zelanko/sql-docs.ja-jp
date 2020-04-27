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
manager: craigg
ms.openlocfilehash: 0de86b9690f0647803938218ce566508662da20e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66094918"
---
# <a name="how-to-install-upgrade-advisor"></a>アップグレード アドバイザーをインストールする方法
  アップグレード アドバイザーでは、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 以外のサポートされているすべてのコンポーネントをリモートで分析できます。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のインスタンスをスキャンしない場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続できる任意のコンピューターにアップグレード アドバイザーをインストールできます。 コンピューターはアップグレード アドバイザーの前提条件を満たしている必要もあります。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のインスタンスをスキャンする場合は、アップグレード アドバイザーをレポート サーバーにインストールする必要があります。  
  
 詳細については、「 [Upgrade Advisor のインストール](../../../2014/sql-server/install/installing-upgrade-advisor.md)」を参照してください。  
  
### <a name="to-install-upgrade-advisor"></a>アップグレード アドバイザーをインストールするには  
  
1.  次の方法のいずれかを使用してインストールを開始します。  
  
    -   Web サイトからをインストールする場合は、[**ダウンロード**] リンクをクリックし、[実行] ボタンをクリックしてインストールを開始します。 **Run** [!INCLUDE[msCoName](../../includes/msconame-md.md)]  
  
    -   製品メディアからをインストールする場合は、 **redist**フォルダーを開き、**アップグレードアドバイザー**フォルダーを開き、[ **sqlua .msi**] をダブルクリックします。  
  
    > [!NOTE]  
    >  アップグレード アドバイザーを使用するには、[!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 4 が必要です。 インストールされていない場合やバージョンが古い場合は、エラー メッセージが表示されます。 古いバージョンの [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] をアンインストールしてから、最新バージョンの .NET Framework 4 をインストールします。  
    >   
    >  Scriptdom [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]はアップグレードアドバイザーをインストールするための前提条件であり、アップグレードアドバイザーのセットアップではインストールされません。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] セットアップで[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)]は、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Feature Pack から scriptdom をダウンロードしてインストールする必要があります。  
  
2.  [ **Upgrade Advisor セットアップの[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]開始**] ページで、[**次へ**] をクリックします。  
  
3.  [**使用許諾契約書**] ページで、使用許諾契約書を読みます。 同意する場合は、[**使用許諾契約書に同意**します] を選択し、[**次へ**] をクリックします。  
  
4.  [**登録情報**] ページで、名前と会社を入力します。  
  
5.  [**機能の選択**] ページで、[**インストールパス**] の値を確認します。 必要に応じて、[**参照**] ボタンを使用して場所を変更します。 **[次へ]** をクリックします。  
  
6.  [**プログラムのインストールの準備完了**] ページで、[**インストール**] をクリックしてアップグレードアドバイザーをインストールします。  
  
7.  **[完了]** をクリックして、ウィザードを終了します。  
  
## <a name="see-also"></a>参照  
 [アップグレード アドバイザーの前提条件](../../../2014/sql-server/install/upgrade-advisor-prerequisites.md)  
  
  
