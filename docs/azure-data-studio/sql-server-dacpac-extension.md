---
title: SQL Server dacpac の拡張機能
titleSuffix: Azure Data Studio
description: Azure Data Studio 用の SQL Server dacpac の拡張機能 (プレビュー) をインストールして使用する
ms.custom: seodec18
ms.date: 03/18/2019
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.openlocfilehash: e40e377310b33034b4abecdc5e58eab17d39695d
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2019
ms.locfileid: "67959192"
---
# <a name="sql-server-dacpac-extension-preview"></a>SQL Server dacpac の拡張機能 (プレビュー)

**データ層アプリケーション ウィザード**では、使いやすいエクスペリエンスによって、.dacpac ファイルの配置と抽出、および bacpac ファイルのインポートとエクスポートを行うことができます。

このエクスペリエンスは、現在、初期のプレビュー段階にあります。 問題と機能に関する要望を[こちら](https://github.com/microsoft/azuredatastudio/issues)にご報告ください。

![data-actions](media/sql-server-dacpac-extension/data-tier-application-actions.png)

 ### <a name="requirements"></a>必要条件
 * このウィザードを開始するには、SQL Server インスタンスへのアクティブな接続が必要です。

 ### <a name="how-do-i-start-the-data-tier-application-wizard"></a>データ層アプリケーション ウィザードを開始するにはどうすればよいですか?
 * このウィザードのメイン エントリ ポイントは、オブジェクト エクスプローラーでデータベースを右クリックし、**データ層アプリケーション ウィザード**をクリックします。
 * SQL Server インスタンスに接続されているユーザーの場合は、コマンド パレット (Ctrl + Shift + P) から、**データ層アプリケーション ウィザード**を検索することで、そのウィザードを起動することもできます。

 ### <a name="why-would-i-use-the-data-tier-application-wizard"></a>データ層アプリケーション ウィザードを使用する理由
 .dacpac ファイルを抽出および展開し、.bacpac ファイルをインポートおよびエクスポートする機能を Azure Data Studio に追加するために、このウィザードは作成されました。

## <a name="install-the-sql-server-dacpac-extension"></a>SQL Server dacpac の拡張機能をインストールする

1. 拡張機能マネージャーを開いて、使用可能な拡張機能にアクセスするには、拡張機能アイコンを選択するか、 **[表示]** メニューの **[拡張機能]** を選択します。
2. SQL Server dacpac の拡張機能を選択し、 **[インストール]** をクリックします。
1. **[再読み込み]** を選択して拡張機能を有効にします (拡張機能を初めてインストールするときにのみ必要です)。
2. ご利用のサーバーまたはデータベースを右クリックし、 **[管理]** を選択することで、ご利用の管理ダッシュボードに移動します。
3. インストールされた拡張機能が、ご利用の管理ダッシュボード上にタブとして表示されます。

## <a name="next-steps"></a>次の手順

dacpac の詳細については、[こちらのドキュメント](https://docs.microsoft.com/sql/relational-databases/data-tier-applications/data-tier-applications?view=sql-server-2017)を参照してください。