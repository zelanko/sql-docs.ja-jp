---
title: オプション (クエリ結果-SQL Server-複数のサーバー) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.sqleditors.multiserverresultssettings
- VS.ToolsOptionsPages.QueryResults.SqlServer.SQLMultiServerResults
ms.assetid: d6768bd8-9cb5-4606-a726-a33a1df9e1bb
caps.latest.revision: 9
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: a1465defc783d0fde352a29648af61c0bb99ff59
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36075573"
---
# <a name="options-query-results-sql-server-multi-server"></a>オプション (クエリ結果-SQL Server-複数のサーバー)
  複数のサーバーに対して同時にクエリを実行する場合、このページで結果セットの表示オプションを指定します。 結果をマージすると、すべてのサーバーからの結果セットが 1 つの結果セットに結合されます。 結果をマージする場合は、最初に応答したサーバーによって結果セットのスキーマが設定されます。 結果セットをマージするには、クエリから返される列の数とその列名が、各サーバーで同じであることが必要です。 結果をマージする際には、最初に結果を返したサーバーから返されたスキーマ (列数と列名) と一致しないサーバーごとにメッセージが表示されます。  
  
 結果をマージしない場合は、各サーバーからの結果セットが、それぞれのスキーマを使用した固有のグリッドに表示されます。  
  
## <a name="uielement-list"></a>UI 要素の一覧  
 **結果をマージします。**  
 複数のサーバーからの結果セットを同じグリッドに結合する場合は、このチェック ボックスをオンにします。  
  
 **サーバー名を結果に追加します。**  
 各行を生成したサーバーの名前を表示する列を追加するには、このチェック ボックスをオンにします。  
  
 **ログイン名を結果に追加します。**  
 各行を提供したサーバーへの接続に使用されたログインを表示する列を追加するには、このチェック ボックスをオンにします。  
  
## <a name="see-also"></a>参照  
 [中央管理サーバーとサーバー グループの作成&#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-a-central-management-server-and-server-group.md)   
 [複数のサーバーに対してステートメントを同時に実行する方法 &#40;SQL Server Management Studio&#41;](../ssms/register-servers/execute-statements-against-multiple-servers-simultaneously.md)  
  
  