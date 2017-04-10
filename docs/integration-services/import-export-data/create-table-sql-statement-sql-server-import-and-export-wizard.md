---
title: "[テーブル作成 SQL ステートメント] (SQL Server インポートおよびエクスポート ウィザード) | Microsoft Docs"
ms.custom: ""
ms.date: "02/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.impexpwizard.createtablesql.f1"
ms.assetid: 0d6f6b3b-d023-4770-a8a9-65b2977c8d05
caps.latest.revision: 67
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 62
---
# [テーブル作成 SQL ステートメント] (SQL Server インポートおよびエクスポート ウィザード)
**[変換先テーブルを作成する]** を選択してから **[列マッピング]** ダイアログ ボックスで **[SQL の編集]** を選択した場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードに **[テーブル作成 SQL ステートメント]** ダイアログ ボックスが表示されます。 このページでは、**CREATE TABLE** コマンドを確認し、必要に応じてカスタマイズします。このコマンドは、新しいターゲット テーブルを作成するためにウィザードで実行されます。
  
> [!NOTE] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードの **[テーブル作成 SQL ステートメント]** ダイアログ ボックスではなく、[!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TABLE ステートメントに関する情報をお探しの場合は、「[CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)」を参照してください。 
  
## <a name="screen-shot-of-the-create-table-sql-statement-page"></a>[CREATE TABLE SQL ステートメント] ページのスクリーン ショット  
 以下のスクリーン ショットには、ウィザードの **[テーブル作成 SQL ステートメント]** ダイアログ ボックスが示されています。
 
この例では、**[SQL ステートメント]** ボックスに、ウィザードで生成される既定の **CREATE TABLE** ステートメントが含まれています。 このステートメントにより、**Person.Address** ソース テーブルのコピーである新しいターゲット テーブルが作成されます。 
  
 ![Create table page of the Import and Export Wizard](../../integration-services/import-export-data/media/create-table.png "Create table page of the Import and Export Wizard")  
  
## <a name="review-or-regenerate-the-create-table-statement"></a>CREATE TABLE ステートメントの確認または再生成  
 **SQL ステートメント**  
 自動生成された SQL ステートメントが表示され、編集できます。 CREATE TABLE ステートメントと構文の詳細については、「[CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)」を参照してください。  
  
 既定の CREATE TABLE コマンドを変更する場合は、関連付けられている列マッピングの変更が必要になることもあります。  
  
 SQL ステートメントのテキストにキャリッジ リターンを含めるには、Ctrl キーを押しながら Enter キーを押します。 Enter キーだけを押すと、ダイアログ ボックスが閉じます。  
  
 **自動生成**  
 既定の SQL ステートメントを変更していた場合、**[自動生成]** をクリックすると復元されます。  
  
## <a name="create-a-table-that-includes-a-filestream-column"></a>FILESTREAM 列を含むテーブルの作成  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードにより、接続されているデータ ソースに基づいて既定の CREATE TABLE ステートメントが生成されます。 ソース テーブルに FILESTREAM 列がある場合でも、この既定の CREATE TABLE ステートメントには FILESTREAM 属性が含まれません。 ウィザードを使用して FILESTREAM 列をコピーするには、まず、対象データベースに FILESTREAM ストレージを実装します。 次に、**[テーブル作成 SQL ステートメント]** ダイアログ ボックスで CREATE TABLE ステートメントに手動で FILESTREAM 属性を追加します。 FILESTREAM の詳細については、「[バイナリ ラージ オブジェクト (Blob) データ (SQL Server)](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md)」を参照してください。  
  
## <a name="whats-next"></a>次の操作  
 CREATE TABLE コマンドを確認し、カスタマイズしてから **[OK]** をクリックすると、**[テーブル作成 SQL ステートメント]** ダイアログ ボックスから **[列マッピング]** ダイアログ ボックスに戻ります。 詳細については、「[列マッピング](../../integration-services/import-export-data/column-mappings-sql-server-import-and-export-wizard.md)」を参照してください。  
