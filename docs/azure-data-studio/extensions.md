---
title: 拡張機能の追加
description: 拡張機能マーケットプレースから Azure Data Studio に拡張機能を追加する
ms.prod: azure-data-studio
ms.technology: ''
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: alayu, maghan, sstein
ms.custom: seodec18
ms.date: 10/03/2019
ms.openlocfilehash: 7e74d0dd7b904cba5b332eb20163c96237ac6d6e
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85774618"
---
# <a name="extend-the-functionality-of-azure-data-studio"></a>Azure Data Studio の機能の拡張

Azure Data Studio の拡張機能により、Azure Data Studio の基本インストールにさらに機能を追加する簡単な方法が提供されます。

拡張機能は、Azure Data Studio チーム (Microsoft) と、サード パーティのコミュニティ (お客様) によって提供されます。 拡張機能の作成の詳細については、[拡張機能の作成](extension-authoring.md)に関するページを参照してください。

## <a name="add-azure-data-studio-extensions"></a>Azure Data Studio の拡張機能を追加する

1. 使用可能な拡張機能にアクセスするには、[拡張機能] アイコンを選択するか、 **[表示]** メニューの **[拡張機能]** を選択します。

    ![拡張機能マネージャーのアイコン](media/extensions/extension-manager-icon.png)

    `Ctrl+Shift+X` キー (Windows/Linux) または `Command+Shift+X` キー (Mac) を押すことによって、拡張機能マネージャーに簡単アクセスすることもできます。

2. 使用可能な拡張機能を選択すると、その詳細が表示されます。
    ![拡張機能の詳細](media/extensions/extension-details.png)

3. 必要な拡張機能を選択して**インストール**します。

4. インストール後、 **[再度読み込む]** をクリックすると、Azure Data Studio で拡張機能が有効になります (初めて拡張機能をインストールするときにのみ必須)。

Azure Data Studio での拡張機能マネージャーへのアクセスに問題がある場合は、[GitHub Wiki](https://github.com/microsoft/azuredatastudio/wiki/List-of-Extensions) で必要な拡張機能をダウンロードできます。


## <a name="access-installed-azure-data-studio-extensions"></a>インストールした Azure Data Studio の拡張機能にアクセスする

Azure Data Studio のエクスペリエンスの向上は拡張機能ごとに異なります。 そのため、拡張機能のエントリ ポイントはさまざまです。 インストール後、その機能にアクセスする方法については、インストールした拡張機能の個別ドキュメントを参照してください。
