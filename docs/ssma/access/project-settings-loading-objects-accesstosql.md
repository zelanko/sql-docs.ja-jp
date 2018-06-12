---
title: プロジェクトの設定 (オブジェクトの読み込み) (AccessToSQL) |Microsoft ドキュメント
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 9ec1c1e8-a3e1-4e81-bf49-631f87daa209
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: dc0517af077d0dcb6d7914eb7decffdc0ee7a198
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34774128"
---
# <a name="project-settings-loading-objects-accesstosql"></a>プロジェクトの設定 (オブジェクトの読み込み) (AccessToSQL)
オブジェクトの読み込みのプロジェクト設定では、SQL Server データベース オブジェクトとデータベース オブジェクトへのアクセスを同期する方法を構成できます。  
  
既定の操作は、Access データベースからオブジェクトを更新する場合と、SQL Server データベースとオブジェクトを同期するために、既定の設定を指定します。 詳細については、次を参照してください[データベースから更新&#40;AccessToSQL。&#41;](../../ssma/access/refresh-from-database-accesstosql.md)  
  
同じ設定を含む 2 つの異なる同期ページにアクセスできます。  
  
-   今後のすべての SSMA プロジェクトの設定を指定する、**ツール** メニューのをクリックして**DefaultProject 設定**、クリックして**オブジェクトの読み込み**左側のウィンドウの下部にあります。  
  
-   現在のプロジェクトの設定を指定する、**ツール** メニューのをクリックして**プロジェクト設定**、クリックして**オブジェクトの読み込み**左側のウィンドウの下部にあります。  
  
## <a name="options"></a>および  
  
##### <a name="misc"></a>その他  
  
##### <a name="attempts"></a>試行回数  
オブジェクトが SQL Server に読み込むためのパスの数に関する情報を示します。 SQL Server へのオブジェクトの読み込みは通常、複数のパスで実行されます。 外部キーなど、最初のパスの読み込みに失敗したオブジェクトを次のパスで読み込むことが正常にします。  
  
既定値は 2 です。  
  
## <a name="synchronization-for-sql-server"></a>SQL Server の同期  
  
##### <a name="default-action-on-local-and-remote-object-change"></a>ローカルとリモート オブジェクトの変更の既定の操作  
SSMA では、データベース サーバーで、オブジェクトの定義が変更されたときに、[同期] ダイアログ ボックスで、既定の設定を指定します。  
  
-   選択した場合**データベースから更新**SSMA は、条件が満たされたときに、メタデータのデータベース定義が読み込むされます。  
  
-   選択した場合**データベースへの書き込み**SSMA は、条件が満たされたときに、SSMA メタデータの内容に基づき、データベース内のオブジェクトは更新します。  
  
-   選択した場合**Skip**SSMA では、更新動作は実行されません。  
  
##### <a name="default-action-on-local-object-change"></a>ローカル オブジェクトの変更の既定の操作  
SSMA でオブジェクトが変更されたときに、[同期] ダイアログ ボックスで、既定の設定を指定します。  
  
-   選択した場合**データベースから更新**SSMA は、条件が満たされたときに、メタデータのデータベース定義が読み込むされます。  
  
-   選択した場合**データベースへの書き込み**SSMA は、条件が満たされたときに、SSMA メタデータの内容に基づき、データベース内のオブジェクトは更新します。  
  
-   選択した場合**Skip**SSMA では、更新動作は実行されません。  
  
##### <a name="default-action-on-remote-object-change"></a>リモート オブジェクトの変更の既定の操作  
データベース サーバーで、オブジェクトが変更の同期 ダイアログ ボックスで、既定の設定を指定します。  
  
-   選択した場合**データベースから更新**SSMA は、条件が満たされたときに、メタデータのデータベース定義が読み込むされます。  
  
-   選択した場合**データベースへの書き込み**SSMA は、条件が満たされたときに、SSMA メタデータの内容に基づき、データベース内のオブジェクトは更新します。  
  
-   選択した場合**Skip**SSMA では、更新動作は実行されません。  
  
##### <a name="default-action-when-local-object-metadata-is-missing"></a>ローカル オブジェクトのメタデータが見つからない場合に、既定のアクション  
ローカルのメタデータが見つからない場合に、[同期] ダイアログ ボックスで、既定の設定を指定します。  
  
-   選択した場合**データベースから更新**SSMA では、条件が満たされたときにデータベース オプションから、更新を選択します。  
  
-   選択した場合**データベースへの書き込み**SSMA は、条件が満たされたときに、データベースからのオブジェクトが削除されます。  
  
-   選択した場合**Skip**SSMA では、更新動作は実行されません。  
  
