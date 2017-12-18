---
title: "SSIS Scale Out Manager による Scale Out Worker の追加 | Microsoft Docs"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: scale-out
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ef11448d03bd188aaea425225312af9f681f530c
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="add-a-scale-out-worker-with-scale-out-manager"></a>Scale Out Manager による Scale Out Worker の追加

Integration Services Scale Out Manager を使用すると、既存の Scale Out 環境に Scale Out Worker を追加する作業が非常に簡単になります。 

次の手順では、Scale Out トポロジに、Scale Out Worker を追加します。

## <a name="1-install-scale-out-worker"></a>1.Scale Out Worker をインストールする
SQL Server のインストール ウィザードの **[機能の選択]** ページで、[統合サービス] と [スケール アウト ワーカー] を選択します。 
![Worker 機能の選択](media/feature-select-worker.PNG)

**Integration Services Scale Out Configuration - Worker Node\(Integration Services Scale Out 構成 - ワーカー ノード\)** ページで単純に 次へ をクリックしてここでの構成を省略し、**Scale Out Manager** を使用してインストール後に構成することができます。

インストール ウィザードを最後まで実行します。

## <a name="2-open-firewall-on-scale-out-master-computer"></a>2.Scale Out Master コンピューターでファイアウォールを開く
Scale Out Master コンピューターの Windows ファイアウォールを使用して、Scale Out Master のインストール時に指定したポート (既定では 8391) と SQL Server のポート (既定では 1433) を開きます。

## <a name="3-add-scale-out-worker-with-scale-out-manager"></a>3.Scale Out Manager による Scale Out Worker の追加
SQL Server Management Studio を管理者として実行し、Scale Out Master の SQL Server インスタンスに接続します。

オブジェクト エクスプローラーで **[SSISDB]** を右クリックし、**[スケール アウトの管理]** を選択します。 

![スケール アウトの管理](media/manage-scale-out.PNG)

表示された **[Scale Out Manager]** で、**[ワーカー マネージャー]** に切り替えます。 "+" ボタンをクリックし、[ワーカーの接続] ダイアログの指示に従います。 詳細については、「[Scale Out Master](integration-services-ssis-scale-out-manager.md)」を参照してください。
