---
title: "[ディストリビューション データベースのプロパティ] | Microsoft Docs"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.rep.configdistwizard.distdbproperties.f1
helpviewer_keywords: Distribution Database Properties dialog box
ms.assetid: 0f404ab9-1237-4936-8df5-888baab6a245
caps.latest.revision: "23"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6116c7ba186ca3f51172c46d60dd2bcc8ca96fe8
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="distribution-database-properties"></a>[ディストリビューション データベースのプロパティ]
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] **[ディストリビューション データベースのプロパティ]** ダイアログ ボックスを使用すると、多数のプロパティを表示でき、データベースにおけるトランザクションの保有期間と履歴の保有期間を設定できます。  
  
## <a name="options"></a>オプション  
 **名前**  
 ディストリビューション データベースの名前です。既定の名前は "distribution" です (読み取り専用)。  
  
 **[ファイルの場所]**  
 データベース ファイルとログ ファイルの場所です (読み取り専用)。  
  
 **[トランザクションの保有期間]**  
 ディストリビューション保有期間とも呼ばれます。 トランザクション レプリケーションで格納されるトランザクションの期間の長さです。 詳細については、「 [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md)」をご覧ください。  
  
 **[履歴の保有期間]**  
 すべての種類のレプリケーションで格納される、履歴メタデータの期間の長さです。  
  
 **[キュー リーダー エージェントのセキュリティ]**  
 キュー リーダー エージェントは、トランザクション レプリケーションのキュー更新サブスクリプションで使用されます。 パブリケーションの新規作成ウィザードの **[パブリケーションの種類]** ページで **[更新可能なサブスクリプションを含むトランザクション パブリケーション]** を選択すると、キュー リーダー エージェントが自動的に作成されます。 エージェントの実行や、ディストリビューターへの接続の作成に使用するアカウントを変更するには、 **[セキュリティ設定]** をクリックします。  
  
 キュー リーダー エージェントは、このページの **[キュー リーダー エージェントを作成する]** を選択することでも作成できます (キュー リーダー エージェントが既に作成されている場合、このオプションは無効になります)。  
  
 キュー リーダー エージェントのその他の接続情報は、次の 2 つの場所で指定されます。  
  
-   **[パブリッシャーのプロパティ]** ダイアログ ボックス。エージェントは、このダイアログ ボックスで指定された資格情報を使用してパブリッシャーに接続します。このダイアログ ボックスは、 **[ディストリビューターのプロパティ]** ダイアログ ボックスの **[パブリッシャー]** ページから開きます。  
  
-   サブスクリプションの新規作成ウィザードの [ディストリビューション エージェント]。エージェントは、ここで指定された資格情報を使用してサブスクライバーに接続します。  
  
 詳細については、「  [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [ディストリビューションの構成](../../relational-databases/replication/configure-distribution.md)   
 [プル サブスクリプションの作成](../../relational-databases/replication/create-a-pull-subscription.md)   
 [ssSDSFull](../../relational-databases/replication/create-a-push-subscription.md)   
 [ディストリビューターとパブリッシャーのプロパティの表示および変更](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)  
  
  
