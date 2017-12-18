---
title: "1 台のコンピューターでの SSIS Scale Out の概要 | Microsoft Docs"
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
ms.openlocfilehash: 8514cd548b003a39bf198b83b6b80d775a55384b
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="get-started-with-integration-services-ssis-scale-out-on-a-single-computer"></a>1 台のコンピューターでの Integration Services (SSIS) Scale Out の概要
このセクションでは、コンピューターが 1 台の環境で Integration Services Scale Out を設定する方法を紹介します。既定の設定を利用します。

## <a name="1-install-sql-server-features"></a>1.SQL Server 機能のインストール
SQL Server のインストール ウィザードの **[機能の選択]** ページで、[データベース エンジン サービス]、[Integration Services]、[スケール アウト マスター]、[スケール アウト ワーカー] を選択します。

![機能の選択 Onebox 1](media/feature-select-onebox1.PNG)

![機能の選択 Onebox 2](media/feature-select-onebox2.PNG)

**[サーバー構成]** ページで、[次へ] をクリックし、既定のサービス アカウントとスタートアップの種類を使用します。

**[データベース エンジンの構成]** ページで、**[混合モード]** を選択し、**[現在のユーザーの追加]** ボタンをクリックします。 

![エンジンの構成](media/engine-config.PNG)

**[Integration Services Scale Out の構成 - マスター ノード]** ページと **[Integration Services Scale Out の構成 - ワーカーノード]** ページで、[次へ] をクリックし、ポートと証明書に既定の設定を適用します。

SQL Server のインストール ウィザードを完了します。

## <a name="2-install-sql-server-management-studio"></a>2.SQL Server Management Studio のインストール

SQL Server Management Studio を[ダウンロード](../../ssms/download-sql-server-management-studio-ssms.md)し、それをインストールします。

## <a name="3-enable-scale-out"></a>3.スケール アウトの有効化
SSMS を開き、ローカル Sql Server インスタンスに接続します。
オブジェクト エクスプローラーで **[Integration Services カタログ]** を右クリックし、**[カタログの作成]** を選択します。

**[カタログの作成]** ダイアログで、**[SSIS スケール アウト マスターとしてこのサーバーを有効にする]** が既定で選択されています。 通常どおりカタログを作成します。 

## <a name="4-enable-scale-out-worker"></a>4.スケール アウト ワーカーの有効化
SSMS で **[SSISDB]** を右クリックし、**[スケール アウトの管理...]** を選択します。![[スケール アウトの管理]](media/manage-scale-out.PNG)

Integration Services Scale Out Manager マネージャーが表示されます。 このマネージャーでスケール アウトを管理できます。 詳細については、「[Integration Services Scale Out Manager](integration-services-ssis-scale-out-manager.md)」 (Integration Services スケール アウト マネージャー) を参照してください。

スケール アウト ワーカーを有効にするには、**[ワーカー マネージャー]** に切り替え、有効にするワーカーを選択します。 ワーカーは既定では無効になっています。 **[ワーカーの有効化]** をクリックして有効にします。

## <a name="5-run-packages-in-scale-out"></a>5.Scale Out でのパッケージの実行
これで、スケール アウトで SSIS パッケージを実行できます。「[Run Packages in Integration Services (SSIS) Scale Out](run-packages-in-integration-services-ssis-scale-out.md)」 (Integration Services (SSIS) スケール アウトでパッケージを実行する) を参照してください。


スケール アウト ワーカーを追加するには、「[Add a Scale Out Worker with Scale Out Manager](add-scale-out-worker.md)」 (スケール アウト マネージャーでスケール アウト ワーカーを追加する) を参照してください。
