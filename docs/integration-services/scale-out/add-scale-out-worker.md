---
title: "ワーカーをスケール アウト Manager での SSIS スケール追加 |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: b769236330941a107865a0b133961bce5bf6b85b
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="add-a-scale-out-worker-with-scale-out-manager"></a>スケール アウト マネージャーによるスケール アウト ワーカーの追加します。

Integration Services スケールのアウト マネージャーには、既存のスケール アウト環境をスケール アウト ワーカーを追加する複雑さが大幅にされますがします。 

次の手順によって、スケール アウト トポロジに、スケール アウト ワーカーを追加できます。

## <a name="1-install-scale-out-worker"></a>1.スケール アウト Worker をインストールします。
SQL Server インストール ウィザードの Integration Services とスケール アウト ワーカー、**機能の選択**ページ。 
![Worker 機能の選択](media/feature-select-worker.PNG)

**Integration Services スケール アウトの構成 - ワーカー ノード** ページをクリックするだけをここでの構成をスキップしを使用して、次へ**スケール アウト Manager**インストール後の構成を行う。

インストール ウィザードを完了します。

## <a name="2-open-firewall-on-scale-out-master-computer"></a>2.スケール アウト マスター コンピューター上のファイアウォールを開く
スケール アウト マスター インストール (既定では 8391) とポートの SQL Server (1433、既定では)、中に指定されたポートを開いてでは、Windows ファイアウォールを使用してスケール アウト マスター コンピューターにします。

## <a name="3-add-scale-out-worker-with-scale-out-manager"></a>3.スケール アウト Manager でのスケール アウト ワーカーを追加します。
SQL Server Management Studio を管理者として実行し、スケール アウト master データベースの SQL Server インスタンスに接続します。

右クリック**SSISDB**クリックし、オブジェクト エクスプ ローラーで**スケール アウトを管理しています.**. 

![スケール アウトの管理します。](media/manage-scale-out.PNG)

表示されたを**スケール アウト Manager**に切り替える**ワーカー マネージャー**です。 をクリックして「+」ボタンをクリックし、ワーカーの接続 ダイアログの指示に従います。 詳細については、「[スケール アウト Manager](integration-services-ssis-scale-out-manager.md)です。

