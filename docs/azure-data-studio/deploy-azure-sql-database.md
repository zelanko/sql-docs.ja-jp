---
title: Notebook を使用して Azure SQL Database をデプロイする
description: このチュートリアルでは、Azure SQL Database を作成する方法について説明します。
author: ninarn
ms.author: ninarn
ms.reviewer: alayu, maghan
ms.topic: tutorial
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.custom: ''
ms.date: 10/14/2020
ms.openlocfilehash: 88bb9fd980da21b20f0faf6f699147d26abe65b9
ms.sourcegitcommit: 76ab3b57718341c6057613c9bd38cf82fb17786e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/14/2020
ms.locfileid: "92060890"
---
# <a name="create-an-azure-sql-database-using-azure-data-studio"></a>Azure Data Studio を使用して Azure SQL Database を作成する

展開ウィザードとノートブックから、Azure Data Studio を使用して Azure SQL Database を作成できます。

## <a name="pre-requisites"></a>前提条件

 - [Azure Data Studio](download-azure-data-studio.md) がインストールされていること
 - アクティブな Azure アカウントとサブスクリプション。 アカウントがない場合は、[無料アカウントを作成](https://azure.microsoft.com/free/)してください。

## <a name="use-the-deployment-wizard"></a>展開ウィザードを使用

次の手順に従って、展開ウィザードを使用します。これにより、簡単な UI エクスペリエンスで必要な設定を行うことができます。

まず、展開ウィザードで Azure SQL Database を見つけて選択します。

 1. Azure Data Studio で、左側のナビゲーションにある [接続] ビューレットを選択します。
 2. [接続] パネルの上部にある **[...]** ボタンを選択し、 **[新しい展開...]** を選択します。
 3. 展開ウィザードで、 **[Azure SQL Database]** タイルを選択し、使用条件に同意するチェックボックスをオンにします。
 4. [リソースの種類] ドロップダウンで、作成するもの (データベース、データベース サーバー、エラスティック プールのいずれか) を選択します。 Azure に SQL Database がない場合は、まずデータベースを作成することをお勧めします。
 5. **[Azure portal で作成する]** を選択します。

次に、データベース、サーバー、またはプールを作成するためのすべての推奨設定を入力します。 これらの設定の構成方法に関するガイダンスについては、[Azure SQL のドキュメント](https://docs.microsoft.com/azure/azure-sql/database/single-database-create-quickstart?tabs=azure-portal)を参照してください。

## <a name="next-steps"></a>次のステップ

データベース、サーバー、またはプールを作成したら、Azure Data Studio でデータベースを[接続してクエリを実行](quickstart-sql-database.md)できます。
