---
title: '[コピー元のテーブルおよびビューを選択] (SQL Server インポートおよびエクスポート ウィザード) | Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.selectsourcetablesandviews.f1
ms.assetid: f60e1a19-2ea6-403c-89ab-3e60ac533ea0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6356cb594013d642741148dd85f7ddefc1e08ff0
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85436749"
---
# <a name="select-source-tables-and-views-sql-server-import-and-export-wizard"></a>[コピー元のテーブルおよびビューを選択]\(SQL Server インポートおよびエクスポート ウィザード)
  [コピー**元のテーブルおよびビューを選択**] ページを使用すると、データソースから変換先にコピーするテーブルとビューを指定できます。  
  
> [!NOTE]  
>  テーブルをコピーするオプションを選択する際に、テーブル内のすべての列をコピーする必要はありません。 変換先テーブルを選択したら、[マッピングの編集] をクリックして [**列マッピング**] ダイアログボックスを表示します。 **\<ignore>** スキップする列については、[**列マッピング**] ダイアログボックスの [**変換先**] 列でを選択します。  
  
 このウィザードの詳細については、「 [SQL Server インポートおよびエクスポートウィザード](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)」を参照してください。 ウィザードを起動するためのオプション、およびウィザードを正常に実行するために必要な権限については、「 [run the SQL Server Import And Export wizard](start-the-sql-server-import-and-export-wizard.md)」を参照してください。  
  
 SQL Server インポートおよびエクスポート ウィザードの目的は、変換元から変換先にデータをコピーすることです。 また、このウィザードでは、変換先データベースと変換先テーブルも作成できます。 ただし、複数のデータベースやテーブルまたは他の種類のデータベース オブジェクトをコピーする必要がある場合は、データベース コピー ウィザードを使用してください。 詳細については、「 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)」を参照してください。  
  
## <a name="options"></a>オプション  
  
### <a name="tables-and-views-list"></a>[テーブルとビュー] の一覧  
 **ソース**  
 チェック ボックスを使用して、コピー先にコピーできるテーブルとビューを一覧から選択します。 コピー元のテーブルとビューを選択していて他のアクションは何も実行しない場合は、コピー元のスキーマとデータは変更なしでコピーされます。  
  
 **宛先**  
 コピー元のテーブルごとに、一覧からコピー先のテーブルを選択します。  
  
> [!NOTE]  
>  この時点でウィザードを一時停止し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または別のツールを使用して [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] の変換先テーブルを作成した場合、新しいテーブルは使用可能な変換先テーブルの一覧にすぐには表示されません。 変換先テーブルの一覧を更新するには、2つのページを [**変換先の選択**] ページに戻り、変換先データベースを再選択してから、 **[コピー元のテーブルおよびビューを選択]** にもう一度進みます。  
  
### <a name="other-options"></a>その他のオプション  
 **[マッピングの編集]**  
 [**列マッピング**] ダイアログボックスを使用すると、ソースデータを受け取る変換先列を指定できます。 \<ignore>スキップする列については、[**列マッピング**] ダイアログボックスの [**変換先**] 列でを選択すると、列のサブセットのみをコピーできます。  
  
 **プレビュー**  
 インポートまたはエクスポートを実行する前に確認するには、[**データのプレビュー** ] ダイアログボックスでソースデータをプレビューします。 [**データのプレビュー** ] ダイアログボックスには、最大200行のデータが表示されます。  
  
 データをプレビューした後に、データのコピー元およびコピー先に対して選択したオプションを変更することもできます。 これらの変更を行うには、**[コピー元のテーブルおよびビューを選択]** ページで **[戻る]** をクリックし、選択の変更が可能な前のページに戻ります。  
  
  
