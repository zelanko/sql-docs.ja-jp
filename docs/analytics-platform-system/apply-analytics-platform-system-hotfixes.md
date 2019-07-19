---
title: Analytics Platform System の修正プログラムの適用 |Microsoft Docs
description: この記事では、Analytics Platform System のソフトウェアに修正プログラムを適用する方法について説明します。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: d6af4a1eaf1e9891356fae40a3d3bb7f11e41dc6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961429"
---
# <a name="apply-analytics-platform-system-hotfixes"></a>Analytics Platform System の修正プログラムの適用
この記事では、Analytics Platform System のソフトウェアに修正プログラムを適用する方法について説明します。  
  
## <a name="before-you-begin"></a>はじめに  
  
> [!WARNING]  
> アプライアンスまたはアプライアンス コンポーネントがダウンしているかで、失敗した場合は、Analytics Platform System の修正プログラムを適用しないで状態にします。 その場合は、についてサポートに問い合わせてください。  
  
> [!WARNING]  
> アプライアンスを使用中に、Analytics Platform System の修正プログラムは適用されません。 修正プログラムを適用すると、アプライアンスのノードを再起動する可能性があります。 アプライアンスが使用されていないときに、メンテナンス期間中に、修正プログラムを適用する必要があります。  
  
### <a name="prerequisites"></a>必須コンポーネント  
次の手順を実行するには、必要があります。  
  
-   アプライアンスの状態を監視する管理コンソールにアクセスする権限を持つ、Analytics Platform System ログインします。 <!-- MISSING LINKS See [Grant Permissions to Use the Admin Console &#40;SQL Server PDW&#41;](../sqlpdw/grant-permissions-to-use-the-admin-console-sql-server-pdw.md).  -->  
  
-   接続に Fabric ドメイン管理者アカウントのサポート技術情報、 _< domain_name >_ **-HST01**ノード。  
  
## <a name="HowToInstallPDW"></a>Analytics Platform System の修正プログラムを適用するには  
Microsoft 更新プログラムとは異なり、Analytics Platform System のソフトウェアの修正プログラムが WSUS を介しては処理されません。 別のワークフローがあり、修正プログラム パッケージを実行してインストールされます。  
  
1.  **アプライアンスの状態インジケーターを確認します。**  
  
    1.  管理コンソールを開き、アプライアンスの状態 ページに移動します。 詳細については、次を参照してください[アプライアンスの監視、管理コンソールを使用して&#40;Analytics Platform System。&#41;](monitor-the-appliance-by-using-the-admin-console.md)  
  
    2.  次の手順に進む前に、すべての赤または黄色のインジケーターを解決する必要があります。 これにはいくつかの例外があります。  
  
        -   ディスク障害がある場合は、管理者コンソール [アラート] ページを使用して、各サーバーまたは SAN 配列内で複数のディスク障害が発生したことを確認します。 各サーバーまたは SAN 配列内の複数のディスク障害がある場合、ディスク エラーを修正する前に次の手順に進むことができます。 できるだけ早くディスク エラーを解決する Microsoft サポートに連絡してください。  
  
        -   C:\ ドライブではないに重大でない (黄色) のディスク ボリューム エラーがある場合、ディスク ボリュームのエラーを解決する前に、次の手順に進むことができます。  
  
2.  **Analytics Platform System の修正プログラムをインストールします。**  
  
    1.  ログインに、<*appliance_domain*>-ドメイン管理者として HST01 ノード。  
  
    2.  使用して、**管理者として実行**オプションをコマンド プロンプトを開きます。  
  
    3.  次のコマンドを実行して交換 *<HotfixPackageName>* 修正プログラムの実行可能パッケージ、および他の項目のプレース ホルダーを置き換えるの名前を持つ *< >* 適切な情報。  
  
        ```  
        <HotfixPackageName> /DomainAdminPassword="<password>"  
        ```  
  
    4.  修正プログラム パッケージによって表される手順に従います。  
  
## <a name="see-also"></a>関連項目  
[ダウンロードして Microsoft 更新プログラムを適用して&#40;Analytics Platform System&#41;](download-and-apply-microsoft-updates.md)  
[Microsoft 更新プログラムのアンインストール&#40;Analytics Platform System&#41;](uninstall-microsoft-updates.md)  
[Analytics Platform System の修正プログラムのアンインストール&#40;Analytics Platform System&#41;](uninstall-analytics-platform-system-hotfixes.md)  
[ソフトウェアのサービス&#40;Analytics Platform System&#41;](software-servicing.md)  
  
