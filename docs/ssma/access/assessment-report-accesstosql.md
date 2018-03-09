---
title: "評価レポート (AccessToSQL) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-access
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
helpviewer_keywords:
- Assessment Report dialog box
- Conversion Report dialog box
ms.assetid: ba6f53aa-0049-4c49-8bb8-607a8bfaa737
caps.latest.revision: "14"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3a171fdf7f717ba5af9e0ecf73f5aca17923e155
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="assessment-report-accesstosql"></a>評価レポート (AccessToSQL)
評価 [レポート] ウィンドウは、データベース オブジェクトの変換結果を示しています。[!INCLUDE[tsql](../../includes/tsql_md.md)]構文、およびヘルプの複雑さと、移行プロジェクトの費用を見積もることができます。  
  
ソース メタデータ エクスプ ローラーで、変換するオブジェクトの選択、評価レポートを作成するには**データベース**、し、**レポートの作成**です。 スキーマを変換した後、このレポートを自動的に表示もできます。 ただし、レポート名は、変換レポートになります。 詳細については、次を参照してください。[プロジェクトの設定 (GUI) (SSMA 共通)](http://msdn.microsoft.com/en-us/cf06baf1-8714-48a3-95dc-781f6ca53693)です。  
  
## <a name="options"></a>および  
**エクスプ ローラー ペイン**  
評価レポート内のオブジェクトの階層が含まれています。 個々 のオブジェクトとこれらのサブコンポーネントを表示するフォルダーを展開します。 カテゴリまたはオブジェクトをクリックすると、詳細ウィンドウで、そのカテゴリまたはオブジェクトの変換の統計情報が表示されます。  
  
**詳細ウィンドウ**  
選択したオブジェクトの統計情報やエラーと警告メッセージの変換を示しています。 たとえば、テーブル フォルダーを選択すると、詳細ウィンドウには外部キー、インデックス、主キー、および変換されたテーブルの数が表示されます。  
  
**[メッセージ] ウィンドウ**  
エラー、警告、および評価レポートの作成時に生成された情報メッセージを示しています。 メッセージは、番号でグループ化されます。  
  
メッセージの詳細を表示するには、いずれかをクリックして**エラー**、**警告**、または**メッセージ**、およびメッセージの順に展開します。 SSMA は、このエラーのあるオブジェクトの一覧に表示されます。 オブジェクトのすべての変換の詳細を表示するオブジェクトをクリックします。  
  
## <a name="see-also"></a>参照  
[ユーザー インターフェイス Reference(Access)](http://msdn.microsoft.com/en-us/af24c303-4a41-449b-9c86-d6558a97e839)  
  
