---
title: ドメイン管理者では、Analytics Platform System の作成 |Microsoft Docs
description: 一部の操作では、Analytics Platform System のドメイン管理者特権が必要です。 これには、ドメイン管理者の追加のアプライアンスを作成する方法について説明します。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 51ed729cda33b5d68a4d115c71f712e2b81d1a65
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961091"
---
# <a name="create-an-aps-domain-administrator"></a>APS ドメイン管理者を作成します。
一部の操作では、Analytics Platform System のドメイン管理者特権が必要です。 これには、ドメイン管理者の追加のアプライアンスを作成する方法について説明します。  
  
## <a name="create-a-domain-administrator"></a>ドメイン管理者を作成します。  
APS のすべてのノードを実行するユーザーを構成する十分なアクセス許可、 **AP Configuration Manager** (`dwconfig.exe`) のメンバーである必要があります、 **Domain Admins**グループ。 ユーザーを開始し、AP サービスの停止のメンバーである必要があります、 **PdwControlNodeAccess**グループ。  
  
#### <a name="to-add-a-user-to-the-domain-admins-group"></a>Domain Admins グループにユーザーを追加するには  
  
1.  アクティブな AD ノードにログイン **(_アプライアンス\_ドメイン_-AD01** または **_アプライアンス\_ドメイン_-AD02**)既存のアプライアンス ドメイン管理者アカウントを使用します。  
  
2.  [スタート] メニューの **[ファイル名を指定して実行]** をクリックします。 **オープン**ボックスに「 **dsa.msc**します。 **[OK]** をクリックします。  
  
3.  **Active Directory ユーザーとコンピューター**プログラムを右クリックして**ユーザー**、 をポイント**新規**、 をクリックし、**ユーザー**します。  
  
4.  **新しいオブジェクト - ユーザー**  ダイアログ ボックスでは、新しいユーザーの説明を完了し、順にクリックします**次**します。  
  
    パスワード ダイアログ ボックスをクリックして**次**します。  
  
    > [!WARNING]  
    > SQL Server PDW では、ドメイン管理者またはローカル管理者パスワードのドル記号 ($) をサポートしません。 ドル記号を含むパスワードは有効なと使用できるが、アップグレード、およびメンテナンス アクティビティをブロックすることができます。  
  
    クリックして、新しいユーザーの説明を確認**完了**します。  
  
5.  ユーザーの一覧で、ユーザーのプロパティ ダイアログ ボックスに新しいユーザーをダブルクリックします。  
  
6.  **メンバーの**] タブで [**追加**します。  
  
    型**Domain Admins です。PdwControlNodeAccess**し**名前の確認**します。 **[OK]** をクリックします。  
  
    新しいユーザーが追加されます、 **Domain Admins**グループと**PdwControlNodeAccess**グループ。 **[OK]** をクリックします。  
  
## <a name="see-also"></a>関連項目  
[Configuration Manager の起動&#40;Analytics Platform System&#41;](launch-the-configuration-manager.md)  
  
