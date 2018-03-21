---
title: "Management Studio でカスタム レポートを使用して R Services を監視する | Microsoft Docs"
ms.custom: 
ms.date: 10/09/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5933c72c-ba63-4966-b882-75719ef8428e
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 0a065ffeeaf5a88ac26cc1e628eaec5d39ba462a
ms.sourcegitcommit: 8e897b44a98943dce0f7129b1c7c0e695949cc3b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2018
---
# <a name="monitor-machine-learning-services-using-custom-reports-in-management-studio"></a>Management Studio でのカスタム レポートを使用して、マシン学習サービスの監視します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

機械学習に使用されるインスタンスを管理しやすいように、製品チームが SQL Server Management Studio に追加できるカスタム レポートのサンプルの数を指定します。 これらのレポートなどの詳細を表示できます。

- アクティブな R、Python またはセッション
- インスタンスの構成設定
- Machine learning のジョブの実行の統計
- R Services の拡張イベント
- 現在のインスタンスにインストールされている R または Python のパッケージ

この記事では、インストールして、マシン leaerning 専用に用意されているカスタム レポートを使用する方法について説明します。 

Management Studio でのレポートを一般的な概要については、次を参照してください。 [Management Studio でのカスタムのレポート](../../ssms/object/custom-reports-in-management-studio.md)です。

## <a name="how-to-install-the-reports"></a>レポートのインストール方法

レポートは SQL Server Reporting Services を使用するように設計されていますが、SQL Server Management Studio から直接使用することができます。インスタンスに Reporting Services がインストールされていない場合でも同じです。 

これらのレポートを使用する場合は、次のようにします。

* SQL Server 製品サンプルの GitHub リポジトリから RDL ファイルをダウンロードします。
* SQL Server Management Studio で使用されるカスタム レポート フォルダーにファイルを追加します。
* SQL Server Management Studio でレポートを開きます。


### <a name="step-1-download-the-reports"></a>手順 1. サンプルのダウンロード

1. 格納されている GitHub リポジトリを開く[SQL Server 製品サンプル](https://github.com/Microsoft/sql-server-samples)、およびサンプル レポートをダウンロードします。 

    + [SSMS のカスタム レポート](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/machine-learning-services/ssms-custom-reports)

    > [!NOTE]
    > レポートは、SQL Server 2017 Machiine 学習サービス、または SQL Server 2016 の R Services のいずれかで使用できます。

2. サンプルをダウンロードする場合、GitHub にログインし、サンプルのローカル分岐を作成することもできます。 

### <a name="step-2-copy-the-reports-to-management-studio"></a>手順 2. Management Studio へのレポートのコピー

3. SQL Server Management Studio で使用されるカスタム レポート フォルダーを見つけます。 既定では、カスタム レポートは次のフォルダーに格納されます。
    
   `C:\Users\user_name\Documents\SQL Server Management Studio\Custom Reports`

   ただし、別のフォルダーを指定したり、サブフォルダーを作成したりすることもできます。

4. *.RDL ファイルをカスタム レポート フォルダーにコピーします。


### <a name="step-3-run-the-reports"></a>手順 3. レポートの実行

5. Management Studio で、レポートを実行するインスタンスの **[データベース]** ノードを右クリックします。
6. **[レポート]**、 **[カスタム レポート]**の順にクリックします。
7. **[ファイルを開く]** ダイアログ ボックスで、カスタム レポート フォルダーを見つけます。
8. ダウンロードした RDL ファイルを選択し、 **[開く]**をクリックします。

> [!IMPORTANT]
> 高 DPI または 1080 p を超える解像度のディスプレイ デバイスを持つ一部のコンピューターや、一部のリモート デスクトップ セッションでは、これらのレポートは使用できません。 SSMS のレポート ビューアー コントロールには、レポートのクラッシュの原因となるバグがあります。

## <a name="report-list"></a>レポートの一覧

現在、GitHub の製品サンプル リポジトリには、次のレポートが含まれています。

+ **R Services - Active Sessions**

  このレポートを使用すると、SQL Server インスタンスと学習のジョブ実行中のコンピューターに現在接続しているユーザーを表示します。 
  
+ **R Services - Configuration**

  このレポートを使用すると、外部スクリプトの実行時と関連サービスの構成を表示します。 レポートでは、再起動が必要かどうかが示され、必要なネットワーク プロトコルが確認されます。 
  
  黙示的な認証は、コンピューティング コンテキストとして SQL Server で実行されている機械学習タスクに必要です。 その黙示的な認証が構成されていることを確認するには、このレポートは、グループ SQLRUserGroup データベース ログインが存在するかどうかを確認します。

 + **R Services - Configure Instance** 

   このレポートは、機械学習を構成できます。 前のレポート内で見つかった構成エラーを解決するには、このレポートを実行することもできます。
 
+ **R Services - Execution Statistics**

  このレポートを使用すると、マシン学習のジョブの実行の統計を表示します。 たとえば、実行された R スクリプトの合計数、並列実行の数、および最も頻繁に使用される RevoScaleR 関数を確認できます。 をクリックして**SQL スクリプトの表示**をこのレポートの背後にある完全な T-SQL コードを取得します。

  現在、レポートで監視されるのは、RevoScaleR パッケージ関数の統計のみです。

+ **R Services - Extended Events**

  このレポートを使用すると、外部スクリプトのランタイムに関連するタスクを監視するために使用可能な拡張イベントの一覧を表示します。 をクリックして**SQL スクリプトの表示**をこのレポートの背後にある完全な T-SQL コードを取得します。

+ **R Services - Packages**

  このレポートを使用すると、SQL Server インスタンスにインストールされている R または Python のパッケージの一覧を表示します。

+ **R Services - Resource Usage**

  このレポートを使用すると、外部スクリプトの実行で CPU、メモリ、および I/O リソースの消費状況を表示します。 外部のリソース プールのメモリ設定を表示することもできます。

## <a name="see-also"></a>参照

[サービスの監視](managing-and-monitoring-r-solutions.md)

[R Services の拡張イベント](extended-events-for-sql-server-r-services.md)
