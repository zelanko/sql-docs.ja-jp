---
title: "評価レポート (DB2ToSQL) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssma-db2
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 9e13eba0-e3cf-4205-974f-c00f982061de
caps.latest.revision: "4"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 53ba7f2b2838d7123530825e12c7a88b2421c85c
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="assessment-report-db2tosql"></a>評価レポート (DB2ToSQL)
評価 [レポート] ウィンドウは、データベース オブジェクトの変換結果を示しています。[!INCLUDE[tsql](../../includes/tsql_md.md)]構文、およびヘルプの複雑さと、移行プロジェクトの費用を見積もることができます。  
  
ソース メタデータ エクスプ ローラーで、変換するオブジェクトの選択、評価レポートにアクセスを右クリックして**スキーマ**または**シノニム**、し、**レポートの作成**です。  
  
## <a name="options"></a>オプション  
  
|||  
|-|-|  
|項目|定義|  
|**変換の統計情報**|ステートメントの種類別の変換の統計情報を示します。 このウィンドウは、スキーマなどのグループ オブジェクトのときに表示されるまたは左側のウィンドウでコードがないオブジェクトを選択します。|  
|**カテゴリ別にオブジェクト**|カテゴリ別のオブジェクトの数を示します。 このウィンドウは、スキーマなどのグループ オブジェクト場合にのみ表示または左側のウィンドウでコードがないオブジェクトを選択します。|  
|**統計**|選択したオブジェクトの変換の統計情報を示します。 このウィンドウは、コードでは個々 のオブジェクトが左側のペインで選択されている場合にのみ表示されます。 展開する必要があります**統計**をすぐに、**ソース** ウィンドウでこのウィンドウを表示します。|  
|**ソース**|変換されていないコードを示し、選択したオブジェクトの DB2 コードを示しています[!INCLUDE[tsql](../../includes/tsql_md.md)]です。 このウィンドウは、コードでは個々 のオブジェクトが左側のペインで選択されている場合にのみ表示されます。<br /><br />行番号を設定またはブックマークをクリア をクリックします。 ウィンドウの上部にあるボタンを使用して、コード内を移動します。|  
|**移行先**|変換の結果を示しています。[!INCLUDE[tsql](../../includes/tsql_md.md)]は変換されていないコードのエラー メッセージと、選択したオブジェクトのコード。 このウィンドウは、コードでは個々 のオブジェクトが左側のペインで選択されている場合にのみ表示されます。<br /><br />行番号を設定またはブックマークをクリア をクリックします。 ウィンドウの上部にあるボタンを使用して、コード内を移動します。|  
|**[メッセージ] ウィンドウ**|エラー、警告、および評価レポートを作成するときに生成された情報のメッセージを示しています。 メッセージは、番号でグループ化されます。 エラーの原因となったコードを表示するクリックして**エラー**、**警告**、または**情報**メッセージのカテゴリを展開し、[メッセージ] をクリックします。|  
  
