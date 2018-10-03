---
title: '[ディストリビューション データベースのプロパティ] | Microsoft Docs'
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.configdistwizard.distdbproperties.f1
helpviewer_keywords:
- Distribution Database Properties dialog box
ms.assetid: 0f404ab9-1237-4936-8df5-888baab6a245
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0412108c9b08e8b3345f4930b4076e10c96ec2ce
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48207712"
---
# <a name="distribution-database-properties"></a>[ディストリビューション データベースのプロパティ]
  **[ディストリビューション データベースのプロパティ]** ダイアログ ボックスを使用すると、多数のプロパティを表示でき、データベースにおけるトランザクションの保有期間と履歴の保有期間を設定できます。  
  
## <a name="options"></a>および  
 **名前**  
 ディストリビューション データベースの名前です。既定の名前は "distribution" です (読み取り専用)。  
  
 **[ファイルの場所]**  
 データベース ファイルとログ ファイルの場所です (読み取り専用)。  
  
 **[トランザクションの保有期間]**  
 ディストリビューション保有期間とも呼ばれます。 トランザクション レプリケーションで格納されるトランザクションの期間の長さです。 詳細については、「 [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md)」をご覧ください。  
  
 **[履歴の保有期間]**  
 すべての種類のレプリケーションで格納される、履歴メタデータの期間の長さです。  
  
 **[キュー リーダー エージェントのセキュリティ]**  
 キュー リーダー エージェントは、トランザクション レプリケーションのキュー更新サブスクリプションで使用されます。 パブリケーションの新規作成ウィザードの **[パブリケーションの種類]** ページで **[更新可能なサブスクリプションを含むトランザクション パブリケーション]** を選択すると、キュー リーダー エージェントが自動的に作成されます。 エージェントの実行や、ディストリビューターへの接続の作成に使用するアカウントを変更するには、 **[セキュリティ設定]** をクリックします。  
  
 キュー リーダー エージェントは、このページの **[キュー リーダー エージェントを作成する]** を選択することでも作成できます (キュー リーダー エージェントが既に作成されている場合、このオプションは無効になります)。  
  
 キュー リーダー エージェントのその他の接続情報は、次の 2 つの場所で指定されます。  
  
-   **[パブリッシャーのプロパティ]** ダイアログ ボックス。エージェントは、このダイアログ ボックスで指定された資格情報を使用してパブリッシャーに接続します。このダイアログ ボックスは、 **[ディストリビューターのプロパティ]** ダイアログ ボックスの **[パブリッシャー]** ページから開きます。  
  
-   サブスクリプションの新規作成ウィザードの [ディストリビューション エージェント]。エージェントは、ここで指定された資格情報を使用してサブスクライバーに接続します。  
  
 詳細については、次を参照してください。 \\ [Replication Agent Security Model](security/replication-agent-security-model.md)します。  
  
## <a name="see-also"></a>参照  
 [[ディストリビューションの構成]](configure-distribution.md)   
 [Create a Pull Subscription](create-a-pull-subscription.md)   
 [Create a Push Subscription](create-a-push-subscription.md)   
 [ディストリビューターとパブリッシャーのプロパティの表示および変更](view-and-modify-distributor-and-publisher-properties.md)  
  
  
