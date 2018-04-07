---
title: 評価レポート (SybaseToSQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: af24f2c4-5e86-4135-a4f3-a24faaeeefe7
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f7d282ec97f55631c35e7e7f544d9f924d96b49a
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="assessment-report-sybasetosql"></a>評価レポート (SybaseToSQL)
評価 [レポート] ウィンドウは、データベース オブジェクトの変換結果を示しています。[!INCLUDE[tsql](../../includes/tsql_md.md)]構文、およびヘルプの複雑さと、移行プロジェクトの費用を見積もることができます。  
  
ソース メタデータ エクスプ ローラーで、変換するオブジェクトの選択、評価レポートにアクセスを右クリックして**データベース**、し、**レポートの作成**です。  
  
## <a name="options"></a>オプション  
**変換の統計情報**  
ステートメントの種類別の変換の統計情報を示します。 このウィンドウは、スキーマなどのグループ オブジェクト場合にのみ表示または左側のウィンドウでコードがないオブジェクトを選択します。  
  
**カテゴリ別にオブジェクト**  
オブジェクトの種類によって変換統計情報を表示します。 このウィンドウは、スキーマなどのグループ オブジェクト場合にのみ表示または左側のウィンドウでコードがないオブジェクトを選択します。  
  
**統計**  
選択したオブジェクトの変換の統計情報を示します。 このウィンドウは、コードでは個々 のオブジェクトが左側のペインで選択されている場合にのみ表示されます。 展開する必要があります**統計**をこのペインを表示します。  
  
**ソースのナビゲーション**  
変換されていないコードを示し、選択したオブジェクトの ASE コードを示しています[!INCLUDE[tsql](../../includes/tsql_md.md)]です。 このウィンドウは、コードでは個々 のオブジェクトが左側のペインで選択されている場合にのみ表示されます。  
  
行番号を設定またはブックマークをクリア をクリックします。 ウィンドウの上部にあるボタンを使用して、コード内を移動します。  
  
**ターゲットのナビゲーション**  
変換の結果を示しています。[!INCLUDE[tsql](../../includes/tsql_md.md)]は変換されていないコードのエラー メッセージと、選択したオブジェクトのコード。 このウィンドウは、コードでは個々 のオブジェクトが左側のペインで選択されている場合にのみ表示されます。  
  
行番号を設定またはブックマークをクリア をクリックします。 ウィンドウの上部にあるボタンを使用して、コード内を移動します。  
  
**[メッセージ] ウィンドウ**  
エラー、警告、および評価レポートを作成するときに生成される情報メッセージを示しています。 メッセージは、番号でグループ化されます。 エラーの原因となったコードを表示するクリックして**エラー**、**警告**、または**情報**メッセージのカテゴリを展開し、[メッセージ] をクリックします。  
  
