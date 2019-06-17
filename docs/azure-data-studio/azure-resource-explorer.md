---
title: Azure リソース エクスプ ローラーで Azure SQL のリソースを調べる
titleSuffix: Azure Data Studio
description: 調査および Azure SQL Server、Azure SQL Database、Azure Resource Explorer で Azure SQL マネージ インスタンスを管理する方法について説明します。
ms.custom: seodec18
author: yanancai
ms.author: yanacai
manager: jroth
ms.date: 09/24/2018
ms.topic: quickstart
ms.prod: sql
ms.technology: azure-data-studio
ms.openlocfilehash: 91e766fae5dca7a3d9e2dec56af17161d684e145
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66789220"
---
# <a name="explore-and-manage-azure-sql-resources-with-azure-resource-explorer"></a>調査、Azure リソース エクスプ ローラーで Azure SQL のリソースの管理

このドキュメントでは、調査し、Azure SQL Server、Azure SQL database、および Azure SQL マネージ インスタンスでの Azure リソース エクスプ ローラーを使用したリソースを管理する方法を説明します[!INCLUDE [Azure Data Studio](../includes/name-sos-short.md)]します。

>[!NOTE]
>Azure リソース エクスプ ローラーは、SQL Server 2019 年 10 月プレビューでサポートされます。 その後、を介してプレビュー拡張機能をインストールすることができます[拡張機能マネージャー](extensions.md)または**ファイル** > **VSIX パッケージからのパッケージのインストール**します。


## <a name="connect-to-azure"></a>Azure への接続します。

SQL プレビューのプラグインをインストールした後は、左側のメニュー バーで、Azure のアイコンが表示されます。 Azure リソース エクスプ ローラーを開く アイコンをクリックします。 Azure のアイコンが見つからない場合、左側のメニュー バーを右クリックし、選択**Azure リソース エクスプ ローラー**します。

### <a name="add-an-azure-account"></a>Azure アカウントを追加します。

Azure のアカウントに関連付けられた SQL リソースを表示するアカウントを最初に追加する必要があります[!INCLUDE [Azure Data Studio](../includes/name-sos-short.md)]します。

1. 開いている**リンクされたアカウント**ダイアログ ボックスの左下にある、または、アカウント管理アイコン**Azure にサインインしています.** Azure リソース エクスプ ローラーでリンクします。

    ![Azure へのサインイン](media/azure-resource-explorer/sign-in-to-azure.png)

2. **リンクされたアカウント**ダイアログ ボックスで、をクリックして**アカウントを追加**します。

    ![Azure アカウントを追加します。](media/azure-resource-explorer/add-an-azure-account.png)

3. クリックして**コピーして開く**認証用のブラウザーを開きます。

    ![ブラウザーで開いて認証ページ](media/azure-resource-explorer/open-authentication-in-browser.png)

4. 貼り付け、**ユーザー コード**web ページをクリックします**続行**を認証します。

    ![ブラウザーで認証します。](media/azure-resource-explorer/authenticate-in-browser.png)

5. [!INCLUDE [Azure Data Studio](../includes/name-sos-short.md)]が表示されます、ログに記録された Azure アカウントに**リンクされたアカウント**ダイアログ。

    ![Azure のアカウントのサインイン](media/azure-resource-explorer/signed-in-azure-account.png)

### <a name="add-more-azure-accounts"></a>その他の Azure アカウントを追加します。

複数の Azure アカウントではサポートされて[!INCLUDE [Azure Data Studio](../includes/name-sos-short.md)]します。 その他の Azure アカウントを追加するには、右上にあるボタンをクリックします。**リンクされたアカウント**ダイアログとで同じ手順に従って、その他の Azure アカウントを追加する Azure アカウント セクションを追加します。

![その他の Azure アカウントを追加します。](media/azure-resource-explorer/add-more-azure-account.png)

### <a name="remove-an-azure-account"></a>Azure アカウントを削除します。

既存を削除するには、Azure アカウントに記録されます。

1. 開いている**リンクされたアカウント**ダイアログの左下にあるアカウント管理アイコンを使用します。
2. をクリックして、 **X**それを削除する Azure アカウントの右側にあるボタンをクリックします。

    ![Azure アカウントを削除します。](media/azure-resource-explorer/remove-azure-account.png)

## <a name="filter-subscription"></a>サブスクリプションをフィルター処理します。

Azure アカウントにログインするとすべてのサブスクリプションに関連付けられている Azure リソース エクスプ ローラーで、Azure アカウントの表示。 各 Azure アカウントのサブスクリプションをフィルター処理することができます。

1. をクリックして、 **Select Subscription** Azure アカウントの右にあるボタンをクリックします。

   ![サブスクリプションをフィルター処理します。](media/azure-resource-explorer/filter-subscription.png)

2. [参照] をクリックするアカウントのサブスクリプションのチェック ボックスをオン**OK**します。

   ![サブスクリプションを選択します](media/azure-resource-explorer/select-subscription.png)

## <a name="explore-azure-sql-resources"></a>Azure SQL のリソースを調べる

Azure リソース エクスプ ローラーで、Azure SQL のリソースを移動するには、Azure アカウントとリソースの種類のグループを展開します。

Azure リソース エクスプ ローラーには現在 Azure SQL Server、Azure SQL Database および Azure SQL マネージ インスタンスがサポートしています。

## <a name="connect-to-azure-sql-resources"></a>Azure SQL のリソースへの接続します。

Azure リソース エクスプ ローラーでは、SQL サーバーとクエリと管理のためデータベースに接続するのに役立つクイック アクセスを提供します。 

1. ツリー ビューから接続するには、SQL リソースについて説明します。
2. リソースを右クリックし、選択**Connect**リソースの右側にある [接続] ボタンを検索することもできます。

   ![Azure SQL のリソースへの接続します。](media/azure-resource-explorer/connect-to-azure-sql-resource.png)

3. 開いている**接続**ダイアログ ボックスで、パスワードを入力し、をクリックして**Connect**します。

   ![SQL 接続ダイアログ](media/azure-resource-explorer/sql-connection-dialog.png)
4. **サーバー**接続が成功した後、このウィンドウは、自動的に新しい接続されている SQL サーバー/データベースが開きます。

## <a name="next-steps"></a>次のステップ

- [使用[!INCLUDE[Azure Data Studio](../includes/name-sos-short.md)]に接続して Azure SQL database のクエリ](quickstart-sql-database.md)
- [使用[!INCLUDE[Azure Data Studio](../includes/name-sos-short.md)]に接続して、Azure SQL Data Warehouse のデータの照会](quickstart-sql-dw.md)