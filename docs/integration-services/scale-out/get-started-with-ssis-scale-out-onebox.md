---
title: "1 台のコンピューターに SSIS スケールの概要 |Microsoft ドキュメント"
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
ms.openlocfilehash: 7175c63be4c0e15e50f2020f75d283ac0e3dfdbf
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="get-started-with-integration-services-ssis-scale-out-on-a-single-computer"></a>Integration Services (SSIS) スケール アウト 1 台のコンピューターの概要します。
このセクションでは、既定の設定を含む 1 ボックス環境での Integration Services スケール アウトの設定のガイダンスを提供します。

## <a name="1-install-sql-server-features"></a>1.SQL Server 機能をインストールします。
SQL Server インストール ウィザードでデータベース エンジン サービス、Integration Services、スケール アウト マスターおよびスケール アウト ワーカーを選択、**機能の選択**ページ。

![機能選択 Onebox 1](media/feature-select-onebox1.PNG)

![機能選択 Onebox 2](media/feature-select-onebox2.PNG)

**サーバー構成** ページで、既定のサービス アカウントとスタートアップの種類を使用するには 次へ をクリックするだけです。

**データベース エンジンの構成**] ページで、["**混在モード**「を」**現在のユーザーの追加**"ボタンをクリックします。 

![エンジンの構成](media/engine-config.PNG)

1 つ、 **Integration Services スケール アウトの構成のマスター ノード**と**Integration Services スケール アウトの構成 - ワーカー ノード**ページを単にポートと証明書の既定の設定を適用するには [次へ] をクリックします。

SQL Server インストール ウィザードを完了します。

## <a name="2-install-sql-server-management-studio"></a>2.SQL Server Management Studio をインストールします。

[ダウンロード](../../ssms/download-sql-server-management-studio-ssms.md)SQL Server Management Studio し、インストールします。

## <a name="3-enable-scale-out"></a>3.スケール アウトを有効にします。
SSMS を開き、ローカルの Sql Server インスタンスに接続します。
右クリック**Integration Services カタログ**クリックし、オブジェクト エクスプ ローラーで**カタログの作成**です。

**カタログの作成**ダイアログ ボックスで、 **SSIS のスケール アウト マスターとしてこのサーバーを有効にする**が既定で選択します。 通常どおり、カタログを作成します。 

## <a name="4-enable-scale-out-worker"></a>4.スケール アウト ワーカーを有効にします。
SSMS を右クリックして**SSISDB**選択**スケール アウトを管理しています.**. 
![スケール アウトの管理します。](media/manage-scale-out.PNG)

統合サービス スケール アウト マネージャーが表示されます。 スケール アウトして管理できます。 詳細については、次を参照してください。 [Integration Services スケールのアウト マネージャー](integration-services-ssis-scale-out-manager.md)です。

スケール アウト ワーカーを有効にするに切り替えて**ワーカー マネージャー**を有効にワーカーを選択します。 最初は、ワーカーが無効です。 をクリックして**ワーカーを有効にする**有効にします。

## <a name="5-run-packages-in-scale-out"></a>5.Scale Out でのパッケージの実行
ここで、スケール アウトで SSIS パッケージを実行する準備ができたらです。 参照してください[Integration services (SSIS) パッケージの実行をスケール アウト](run-packages-in-integration-services-ssis-scale-out.md)です。


多くのスケール アウト ワーカーを追加するを参照してください。[スケール アウト マネージャーとワーカー スケール アウトの追加](add-scale-out-worker.md)です。
