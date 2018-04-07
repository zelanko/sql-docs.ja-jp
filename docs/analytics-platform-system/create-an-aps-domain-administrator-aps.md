---
title: APS ドメイン管理者 (AP) を作成します。
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
ms.assetid: ed52bf78-2b0a-4252-98a7-8c2805e22d3d
caps.latest.revision: 7
ms.openlocfilehash: 6842992931ba35f450d49d6db9beb803dce6b73a
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="create-an-aps-domain-administrator"></a>APS ドメイン管理者を作成します。
一部の操作では、Analytics Platform System ドメイン管理者特権が必要です。 これには、ドメイン管理者の追加のアプライアンスを作成する方法について説明します。  
  
## <a name="create-a-domain-administrator"></a>ドメイン管理者を作成します。  
APS のすべてのノードを実行するユーザーを構成する十分なアクセス許可、 **APS Configuration Manager** (`dwconfig.exe`) のメンバーである必要があります、 **Domain Admins**グループ。 ユーザーを開始および APS サービスを停止のメンバーである必要があります、 **PdwControlNodeAccess**グループ。  
  
#### <a name="to-add-a-user-to-the-domain-admins-group"></a>Domain Admins グループにユーザーを追加するには  
  
1.  アクティブな AD ノードへのログイン**(*appliance_domain*-AD01**または ***appliance_domain *-AD02**) 既存のアプライアンス ドメイン管理者アカウントを使用します。  
  
2.  [スタート] メニューの **[ファイル名を指定して実行]**をクリックします。 **開く**ボックスに、入力**dsa.msc**です。 **[OK]**をクリックします。  
  
3.  **Active Directory ユーザーとコンピューター**プログラムを右クリックして**ユーザー**、 をポイント**新規**、クリックして**ユーザー**です。  
  
4.  **新しいオブジェクト-ユーザー**  ダイアログ ボックスは、新しいユーザーの説明を完了し、をクリックして**次**です。  
  
    パスワード ダイアログ ボックスを完了し、をクリックして**次**です。  
  
    > [!WARNING]  
    > SQL Server PDW はサポートされていません、ドル記号 ($) は、ドメイン管理者またはローカル管理者パスワード。 ドル記号を含むパスワードは有効なと使用できるようにするが、アップグレードおよびメンテナンス アクティビティをブロックすることができます。  
  
    新しいユーザーの説明を確認し、をクリックして**完了**です。  
  
5.  ユーザーの一覧で、新しいユーザーを開くには、ユーザーのプロパティ ダイアログ ボックスをダブルクリックします。  
  
6.  **メンバーの** タブで、をクリックして**追加**です。  
  
    型**Domain Admins です。PdwControlNodeAccess**  をクリックし、**名前の確認**です。 **[OK]**をクリックします。  
  
    新しいユーザーを追加、 **Domain Admins**グループおよび**PdwControlNodeAccess**グループ。 **[OK]**をクリックします。  
  
## <a name="see-also"></a>参照  
[構成マネージャーを起動&#40;分析プラットフォーム システム&#41;](launch-the-configuration-manager.md)  
  
