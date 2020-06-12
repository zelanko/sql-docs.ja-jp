---
title: オプション (クエリ結果-マルチサーバー SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.sqleditors.multiserverresultssettings
- VS.ToolsOptionsPages.QueryResults.SqlServer.SQLMultiServerResults
ms.assetid: d6768bd8-9cb5-4606-a726-a33a1df9e1bb
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: c52b48ffdfc0e837525447eff3813b3d91b57700
ms.sourcegitcommit: 18a7c77be31f9af92ad9d0d3ac5eecebe8eec959
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/26/2020
ms.locfileid: "83856526"
---
# <a name="options-query-results-sql-server-multi-server"></a>[オプション] ([クエリ結果] - [SQL Server] - [マルチサーバー])
  複数のサーバーに対して同時にクエリを実行する場合、このページで結果セットの表示オプションを指定します。 結果をマージすると、すべてのサーバーからの結果セットが 1 つの結果セットに結合されます。 結果をマージする場合は、最初に応答したサーバーによって結果セットのスキーマが設定されます。 結果セットをマージするには、クエリから返される列の数とその列名が、各サーバーで同じであることが必要です。 結果をマージする際には、最初に結果を返したサーバーから返されたスキーマ (列数と列名) と一致しないサーバーごとにメッセージが表示されます。  
  
 結果をマージしない場合は、各サーバーからの結果セットが、それぞれのスキーマを使用した固有のグリッドに表示されます。  
  
## <a name="ui-element-list"></a>UI 要素の一覧  
 **[結果のマージ]**  
 複数のサーバーからの結果セットを同じグリッドに結合する場合は、このチェック ボックスをオンにします。  
  
 **[サーバー名を結果に追加]**  
 各行を生成したサーバーの名前を表示する列を追加するには、このチェック ボックスをオンにします。  
  
 **[ログイン名を結果に追加]**  
 各行を提供したサーバーへの接続に使用されたログインを表示する列を追加するには、このチェック ボックスをオンにします。  
  
## <a name="see-also"></a>参照  
 [中央管理サーバーとサーバーグループ &#40;SQL Server Management Studio を作成&#41;](../ssms/register-servers/create-a-central-management-server-and-server-group.md)   
 [複数のサーバーに対してステートメントを同時に実行する方法 &#40;SQL Server Management Studio&#41;](../ssms/register-servers/execute-statements-against-multiple-servers-simultaneously.md)  
  
  
