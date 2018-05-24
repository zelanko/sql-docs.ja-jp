---
title: Analytics Platform System Active Directory パスワードを設定 |Microsoft ドキュメント
description: Analytics Platform System (APS) ディレクトリ サービス復元モードでは、Active Directory ノードの管理者ログオン パスワードを設定します。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: e74689216c1485fc0c11c588acb151269e2b5d2b
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="set-admin-password-for-logging-on-to-ad-nodes-in-directory-services-restore-mode-dsrm---analytics-platform-system"></a>ディレクトリ サービス内の AD のノードにログオン復元モード (DSRM) - Analytics Platform System の管理者パスワードを設定します。
ディレクトリ サービス復元モード (DSRM) は、修復、または Active Directory ドメイン サービス (AD DS) の復元のブート モードです。 AD DS が失敗した後、または AD DS は、復元する必要がある場合、AD アプライアンスのノードにログオンに使用されます。 DSRM のパスワードは、ハードウェア ベンダー サイトのアプライアンス セットアップ時に初期化されており、アプライアンスの管理者によって変更する必要があります。 Analytics Platform System が 2 つの AD DS (ドメイン コント ローラー)***appliance_domain *-AD01**と ***appliance_domain *-AD02**です。 アプライアンス AD ノードごとに、次の手順を使用して、DSRM パスワードを変更します。  
  
## <a name="HowToDSRM"></a>管理者パスワードをリセットするには  
  
1.  アプライアンス AD ノードでコマンド プロンプト ウィンドウを開いて***appliance_domain *– AD*xx***仮想マシン。  
  
2.  コマンド プロンプトで次のように入力します。`ntdsutil`です。  
  
3.  **Ntdsutil**プロンプトで「`set dsrm password`です。  
  
4.  **管理者パスワードのリセット:** プロンプトで「`reset password on server null`です。  
  
5.  プロンプトで、新しいパスワードを入力します。  
  
6.  アプライアンス AD の仮想マシンごとに 1 ~ 5 の上の手順を繰り返します。  
  
    > [!WARNING]  
    > Analytics Platform System はサポートされていません、ドル記号 ($) は、ドメイン管理者またはローカル管理者パスワード。 ドル記号を含むパスワードは検証し、する操作可能なアップグレードおよびメンテナンス アクティビティをブロックすることができます。  
  
> [!NOTE]  
> AD の仮想マシンを特定の Active Directory ドメイン サービスまたはバーチャル マシンが破損した場合に実行されている**ReplaceVM**影響を受ける AD の仮想マシンは、推奨される修正措置です。 サポートが必要な CSS に問い合わせます。  
  
## <a name="see-also"></a>参照  
[パスワードのリセット&#40;分析プラットフォーム システム&#41;](password-reset.md)  
  
