---
title: 基になるクエリの指定 (SQL Server インポートおよびエクスポート ウィザード) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.providesourcequery.f1
ms.assetid: c8cbd07e-b9c3-422f-94b8-d6fc8cf31cf5
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 7a028c880d87e21e1fcc63ffc605e7d375619dbf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62767864"
---
# <a name="provide-a-source-query-sql-server-import-and-export-wizard"></a>[基になるクエリの指定]\(SQL Server インポートおよびエクスポート ウィザード)
  [基になる**クエリの指定**] ページを使用すると、データソースからコピー先にコピーするデータを生成する SQL ステートメントを入力できます。  
  
 このウィザードの詳細については、「 [SQL Server インポートおよびエクスポートウィザード](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)」を参照してください。 ウィザードを起動するためのオプション、およびウィザードを正常に実行するために必要な権限の詳細については、「 [run the SQL Server Import And Export wizard](start-the-sql-server-import-and-export-wizard.md)」を参照してください。  
  
 SQL Server インポートおよびエクスポート ウィザードの目的は、変換元から変換先にデータをコピーすることです。 また、このウィザードでは、変換先データベースと変換先テーブルも作成できます。 ただし、複数のデータベースやテーブルまたは他の種類のデータベース オブジェクトをコピーする必要がある場合は、データベース コピー ウィザードを使用してください。 詳細については、「 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **SQL ステートメント**  
 SQL ステートメントを入力して、ソース データベースから選択したデータ行を取得します。 たとえば、次のクエリステートメントは、 **SalesPersonID**、 **salesquota**、および**salesquota**を、歩合の割合が1.5% を超える販売員の AdventureWorks データベースから取得します。  
  
```  
SELECT SalesPersonID, SalesQuota, SalesYTD  
FROM Sales.SalesPerson  
WHERE CommissionPct > 0.015  
```  
  
 **分解**  
 
  **[SQL ステートメント]** テキスト ボックスで、SQL ステートメントの構文をチェックします。  
  
> [!NOTE]  
>  ステートメントの構文をチェックするのに必要な時間がタイムアウト値の 30 秒を超えると、解析は停止し、エラーが発生します。 解析が成功するまでは、ウィザードのこのページ以降に進めません。 1 つの解決策として、クエリに基づくデータベース ビューを作成し、クエリ テキストを直接入力するのではなく、ウィザードからビューに対してクエリを実行する方法があります。  
  
 **[参照]**  
 [**開く**] ダイアログボックスを使用して、SQL ステートメントを含むファイルを選択します。 ファイルを選択すると、ファイルから [**クエリステートメント**] テキストボックスにテキストがコピーされます。  
  
  
