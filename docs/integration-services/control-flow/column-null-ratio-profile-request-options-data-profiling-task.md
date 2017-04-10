---
title: "[列の NULL 比プロファイル要求] のオプション (データ プロファイル タスク) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "データ プロファイル タスク エディター"
ms.assetid: 157ef8e4-fd23-4f81-8194-eebf74e9fd86
caps.latest.revision: 19
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 19
---
# [列の NULL 比プロファイル要求] のオプション (データ プロファイル タスク)
  **[プロファイル要求]** ページの **[要求プロパティ]** ペインを使用すると、要求ペインで選択した **[列の NULL 比要求]** のオプションを設定できます。 列の NULL 比プロファイルは、選択した列の NULL 値の比率を報告します。 このプロファイルを使用すると、列の NULL 値の比率が予想外に高いなどのデータの問題を特定できます。 たとえば、列の NULL 比プロファイルを使用して郵便番号列をプロファイルすると、許容範囲を超える欠落した郵便番号の比率を検出できます。  
  
> [!NOTE]  
>  このトピックで説明するオプションは、 **[データ プロファイル タスク エディター]** の **[プロファイル要求]**ページに表示されます。 エディターのこのページの詳細については、「[[データ プロファイル タスク エディター] ([プロファイル要求] ページ)](../Topic/Data%20Profiling%20Task%20Editor%20\(Profile%20Requests%20Page\).md)」を参照してください。  
  
 データ プロファイル タスクの使用方法の詳細については、「[データ プロファイル タスクのセットアップ](../../integration-services/control-flow/setup-of-the-data-profiling-task.md)」を参照してください。 Data Profile Viewer を使用してデータ プロファイル タスクの出力を分析する方法の詳細については、「[Data Profile Viewer](../../integration-services/control-flow/data-profile-viewer.md)」を参照してください。  
  
## [要求プロパティ] のオプション  
 **[要求プロパティ]**ペインに表示される **[列の NULL 比要求]** のオプション グループは次のとおりです。  
  
-   **[データ]**( **[TableOrView]** オプション、 **[Column]** オプションなど)  
  
-   **全般**  
  
### [データ] のオプション  
 **[ConnectionManager]**  
 プロファイル対象のテーブルまたはビューを含む [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに接続するには、.NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) を使用する既存の [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーを選択します。  
  
 **[TableOrView]**  
 プロファイル対象の列を含む既存のテーブルまたはビューを選択します。  
  
 詳細については、このトピックの「[TableorView] のオプション」を参照してください。  
  
 **列**  
 プロファイル対象の既存の列を選択します。 すべての列をプロファイルするには、**[(\*)]** を選択します。  
  
 詳細については、このトピックの「[列] のオプション」を参照してください。  
  
#### [TableOrView] のオプション  
 **スキーマ**  
 選択したテーブルが属するスキーマを指定します。 このオプションは読み取り専用です。  
  
 **Table**  
 選択したテーブルの名前を表示します。 このオプションは読み取り専用です。  
  
#### [列] のオプション  
 **IsWildCard**  
 **[(\*)]** ワイルドカードが選択されているかどうかを示します。 **[(\*)]** を選択してすべての列をプロファイルする場合、このオプションは **[True]** に設定されます。 個々の列をプロファイル対象として選択した場合、このオプションは **[False]** になります。 このオプションは読み取り専用です。  
  
 **[ColumnName]**  
 選択した列の名前を表示します。 **[(\*)]** を選択してすべての列をプロファイルする場合、このオプションは空白になります。 このオプションは読み取り専用です。  
  
 **[StringCompareOptions]**  
 このオプションは、列の NULL 比プロファイルには適用されません。  
  
### [全般] のオプション  
 **RequestID**  
 このプロファイル要求を識別するわかりやすい名前を入力します。 通常、自動生成された値を変更する必要はありません。  
  
## 参照  
 [データ プロファイル タスク エディター ([全般] ページ)](../Topic/Data%20Profiling%20Task%20Editor%20\(General%20Page\).md)   
 [単一テーブル クイック プロファイル フォーム (データ プロファイル タスク)](../../integration-services/control-flow/single-table-quick-profile-form-data-profiling-task.md)  
  
  