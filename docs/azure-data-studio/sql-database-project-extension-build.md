---
title: プロジェクトをビルドして公開する
description: SQL Server データベース プロジェクトの拡張機能を使用してプロジェクトをビルドして公開する
ms.custom: seodec18
ms.date: 06/25/2020
ms.reviewer: drskwier, maghan, sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: dzsquared
ms.author: drskwier
ms.openlocfilehash: 4348f117b57c9b13a70f4a6db39ab6710eafd0ef
ms.sourcegitcommit: b860fe41b873977649dca8c1fd5619f294c37a58
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2020
ms.locfileid: "85519191"
---
# <a name="build-and-publish-a-project"></a>プロジェクトをビルドして公開する

Azure Data Studio の SQL データベース プロジェクトの拡張機能のビルド プロセスでは、Windows、macOS、Linux 環境で *dacpac* を作成できます。 プロジェクトは、公開プロセスを使用してローカルまたはクラウド環境にデプロイできます。

## <a name="prerequisites"></a>前提条件
- [Azure Data Studio の SQL データベース プロジェクトの拡張機能](sql-database-project-extension.md)のインストールと構成。


## <a name="build-a-database-project"></a>データベース プロジェクトをビルドする

 **[エクスプローラー]** の下の **[プロジェクト]** viewlet で、 *.sqlproj* ルート ノードを右クリックし、 **[ビルド]** を選択します。

 出力ウィンドウに、ビルド プロセスからの出力が自動的に表示されます。  ビルドが成功すると、次のメッセージが表示されます。 

 ``` ... exited with code: 0 ```


## <a name="publish-a-database-project"></a>データベース プロジェクトを公開する

ビルド プロセスによってプロジェクトが正常にコンパイルされたら、データベースを SQL Server インスタンスに公開できます。 データベース プロジェクトを公開するには、 **[エクスプローラー]** の下の **[プロジェクト]** viewlet で、 *.sqlproj* ルート ノードを右クリックし、 **[公開]** を選択します。

表示される **[データベースの公開]** ダイアログで、サーバー接続と作成するデータベース名を指定します。

## <a name="next-steps"></a>次のステップ

- [Azure Data Studio の SQL データベース プロジェクトの拡張機能](sql-database-project-extension.md)
- [データ層アプリケーション](../relational-databases/data-tier-applications/data-tier-applications.md)


