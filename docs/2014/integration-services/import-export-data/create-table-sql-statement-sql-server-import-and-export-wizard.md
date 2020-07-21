---
title: '[テーブル作成 SQL ステートメント] (SQL Server インポートおよびエクスポート ウィザード) | Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.createtablesql.f1
ms.assetid: 0d6f6b3b-d023-4770-a8a9-65b2977c8d05
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d3fc2054711708a27691f2d7219c33749f11b977
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85424959"
---
# <a name="create-table-sql-statement-sql-server-import-and-export-wizard"></a>[テーブル作成 SQL ステートメント] (SQL Server インポートおよびエクスポート ウィザード)
  [**テーブル作成 SQL ステートメント**] ダイアログボックスを使用すると、自動的に生成されたステートメントを表示したり、目的に合わせて変更したりできます。 このステートメントを変更する場合、それに関連して、列のマッピングにも変更を加えなければならない場合があります。それ以降も、編集した SQL ステートメントは手動で保守する必要があります。  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] により、接続されているデータ ソースに基づいて既定の CREATE TABLE ステートメントが生成されます。 基になるテーブルの列に FILESTREAM 属性が宣言されていても、この既定の CREATE TABLE ステートメントには FILESTREAM 属性が含まれません。 FILESTREAM 属性を使用して [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] コンポーネントを実行するには、まず対象データベースに FILESTREAM ストレージを実装します。 次に、 **[テーブルの作成]** ダイアログ ボックスで CREATE TABLE ステートメントに FILESTREAM 属性を追加します。 詳細については、「[バイナリ ラージ オブジェクト &#40;Blob&#41; データ &#40;SQL Server&#41;](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md)」を参照してください。  
  
 このウィザードの詳細については、「 [SQL Server インポートおよびエクスポートウィザード](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)」を参照してください。 ウィザードを起動するためのオプション、およびウィザードを正常に実行するために必要な権限の詳細については、「 [run the SQL Server Import And Export wizard](start-the-sql-server-import-and-export-wizard.md)」を参照してください。  
  
 SQL Server インポートおよびエクスポート ウィザードの目的は、変換元から変換先にデータをコピーすることです。 また、このウィザードでは、変換先データベースと変換先テーブルも作成できます。 ただし、複数のデータベースやテーブルまたは他の種類のデータベース オブジェクトをコピーする必要がある場合は、データベース コピー ウィザードを使用してください。 詳細については、「 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **SQL ステートメント**  
 自動生成された SQL ステートメントが表示され、編集できます。  
  
> [!NOTE]  
>  SQL ステートメントにキャリッジ リターンを含める場合は、&lt;localizedText&gt;Ctrl&lt;/localizedText&gt; キーを押しながら &lt;localizedText&gt;Enter&lt;/localizedText&gt; キーを押します。 Enter&lt;/localizedText&gt; キーだけを押すと、ダイアログ ボックスが終了します。  
  
 **生成**  
 既定の SQL ステートメントを変更していた場合、**[自動生成]** をクリックすると復元されます。  
  
  
