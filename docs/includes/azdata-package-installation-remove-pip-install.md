---
author: MikeRayMSFT
ms.prod: sql
ms.topic: include
ms.date: 01/07/2020
ms.author: mikeray
ms.openlocfilehash: 401d214495cd8df8ec3401c0b18db8ebe8773226
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "75721535"
---
### <a name="pythonpip-installation"></a>Python と Pip のインストール

yum、apt、または zypper を使用して Linux に `azdata` をインストールするか、Homebrew インストール パッケージ マネージャーを使用して macOS にインストールすることができます。 これらのパッケージ マネージャーが使用可能になる前は、インストールに Python と pip が必要でした。

>[!IMPORTANT]
>次に進む前に、グローバル システム Python にインストールされた `azdata` のすべてのインストールを削除する必要があります。 新しいインストーラーまたはネイティブ パッケージによってパスに `azdata` が追加されます。どれが最初かを判別することはできません。
グローバル システム Python に既存の `azdata` をインストールした場合は、次に進む前に削除します。

現在のインストールを表示するには、次のコマンドを実行します。

```bash
$ pip list --format columns
```

pip によって `azdata` がインストールされている場合、パッケージとバージョンが返されます。 次に例を示します。

```
 Package             Version
------------------- ----------
azdata-cli          15.0.X
azdata-cli-app      15.0.X
azdata-cli-cluster  15.0.X
azdata-cli-core     15.0.X
azdata-cli-hdfs     15.0.X
azdata-cli-notebook 15.0.X
azdata-cli-profile  15.0.X
azdata-cli-spark    15.0.X
azdata-cli-sql      15.0.X
```

次の例では、`azdata` の pip のインストールを削除します。

```bash
$ pip freeze | grep azdata-* | xargs pip uninstall -y
```

pip を使用してインストールされた `azdata` のインストールを削除したことを確認したら、インストールを続行します。