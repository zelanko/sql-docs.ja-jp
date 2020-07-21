---
title: SQL Server プロファイラー-[検索] ダイアログボックス |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.find.f1
helpviewer_keywords:
- Find dialog box
ms.assetid: dfaeec04-93d3-4214-9fc1-38b80179b36b
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 141cfe63151f65e171550beda1c20e232a6205e0
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84928683"
---
# <a name="sql-server-profiler---find-dialog-box"></a>[SQL Server Profiler] - [検索] ダイアログ ボックス
  **[検索]** ダイアログ ボックスを使用すると、トレース内で特定の文字や単語を検索できます。 検索の実行中に取り消すには、<localizedText>Esc</localizedText> キーを押します。  
  
 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]でこのダイアログ ボックスを開くには、 **[編集]** メニューの **[検索]** をクリックします。  
  
## <a name="options"></a>オプション  
 **[検索する文字列]**  
 検索するテキストを入力します。 指定した文字列を含むすべての文字列が検索されます。 たとえば、検索文字列として "Completed" を指定すると、一致する文字列として "SQL:BatchCompleted" が検索されます。 ワイルドカード文字 (*、? など) はサポートされません。  
  
 **[検索する列]**  
 検索するデータ列をクリックするか、クリックして **\<All columns>** トレース内のすべてのデータ列を検索します。  
  
 **[大文字と小文字を区別する]**  
 **[検索する文字列]** ボックスで指定したテキストと、大文字と小文字の違いまで一致するテキストを検索します。 このチェック ボックスをオフにすると、大文字と小文字の違いが一致しないテキストも含めてトレースを検索します。  
  
 **[単語単位]**  
 単語全体に一致する対象のみを検索します。 **[単語単位]** チェック ボックスをオフにすると、単語内の文字列も検索対象になります。  
  
 **[次を検索]**  
 次に出現する **[検索する文字列]** ボックスの文字列を検索します。  
  
 **[前を検索]**  
 トレース内をさかのぼって、前に出現する **[検索する文字列]** ボックスの文字列を検索します。  
  
## <a name="see-also"></a>参照  
 [&#40;SQL Server プロファイラーのトレース中に値列またはデータ列を検索&#41;](../tools/sql-server-profiler/find-a-value-or-data-column-while-tracing-sql-server-profiler.md)   
 [トレース &#40;SQL Server プロファイラーの作成&#41;](../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)   
 [トレーステーブル &#40;SQL Server プロファイラーを開き&#41;](../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md)   
 [トレースファイル &#40;SQL Server プロファイラーを開き&#41;](../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md)   
 [SQL Server プロファイラーのテンプレートと権限](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
