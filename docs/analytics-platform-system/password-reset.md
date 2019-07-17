---
title: パスワード リセット - Analytics Platform System |Microsoft Docs
description: パスワードのリセット ページでは、Analytics Platform System で使用される管理者アカウントのパスワードを変更することができます。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 5fb3bbb5adba5754c220c34503a22656f6da39c5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960468"
---
# <a name="password-reset---analytics-platform-system"></a>パスワード リセット - Analytics Platform System
**パスワードのリセット** ページでは、Analytics Platform System で使用される管理者アカウントのパスワードを変更することができます。  
  
> [!WARNING]  
> 常に使用して、 **Configuration Manager**アプライアンス ドメイン管理者のパスワードを更新します。 その他のメソッドでは、Analytics Platform System のすべてのコンポーネントを更新できなかった可能性が、アプライアンスへのアクセスの問題が発生する可能性があります。  
  
アプライアンスが配信されるとき、Analytics Platform System のパスワードが表示されます。 アプライアンスの責任を取得するときに常にパスワードを新しい値に変更します。 3 つのパスワードを更新するにがあります。 パスワードを互いに同じにする必要はありません。  
  
**F<*xxxx*>\Administrator**  
**管理者**のアプライアンスのドメイン。  
  
**.\Administrator**  
ローカル**管理者**仮想マシンをホストするコンピューターのアカウント。  
  
> [!IMPORTANT]  
> アプライアンスの update 1、 **Configuration Manager**全体にわたって、PDW VM のローカル管理者アカウントのパスワードが正しく変更しません。 これが必要な場合は、その他については CSS に問い合わせてください。  
  
**sa**  
**Sa** SQL Server にログインします。 **sa**のメンバーである、 **sysadmin** SQL Server の管理者であり、固定サーバー ロール。 パスワード、 **sa**を使用してログインを変更することも、 **ALTER LOGIN**ステートメント。  
  
## <a name="password-requirements"></a>パスワードの要件  
ドメイン管理者の資格情報とシステム管理者の資格情報の両方は、資格情報の種類ごとにパスワードの強度のポリシーに準拠します。 ドメインに新しいパスワードが更新ドメイン管理者の資格情報を変更するときに SQL Server PDW 全体で必要な場所。  
  
> [!IMPORTANT]  
> SQL Server PDW はドル記号をサポートしていません ( **$** ) で、ドメイン管理者またはローカル管理者パスワード。 文字 **^ % &** は、PowerShell は、これらの特殊文字が、パスワードで許可されています。 これらの文字は、システム管理者または SQL Server のパスワードで使用されている場合**sa**アカウント (、 **AdminPassword**と**PdwSAPassword**時にパラメーターセットアップ) をセットアップしなどのインストール、アップグレード、REPLACENODE、および、修正プログラムの適用は失敗します。 現在のパスワードには、サポートされていない文字が含まれている場合は、アップグレードの成功を確実に、アップグレードを実行する前にこのような文字がないように、これらのパスワードを変更します。 アップグレードの完了後は、元の値にこれらのパスワードを設定できます。 パスワードの要件の詳細については、次を参照してください。 [ALTER LOGIN](../t-sql/statements/alter-login-transact-sql.md)します。  
  
## <a name="to-reset-a-password"></a>パスワードをリセットするには  
  
1.  起動と制御ノードに接続して、 **Configuration Manager** (**dwconfig.exe**)。 詳細については、次を参照してください。 [Configuration Manager の起動&#40;Analytics Platform System&#41;](launch-the-configuration-manager.md)します。  
  
2.  左側のウィンドウで、 **Configuration Manager**、 をクリックして**パスワードのリセット**します。  
  
3.  管理者の種類を選択、**アカウント**ドロップダウン メニューでは、新しいパスワードを入力し、**パスワード**と**パスワードの確認**ボックス。 クリックして**適用**変更を保存します。  
  
    これらのアカウントに加えた変更は、現在アクティブなセッションには影響しませんが、各ユーザーの次回のログオンで適用されます。  
  
    ![SQL Server DWConfig パスワード](./media/password-reset/SQL_Server_PDW_DWConfig_TopPW.png "SQL_Server_PDW_DWConfig_TopPW")  
  
## <a name="see-also"></a>関連項目  
[ディレクトリ サービス復元モードで AD ノードにログオンするための管理者パスワードを設定&#40;DSRM&#41; &#40;Analytics Platform System&#41;](set-admin-password-for-logging-on-to-ad-nodes-in-directory-services-restore-mode.md)  
[Configuration Manager の起動&#40;Analytics Platform System&#41;](launch-the-configuration-manager.md)  
  
