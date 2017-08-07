---
title: "SQL Server Integration Services のスケール アウト Manager |Microsoft ドキュメント"
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
ms.openlocfilehash: 96748296acd1b2f5ba98558335fece9637eadb87
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="integration-services-scale-out-manager"></a>Integration Services のスケール アウト マネージャー

スケール アウト マネージャーは、1 つの場所にある完全 SSIS スケール アウト トポロジを管理できる管理ツールです。 複数のコンピューターでの運用と TSQL コマンドを処理する負担が削除されます。 

スケール アウト マネージャーをトリガーする 2 つの方法ができます。

## <a name="1-open-scale-out-manager-from-sql-server-management-studio"></a>1.SQL Server Management Studio からのスケール アウト マネージャーを開く
SQL Server Management Studio を開き、スケール アウト master データベースの SQL Server インスタンスに接続します。

右クリック**SSISDB**クリックし、オブジェクト エクスプ ローラーで**スケール アウトを管理しています.**. 
![スケール アウトの管理します。](media/manage-scale-out.PNG)

> [!NOTE]
> 管理者として「スケール アウト ワーカーの追加」などのスケール アウトの管理操作の一部として SQL Server Management Studio を実行に必要に管理者特権をお勧めします。


## <a name="2-open-scale-out-manager-by-runing-ismanagerexe-directly"></a>2.直接実行 ISManager.exe してスケール アウト マネージャーを開く

%SystemDrive%\Program Files (x86) \Microsoft SQL Server\140\DTS\Binn\Management ISManager.exe を検索します。 右クリックして**ISManager.exe** "管理者として実行 を選択します。 

開いたら、スケール アウト master データベースの Sql Server 名を入力し、スケール アウトを管理する前に接続する必要があります。

![ポータルを接続します。](media/portal-connect.PNG)

スケール アウト マネージャーは、次に示すさまざまな機能を提供します。 

## <a name="enable-scale-out"></a>スケール アウトを有効にします。
SQL Server に接続すると、スケール アウトが有効でない場合と、次の有効にする [有効] にボタンがクリックできます。

![ポータルを有効にするスケール アウト](media/portal-enable-scale-out.PNG) 
## <a name="view-scale-out-master-status"></a>スケール アウト マスターの状態の表示
スケール アウト master データベースの状態を示す、**ダッシュ ボード**ページ。

![ポータルのダッシュ ボード](media/portal-dashboard.PNG)
## <a name="view-scale-out-worker-status"></a>スケール アウト ワーカーの状態の表示
スケール アウト ワーカーの状態を示す、**ワーカー マネージャー**ページ。 個々 の状態を表示するには、各ワーカーをクリックすることができます。

![ポータル ワーカー マネージャー](media/portal-worker-manager.PNG)

## <a name="add-scale-out-worker"></a>スケール アウト ワーカーを追加します。
スケール アウト ワーカーを追加するには、スケール アウト ワーカー一覧の下部にある「+」ボタンをクリックします。 

スケール アウト作業者の追加「確認」 をクリックするマシン名を入力します。 スケール アウト マネージャーには、現在のユーザーをスケール アウト マスターとスケール アウト ワーカーのコンピューターに証明書ストアへのアクセスを持つかどうかは確認します。

![ワーカーを接続します。](media/connect-worker.PNG)

検証に合格した場合はスケール アウト マネージャーは、ワーカーの構成ファイルを読み取るし、ワーカーの証明書のサムプリントの取得を試みます。 詳細については、次を参照してください。[スケール アウト ワーカー](integration-services-ssis-scale-out-worker.md)です。 ワーカーの構成ファイルを読み込むことがないの場合は、ワーカーの証明書を提供するための 2 つの代替方法。 

ワーカーの証明書の拇印を直接入力することができますか 

![ワーカーの証明書 1](media/portal-cert1.PNG)

または、証明書ファイルを提供します。 

![ワーカーの証明書 2](media/portal-cert2.PNG)

すべての情報を収集した後には、スケール アウト マネージャーを実行するアクションを提供します。 Tyically、証明書のインストール、ワーカーの構成ファイルの更新プログラムおよびサービスを再起動するワーカーが含まれます。 

![ポータルが 1 の確認を追加](media/portal-add-confirm1.PNG)

ワーカーの証明書がアクセス可能でない場合は、自分で手動で更新してから、ワーカー サービスを再起動する必要があります。

![ポータルの確認 2 の追加](media/portal-add-confirm2.PNG)

確認のチェック ボックスをクリックし、スケール アウト ワーカーの追加を開始します。

## <a name="delete-scale-out-worker"></a>スケール アウト ワーカーを削除します。
スケール アウト ワーカーを削除するには、スケール アウト ワーカーを選択し、クリックして、"-"のスケール アウト ワーカー一覧の下部にあるボタンをクリックします。


## <a name="enabledisable-scale-out"></a>スケール アウトを有効/無効にします。
有効または無効にスケール アウト ワーカー、スケール アウト ワーカーを選択し、「ワーカーを有効にする」または「無効にするワーカー」ボタンをクリックします。 スケール アウト マネージャーのワーカーの状態は、作業者がオフラインでない場合、それに応じて変更されます。

## <a name="edit-scale-out-worker-description"></a>スケール アウト ワーカーの説明を編集します。
スケール アウト ワーカーの説明を編集するには、スケール アウト ワーカーを選択し、"Edit"ボタンをクリックします。 編集が完了したら、[保存] ボタンをクリックします。

![ワーカー保存ポータル](media/portal-save-worker.PNG)


