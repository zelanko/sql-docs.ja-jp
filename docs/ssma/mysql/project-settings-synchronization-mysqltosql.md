---
title: プロジェクトの設定 (同期) (MySQLToSQL) |Microsoft ドキュメント
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
ms.assetid: 42061ff7-e6e7-497b-a0d9-440b9cf5986c
caps.latest.revision: 3
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 16ddb4db77140eb57c893d68d954b538db2f418a
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34776198"
---
# <a name="project-settings-synchronization-mysqltosql"></a>プロジェクトの設定 (同期) (MySQLToSQL)
同期**プロジェクト設定**SQL Server データベース オブジェクトと MySQL のデータベース オブジェクトを同期する方法を構成できます。  
  
既定の操作は、MySQL データベースからオブジェクトを更新する場合と、SQL Server データベースとオブジェクトを同期するために、既定の設定を指定します。 詳細については、次を参照してください[データベースから更新&#40;MySQLToSQL。&#41;](../../ssma/mysql/refresh-from-database-mysqltosql.md)  
  
同じ設定を含む 2 つの異なる同期ページにアクセスできます。  
  
-   今後のすべての SSMA プロジェクトの設定を指定する、**ツール** メニューのをクリックして**DefaultProject 設定**、クリックして**同期**左側のウィンドウの下部にあります。  
  
-   現在のプロジェクトの設定を指定する、**ツール** メニューのをクリックして**プロジェクト設定**、クリックして**同期**左側のウィンドウの下部にあります。  
  
## <a name="options"></a>および  
  
##### <a name="misc"></a>その他  
  
##### <a name="attempts"></a>試行回数  
オブジェクトが SQL Server に読み込むためのパスの数に関する情報を示します。 SQL Server へのオブジェクトの読み込みは通常、複数のパスで実行されます。 外部キーなど、最初のパスの読み込みに失敗したオブジェクトを次のパスで読み込むことが正常にします。  
  
既定値は 2 です。  
  
## <a name="synchronization-for-mysql"></a>MySQL の同期  
  
##### <a name="action-on-local-and-remote-object-change"></a>ローカルおよびリモート オブジェクトの変更のアクション  
SSMA では、データベース サーバーで、オブジェクトの定義が変更されたときに、[同期] ダイアログ ボックスで、既定の設定を指定します。  
  
-   データベースから更新を選択した場合、メタデータに、条件が満たされたときに SSMA にデータベースの定義が読み込まれます。  
  
-   スキップを選択すると、SSMA は更新アクションを実行できません。  
  
##### <a name="action-on-local-object-change"></a>ローカル オブジェクトの変更のアクション  
SSMA でオブジェクトが変更されたときに、[同期] ダイアログ ボックスで、既定の設定を指定します。  
  
-   選択した場合**データベースから更新**SSMA は、条件が満たされたときに、メタデータのデータベース定義が読み込むされます。  
  
-   選択した場合**Skip**SSMA では、更新動作は実行されません。  
  
##### <a name="action-on-remote-object-change"></a>リモート オブジェクトの変更のアクション  
データベース サーバーで、オブジェクトが変更の同期 ダイアログ ボックスで、既定の設定を指定します。  
  
-   選択した場合**データベースから更新**SSMA は、条件が満たされたときに、メタデータのデータベース定義が読み込むされます。  
  
-   選択した場合**Skip**SSMA では、更新動作は実行されません。  
  
##### <a name="action-when-local-object-metadata-is-missing"></a>ローカル オブジェクトのメタデータが不足している場合の動作  
ローカルのメタデータが見つからない場合に、[同期] ダイアログ ボックスで、既定の設定を指定します。  
  
-   選択した場合**データベースから更新**、SSMA SSMA は、条件が満たされたときに、メタデータのデータベース定義が読み込むされます。  
  
-   選択した場合**Skip**SSMA は、すべての更新操作を実行していません。  
  
## <a name="synchronization-for-sql-server"></a>SQL Server の同期  
  
##### <a name="action-on-local-and-remote-object-change"></a>ローカルとリモート オブジェクトの変更のアクション  
SSMA では、データベース サーバーで、オブジェクトの定義が変更されたときに、[同期] ダイアログ ボックスで、既定の設定を指定します。  
  
-   選択した場合**データベースから更新**SSMA は、条件が満たされたときに、メタデータのデータベース定義が読み込むされます。  
  
-   選択した場合**データベースへの書き込み**SSMA は、条件が満たされたときに、SSMA メタデータの内容に基づき、データベース内のオブジェクトは更新します。  
  
-   選択した場合**Skip**SSMA では、更新動作は実行されません。  
  
##### <a name="action-on-local-object-change"></a>ローカル オブジェクトの変更のアクション  
SSMA でオブジェクトが変更されたときに、[同期] ダイアログ ボックスで、既定の設定を指定します。  
  
-   選択した場合**データベースから更新**SSMA は、条件が満たされたときに、メタデータのデータベース定義が読み込むされます。  
  
-   選択した場合**データベースへの書き込み**SSMA は、条件が満たされたときに、SSMA メタデータの内容に基づき、データベース内のオブジェクトは更新します。  
  
-   選択した場合**Skip**SSMA では、更新動作は実行されません。  
  
##### <a name="action-on-remote-object-change"></a>リモート オブジェクトの変更のアクション  
データベース サーバーで、オブジェクトが変更の同期 ダイアログ ボックスで、既定の設定を指定します。  
  
-   選択した場合**データベースから更新**SSMA は、条件が満たされたときに、メタデータのデータベース定義が読み込むされます。  
  
-   選択した場合**データベースへの書き込み**SSMA は、条件が満たされたときに、SSMA メタデータの内容に基づき、データベース内のオブジェクトは更新します。  
  
-   選択した場合**Skip**SSMA では、更新動作は実行されません。  
  
##### <a name="action-when-local-object-metadata-is-missing"></a>ローカル オブジェクトのメタデータが不足している場合の動作  
ローカルのメタデータが見つからない場合に、[同期] ダイアログ ボックスで、既定の設定を指定します。  
  
-   選択した場合**データベースから更新**SSMA では、条件が満たされたときにデータベース オプションから、更新を選択します。  
  
-   選択した場合**データベースへの書き込み**SSMA は、条件が満たされたときに、データベースからのオブジェクトが削除されます。  
  
-   選択した場合**Skip**SSMA では、更新動作は実行されません。  
  
