---
title: '[コピー元のテーブルおよびビューを選択] (SQL Server インポートおよびエクスポート ウィザード) | Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.selectsourcetablesandviews.f1
ms.assetid: f60e1a19-2ea6-403c-89ab-3e60ac533ea0
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2f99b94c133ba2a8bfd8bbe6d7b78bd455061409
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48050138"
---
# <a name="select-source-tables-and-views-sql-server-import-and-export-wizard"></a>[コピー元のテーブルおよびビューを選択]\(SQL Server インポートおよびエクスポート ウィザード)
  使用して、**選択元のテーブルおよびビュー**ページでテーブルと変換先にデータ ソースからコピーされるビューを指定します。  
  
> [!NOTE]  
>  テーブルをコピーするオプションを選択する際に、テーブル内のすべての列をコピーする必要はありません。 変換先テーブルを選択すると、表示するには、マッピングの編集 をクリックして、**列マッピング** ダイアログ ボックス。 選択**\<無視 >** で、**先**の列、**列マッピング**をスキップする列 ダイアログ ボックス。  
  
 このウィザードの詳細については、次を参照してください。 [SQL Server インポートおよびエクスポート ウィザード](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)します。 ウィザードを正常に実行するために必要なアクセス許可と、ウィザードを起動するオプションについて説明しますを参照してください。 [、SQL Server インポートおよびエクスポート ウィザードを実行](start-the-sql-server-import-and-export-wizard.md)します。  
  
 SQL Server インポートおよびエクスポート ウィザードの目的は、変換元から変換先にデータをコピーすることです。 また、このウィザードでは、変換先データベースと変換先テーブルも作成できます。 ただし、複数のデータベースやテーブルまたは他の種類のデータベース オブジェクトをコピーする必要がある場合は、データベース コピー ウィザードを使用してください。 詳細については、「 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)」を参照してください。  
  
## <a name="options"></a>および  
  
### <a name="tables-and-views-list"></a>[テーブルとビュー] の一覧  
 **Source**  
 チェック ボックスを使用して、コピー先にコピーできるテーブルとビューを一覧から選択します。 コピー元のテーブルとビューを選択していて他のアクションは何も実行しない場合は、コピー元のスキーマとデータは変更なしでコピーされます。  
  
 **変換先**  
 コピー元のテーブルごとに、一覧からコピー先のテーブルを選択します。  
  
> [!NOTE]  
>  この時点で、変換先テーブルを作成するウィザードで一時停止した場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を使用して[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]か別のツール、新しいテーブルが使用できる変換先テーブルの一覧に直ちに表示ではありません。 変換先テーブルの一覧を更新するには、手順に 2 つのページをバックアップ、**変換先の選択**ページで、移行先データベースを再度選択し、もう一度ステップ前進、**選択元のテーブルおよびビュー**します。  
  
### <a name="other-options"></a>その他のオプション  
 **マッピングを編集します。**  
 使用して、**列マッピング** ダイアログ ボックスで、ソース データを受信する変換先列を指定します。 列のサブセットのみをコピーするを選択\<無視 > で、**先**の列、**列マッピング**をスキップする列 ダイアログ ボックス。  
  
 **プレビュー**  
 ソースのデータのプレビュー、**データのプレビュー**インポートを実行する前に確認またはエクスポート ダイアログ ボックス。 **データのプレビュー**  ダイアログ ボックスには、最大 200 行のデータが表示されます。  
  
 データをプレビューした後に、データのコピー元およびコピー先に対して選択したオプションを変更することもできます。 これらの変更を行うには、**[コピー元のテーブルおよびビューを選択]** ページで **[戻る]** をクリックし、選択の変更が可能な前のページに戻ります。  
  
  
