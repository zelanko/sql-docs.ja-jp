---
title: ディレクトリ サービス復元モード (AP) の AD ノードの管理者ログオン パスワードを設定します。
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 97a9c715-2763-417d-b45c-bb0180759e47
caps.latest.revision: 20
ms.openlocfilehash: 3e09305152a2892ae4acaf7096921d2a73345b63
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="set-admin-password-for-logging-on-to-ad-nodes-in-directory-services-restore-mode-dsrm"></a>ディレクトリ サービス復元モード (DSRM) での AD ノードにログオンするための管理者パスワードの設定します。
ディレクトリ サービス復元モード (DSRM) は、修復、または Active Directory ドメイン サービス (AD DS) の復元のブート モードです。 AD DS が失敗した後、または AD DS は、復元する必要がある場合、AD アプライアンスのノードにログオンに使用されます。 DSRM のパスワードは、ハードウェア ベンダー サイトのアプライアンス セットアップ時に初期化されており、アプライアンスの管理者によって変更する必要があります。 Analytics Platform System が 2 つの AD DS (ドメイン コント ローラー)***appliance_domain *-AD01**と ***appliance_domain *-AD02**です。 アプライアンス AD ノードごとに、次の手順を使用して、DSRM パスワードを変更します。  
  
## <a name="HowToDSRM"></a>管理者パスワードをリセットするには  
  
1.  アプライアンス AD ノードでコマンド プロンプト ウィンドウを開いて***appliance_domain*– AD*xx***仮想マシン。  
  
2.  コマンド プロンプトで次のように入力します。`ntdsutil`です。  
  
3.  **Ntdsutil**プロンプトで「`set dsrm password`です。  
  
4.  **管理者パスワードのリセット:**プロンプトで「`reset password on server null`です。  
  
5.  プロンプトで、新しいパスワードを入力します。  
  
6.  アプライアンス AD の仮想マシンごとに 1 ~ 5 の上の手順を繰り返します。  
  
    > [!WARNING]  
    > Analytics Platform System はサポートされていません、ドル記号 ($) は、ドメイン管理者またはローカル管理者パスワード。 ドル記号を含むパスワードは検証し、する操作可能なアップグレードおよびメンテナンス アクティビティをブロックすることができます。  
  
> [!NOTE]  
> AD の仮想マシンを特定の Active Directory ドメイン サービスまたはバーチャル マシンが破損した場合に実行されている**ReplaceVM**影響を受ける AD の仮想マシンは、推奨される修正措置です。 サポートが必要な CSS に問い合わせます。  
  
## <a name="see-also"></a>参照  
[パスワードのリセット&#40;分析プラットフォーム システム&#41;](password-reset.md)  
  
