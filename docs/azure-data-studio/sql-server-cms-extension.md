---
title: SQL Server の中央管理サーバーの拡張機能
titleSuffix: Azure Data Studio
description: インストールして Azure Data Studio の SQL Server の中央管理サーバーの拡張機能 (プレビュー) を使用
ms.custom: seodec18
ms.date: 06/06/2019
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: 1d10e3c4e9c1e1b2a6ce316902d4f70bbfac3740
ms.sourcegitcommit: 32dce314bb66c03043a93ccf6e972af455349377
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2019
ms.locfileid: "66748475"
---
# <a name="sql-server-central-management-servers-extension-preview"></a>SQL Server の中央管理サーバーの拡張機能 (プレビュー)
中央管理サーバーの拡張機能では、1 つまたは複数のグループに編成は、SQL Server のインスタンスのリストを格納することができます。 CMS のグループを使用して実行されるアクションは、サーバー グループ内のすべてのサーバー上で動作します。

このエクスペリエンスは、初期のプレビューは現在です。 問題の報告や機能要求[ここ](https://github.com/microsoft/azuredatastudio/issues)します。

![CMS の拡張機能](media/sql-server-cms-extension/cms-list.png)

## <a name="install-the-sql-server-central-management-servers-extension"></a>SQL Server の中央管理サーバーの拡張機能をインストールします。

1. 拡張機能マネージャーを開き、使用可能な拡張機能にアクセスするには、拡張機能 アイコンを選択するか、**ビュー**メニューの**拡張**を選択します。
2. 詳細を表示する使用可能な拡張機能を選択します。
1. (SQL Server サーバーの全体管理サーバー) が必要な拡張機能を選択し、**インストール**こと。

### <a name="how-do-i-start-central-management-servers"></a>中央管理サーバーを起動する方法はありますか
 中央管理サーバーは、(およびコマンド Ctrl + G)、接続アイコンをクリックして表示できます。 最初に、拡張機能をダウンロードする CMS ビューを最小化とでクリックして開くことができます**中央管理サーバー**

## <a name="next-steps"></a>次のステップ
中央管理サーバーでは、詳細については概念[詳しくはこちらを確認できます。](https://docs.microsoft.com/sql/ssms/register-servers/create-a-central-management-server-and-server-group)


