---
title: "[SQL 変換先エディター] ([接続マネージャー] ページ) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.sqlserverdestadapter.connection.f1"
helpviewer_keywords: 
  - "SQL Server 変換先エディター"
ms.assetid: 423e1654-54af-47c6-ab6f-98670534557d
caps.latest.revision: 37
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 37
---
# [SQL 変換先エディター] ([接続マネージャー] ページ)
  **[SQL 変換先エディター]** ダイアログ ボックスの **[接続マネージャー]** ページを使用すると、データ ソース情報を指定したり、結果をプレビューしたりできます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 変換先エディターは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのテーブルまたはビューにデータを読み込みます。  
  
 SQL Server 変換先の詳細については、「 [SQL Server Destination](../../integration-services/data-flow/sql-server-destination.md)」を参照してください。  
  
## オプション  
 **OLE DB 接続マネージャー**  
 一覧から既存の接続を選択するか、**[新規作成]** をクリックして新しい接続を作成します。  
  
 **新規**  
 **[OLE DB 接続マネージャーの構成]** ダイアログ ボックスを使用して、新しい接続を作成します。  
  
 **[テーブルまたはビューを使用する]**  
 既存のテーブルまたはビューを一覧から選択するか、**[新規作成]** をクリックして新しい接続を作成します。  
  
 **新規**  
 **[テーブルの作成]** ダイアログ ボックスを使用して新しいテーブルを作成します。  
  
> [!NOTE]  
>  **[新規作成]** をクリックすると、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] により、接続されているデータ ソースに基づいて既定の CREATE TABLE ステートメントが生成されます。 基になるテーブルの列に FILESTREAM 属性が宣言されていても、この既定の CREATE TABLE ステートメントには FILESTREAM 属性が含まれません。 FILESTREAM 属性を使用して [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] コンポーネントを実行するには、まず対象データベースに FILESTREAM ストレージを実装します。 次に、**[テーブルの作成]** ダイアログ ボックスで CREATE TABLE ステートメントに FILESTREAM 属性を追加します。 詳細については、「[バイナリ ラージ オブジェクト (Blob) データ (SQL Server)](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md)」を参照してください。  
  
 **プレビュー**  
 **[クエリ結果のプレビュー]** ダイアログ ボックスを使用して、結果をプレビューします。 プレビューでは、最大で 200 行を表示できます。  
  
## 参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)   
 [[SQL 変換先エディター] ([マッピング] ページ)](../Topic/SQL%20Destination%20Editor%20\(Mappings%20Page\).md)   
 [[SQL 変換先エディター] ([詳細設定] ページ)](../Topic/SQL%20Destination%20Editor%20\(Advanced%20Page\).md)   
 [SQL Server 変換先を使用してデータの一括読み込みを行う](../../integration-services/data-flow/bulk-load-data-by-using-the-sql-server-destination.md)  
  
  