---
title: "SSIS Scale Out Manager による Scale Out Worker の追加 | Microsoft Docs"
ms.description: This article describes how to add an SSIS Scale Out Worker to an existing Scale Out environment by using Scale Out Manager.
ms.custom: 
ms.date: 12/19/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: scale-out
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 
author: haoqian
ms.author: haoqian
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9fb097365def44d943a7fe6193a4a6498f4d9e37
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="add-a-scale-out-worker-with-scale-out-manager"></a>Scale Out Manager による Scale Out Worker の追加

Integration Services Scale Out Manager を使用すると、既存の Scale Out 環境に Scale Out Worker を追加するプロセスが簡単になります。 

次の手順に従って、Scale Out トポロジに Scale Out Worker を追加します。

## <a name="1-install-scale-out-worker"></a>1.Scale Out Worker をインストールする
SQL Server のインストール ウィザードの **[機能の選択]** ページで、[統合サービス] と [スケール アウト ワーカー] を選択します。 
![Worker 機能の選択](media/feature-select-worker.PNG)

**[Integration Services Scale Out の構成 - ワーカーノード]** ページで、**[次へ]** をクリックして、この時点での構成を省略し、**[Scale Out Manager]** を使用してインストール後に構成することができます。

インストール ウィザードを最後まで実行します。

## <a name="2-open-the-firewall-on-the-scale-out-master-computer"></a>2.Scale Out Master コンピューターでファイアウォールを開く
Scale Out Master コンピューターの Windows ファイアウォールで、Scale Out Master のインストール時に指定したポート (既定では 8391) と SQL Server のポート (既定では 1433) を開きます。

## <a name="3-add-a-scale-out-worker-with-scale-out-manager"></a>3.Scale Out Manager による Scale Out Worker の追加
SQL Server Management Studio を管理者として実行し、Scale Out Master の SQL Server インスタンスに接続します。

オブジェクト エクスプローラーで、**[SSISDB]** を右クリックして、**[スケール アウトの管理]** を選択します。 

![スケール アウトの管理](media/manage-scale-out.PNG)

**[Scale Out Manager]** ダイアログ ボックスで、**[ワーカー マネージャー]** に切り替えます。 **[+]** を選択し、**[ワーカーの接続]** ダイアログ ボックスの指示に従います。 

## <a name="next-steps"></a>次の手順
詳細については、[Scale Out Manager](integration-services-ssis-scale-out-manager.md) に関するページを参照してください。