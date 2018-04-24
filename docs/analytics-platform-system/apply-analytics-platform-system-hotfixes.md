---
title: Analytics Platform System の修正プログラム適用 |Microsoft ドキュメント
description: この記事では、分析プラットフォーム システム ソフトウェアの修正プログラムを適用する方法について説明します。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: b3a7a31ce791fbe44c38d1d30ce408235720e241
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="apply-analytics-platform-system-hotfixes"></a>Analytics Platform System の修正プログラムを適用します。
この記事では、分析プラットフォーム システム ソフトウェアの修正プログラムを適用する方法について説明します。  
  
## <a name="before-you-begin"></a>はじめに  
  
> [!WARNING]  
> 場合は、アプライアンスまたはアプライアンス コンポーネントがダウンしているか、失敗の分析プラットフォーム システム修正プログラムを適用しないでの状態の上です。 その場合は、サポートが必要なサポートに問い合わせてください。  
  
> [!WARNING]  
> アプライアンスの使用中に、Analytics Platform System の修正プログラムは適用されません。 修正プログラムの適用、アプライアンスのノードを再起動する可能性があります。 アプライアンスが使用されていないときに、メンテナンス期間中に、修正プログラムを適用する必要があります。  
  
### <a name="prerequisites"></a>前提条件  
次の手順を実行するには、必要があります。  
  
-   アプライアンスの状態を監視する管理コンソールにアクセスする権限を持つ分析プラットフォーム システム ログインします。 <!-- MISSING LINKS See [Grant Permissions to Use the Admin Console &#40;SQL Server PDW&#41;](../sqlpdw/grant-permissions-to-use-the-admin-console-sql-server-pdw.md).  -->  
  
-   接続に、ファブリック管理者はドメイン アカウントのナレッジ、 *< domain_name > * * *-HST01** ノード。  
  
## <a name="HowToInstallPDW"></a>Analytics Platform System 修正プログラムを適用するには  
Microsoft 更新プログラムとは異なり、Analytics Platform System ソフトウェアの修正プログラムは WSUS を介して処理されません。 別のワークフローと修正プログラム パッケージを実行してインストールされます。  
  
1.  **アプライアンスの状態インジケーターを確認します。**  
  
    1.  管理コンソールを開き、アプライアンスの状態 ページに移動します。 詳細については、次を参照してください[アプライアンスを管理コンソールを使用して監視&#40;分析プラットフォーム システム。&#41;](monitor-the-appliance-by-using-the-admin-console.md)  
  
    2.  次の手順に進む前に、すべての赤または黄色のインジケーターを解決する必要があります。 これにはいくつかの例外があります。  
  
        -   ディスクの障害がある場合は、管理者コンソール [アラート] ページを使用して、各サーバーまたは SAN 配列内の 2 つ以上のディスク障害が発生したことを確認します。 各サーバーまたは SAN 配列内の 2 つ以上のディスク障害がある場合、ディスク エラーを修正する前に、次の手順を続行することができます。 ディスク エラーをできるだけ早く修正を Microsoft サポートに問い合わせることを確認します。  
  
        -   C:\ ドライブにないに重大でない (黄色) のディスク ボリューム エラーがある場合、ディスク ボリュームのエラーを解決する前に、次の手順を続行することができます。  
  
2.  **Analytics Platform System 修正プログラムをインストールします。**  
  
    1.  ログインに、<*appliance_domain*>-ドメイン管理者として HST01 ノード。  
  
    2.  使用して、**管理者として実行**コマンド プロンプトを開くにはオプションです。  
  
    3.  次のコマンドを実行交換*<HotfixPackageName>*修正プログラムの実行可能パッケージ、および他の項目のプレース ホルダーを置換の名前を持つ*< >*適切な情報です。  
  
        ```  
        <HotfixPackageName> /DomainAdminPassword="<password>"  
        ```  
  
    4.  修正プログラム パッケージに示されている手順に従います。  
  
## <a name="see-also"></a>参照  
[ダウンロードして Microsoft 更新プログラムを適用して&#40;分析プラットフォーム システム&#41;](download-and-apply-microsoft-updates.md)  
[Microsoft 更新プログラムのアンインストール&#40;分析プラットフォーム システム&#41;](uninstall-microsoft-updates.md)  
[分析プラットフォーム システムの修正プログラムをアンインストール&#40;分析プラットフォーム システム&#41;](uninstall-analytics-platform-system-hotfixes.md)  
[ソフトウェア サービス&#40;分析プラットフォーム システム&#41;](software-servicing.md)  
  
