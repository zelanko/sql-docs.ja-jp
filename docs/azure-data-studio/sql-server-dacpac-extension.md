---
title: SQL Server の dacpac の拡張機能
titleSuffix: Azure Data Studio
description: インストールして Azure Data Studio の SQL Server の dacpac 拡張機能 (プレビュー) を使用します。
ms.custom: seodec18
ms.date: 03/18/2019
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: jroth
ms.openlocfilehash: 70b06749d1cbecc2127c70fee28b60f49583d5ce
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66797984"
---
# <a name="sql-server-dacpac-extension-preview"></a>SQL Server dacpac の拡張機能 (プレビュー)

**データ層アプリケーションのウィザード**デプロイ、.dacpac ファイルを抽出し、インポートし、.bacpac ファイルをエクスポートする使いやすいエクスペリエンスが提供されます。

このエクスペリエンスは、初期のプレビューは現在です。 問題の報告や機能の要求をください[ここです。](https://github.com/microsoft/azuredatastudio/issues)

![データ アクション](media/sql-server-dacpac-extension/data-tier-application-actions.png)

 ### <a name="requirements"></a>必要条件
 * このウィザードでは、アクティブな接続を開始する SQL Server インスタンスが必要です。

 ### <a name="how-do-i-start-the-data-tier-application-wizard"></a>データ層アプリケーションのウィザードを起動する方法はありますか
 * オブジェクト エクスプ ローラーでデータベースを右クリックし、をクリックして、ウィザードのメイン エントリ ポイントは、**データ層アプリケーションのウィザード**します。
 * ユーザーが SQL Server インスタンスに接続されている場合、ユーザーもウィザードを起動できますコマンド パレット (Ctrl + Shift + P) を検索して**データ層アプリケーションのウィザード。**

 ### <a name="why-would-i-use-the-data-tier-application-wizard"></a>データ層アプリケーションのウィザードを使用する理由でしょうか。
 このウィザードは、抽出と .dacpac ファイルを配置およびインポートでは、Azure Data Studio .bacpac ファイルをエクスポートする機能を追加作成されました。

## <a name="install-the-sql-server-dacpac-extension"></a>Dacpac の SQL Server 拡張機能をインストールします。

1. 拡張機能マネージャーを開き、使用可能な拡張機能にアクセスするには、拡張機能 アイコンを選択するか、**ビュー**メニューの**拡張**を選択します。
2. Dacpac の SQL Server 拡張機能を選択し、クリックして**インストール**します。
1. **再読み込み**を選択して拡張機能を有効にします(初めて拡張機能をインストールするときのみ必要です)。
2. サーバーまたはデータベースを右クリックし、**管理**を選択して管理ダッシュ ボードに移動します。
3. インストールされた拡張機能は、管理ダッシュ ボードのタブとして表示されます。

## <a name="next-steps"></a>次のステップ

詳細については、dacpac の[ドキュメントを確認します。](https://docs.microsoft.com/sql/relational-databases/data-tier-applications/data-tier-applications?view=sql-server-2017)