---
title: SQL Server Integration Services Scale Out Manager | Microsoft Docs
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
ms.openlocfilehash: 84fe58d4dc7894728c43cb19d17d3444b5b84820
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="integration-services-scale-out-manager"></a>Integration Services Scale Out Manager

Scale Out Manager は、1 つの場所にある完全な SSIS Scale Out トポロジを管理できる管理ツールです。 複数のコンピューターでの操作と TSQL コマンドを処理する負担がなくなります。 

Scale Out Manager をトリガーする 2 つの方法があります。

## <a name="1-open-scale-out-manager-from-sql-server-management-studio"></a>1.SQL Server Management Studio から Scale Out Manager を開く
SQL Server Management Studio を開き、Scale Out Master の SQL Server インスタンスに接続します。

オブジェクト エクスプローラーで **[SSISDB]** を右クリックし、**[スケール アウトの管理]** を選択します。![スケール アウトの管理](media/manage-scale-out.PNG)

> [!NOTE]
> 管理者特権を必要とする "Scale Out Worker の追加" などの一部の Scale Out 管理操作と同じように、管理者として SQL Server Management Studio を実行することをお勧めします。


## <a name="2-open-scale-out-manager-by-runing-ismanagerexe-directly"></a>2.ISManager.exe を直接実行して、Scale Out Manager を開く

ISManager.exe は、%SystemDrive%\Program Files (x86)\Microsoft SQL Server\140\DTS\Binn\Management の下にあります。 **ISManager.exe** を右クリックし、[管理者として実行] を選択します。 

ISManager.exe が開いたら、Scale Out を管理する前に、Scale Out Master の SQL Server 名を入力して接続する必要があります。

![ポータルの接続](media/portal-connect.PNG)

Scale Out Manager は、次のようなさまざまな機能を提供します。 

## <a name="enable-scale-out"></a>Scale Out を有効にする
SQL Server に接続した後で、Scale Out が有効になっていない場合は、[有効] ボタンをクリックして有効にできます。

![ポータルで Scale Out を有効にする](media/portal-enable-scale-out.PNG) 
## <a name="view-scale-out-master-status"></a>Scale Out Master の状態を表示する
Scale Out Master の状態は、**[ダッシュボード]** ページに表示されます。

![ポータルのダッシュボード](media/portal-dashboard.PNG)
## <a name="view-scale-out-worker-status"></a>Scale Out Worker の状態を表示する
Scale Out Worker の状態は、**[ワーカー マネージャー]** ページに表示されます。 各ワーカーをクリックすると、個別の状態を表示できます。

![ポータルのワーカー マネージャー](media/portal-worker-manager.PNG)

## <a name="add-scale-out-worker"></a>Scale Out Worker を追加する
Scale Out Worker を追加するには、Scale Out Worker リストの下部にある [+] ボタンをクリックします。 

追加する Scale Out Worker のコンピューター名を入力し、[検証] をクリックします。 Scale Out Manager によって、現在のユーザーが Scale Out Master と Scale Out Worker のコンピューター上の証明書ストアへのアクセス権を持っているかどうかがチェックされます。

![ワーカーの接続](media/connect-worker.PNG)

検証に合格すると、Scale Out Manager は、ワーカー構成ファイルを読み取り、ワーカーの証明書のサムプリントの取得を試みます。 詳細については、「[Integration Services (SSIS) Scale Out Worker](integration-services-ssis-scale-out-worker.md)」を参照してください。 ワーカー構成ファイルを読み取れない場合、ワーカー証明書を提供するための 2 つの代替方法があります。 

ワーカー証明書のサムプリントを直接入力するか、 

![ワーカー証明書 1](media/portal-cert1.PNG)

証明書ファイルを提供します。 

![ワーカー証明書 2](media/portal-cert2.PNG)

すべての情報を収集すると、Scale Out Manager が実行されるアクションを提供します。 通常、これには証明書のインストール、ワーカー構成ファイルの更新、およびワーカー サービスの再起動が含まれます。 

![ポータルの追加の確認 1](media/portal-add-confirm1.PNG)

ワーカー証明書にアクセスできない場合は、ユーザーが証明書を手動で更新してから、ワーカー サービスを再起動する必要があります。

![ポータルの追加の確認 2](media/portal-add-confirm2.PNG)

確認のチェック ボックスをクリックし、Scale Out Worker の追加を開始します。

## <a name="delete-scale-out-worker"></a>Scale Out Worker を削除する
Scale Out Worker を削除するには、Scale Out Worker を選択し、Scale Out Worker リストの下部にある [-] ボタンをクリックします。


## <a name="enabledisable-scale-out"></a>Scale Out を有効/無効にする
Scale Out Worker を有効または無効にするには、[ワーカーの有効化] または [ワーカーの無効化] をクリックします。 Scale Out Manager のワーカーの状態は、ワーカーがオフラインでなければ、都度変化します。

## <a name="edit-scale-out-worker-description"></a>Scale Out Worker の説明を編集する
Scale Out Worker の説明を編集するには、Scale Out Worker を選択し、[編集] ボタンをクリックします。 編集が完了したら、[保存] ボタンをクリックします。

![ポータルのワーカーの保存](media/portal-save-worker.PNG)

