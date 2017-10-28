---
title: "Stretch Database データベースとテーブル - Stretch Database Advisor | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/14/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-stretch
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Stretch Database, identifying databases
- Stretch Database, identifying tables
- identifying databases for Stretch Database
- identifying tables for Stretch Database
ms.assetid: 81bd93d8-eef8-4572-88d7-5c37ab5ac2bf
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 9045ebe77cf2f60fecad22672f3f055d8c5fdff2
ms.openlocfilehash: 59608301d353d99eb710a956389fd9f8d8948dfe
ms.contentlocale: ja-jp
ms.lasthandoff: 07/29/2017

---
# <a name="stretch-database-databases-and-tables---stretch-database-advisor"></a>Stretch Database データベースとテーブル - Stretch Database Advisor
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Stretch Database の候補となるデータベースとテーブルを特定するには、SQL Server 2016 Upgrade Advisor をダウンロードし、Stretch Database Advisor を実行します。 Stretch Database Advisor はブロックの問題も特定します。  
  
## <a name="download-and-install-upgrade-advisor"></a>アップグレード アドバイザーのダウンロードおよびインストール  
 アップグレード アドバイザーを [ここ](https://www.microsoft.com/en-us/download/details.aspx?id=53595)からダウンロードし、インストールします。 このツールは、 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] インストール メディアには含まれていません。  
  
## <a name="run-the-stretch-database-advisor"></a>Stretch Database Advisor の実行  
  
1.  アップグレード アドバイザーを実行します。  
  
2.  **[シナリオ]**を選択してから、 **[STRETCH DATABASE ADVISOR の実行]**を選択します。  
  
3.  **[Stretch Database Advisor の実行]** ブレードで、 **[分析するデータベースの選択]**をクリックします。  
  
4.  **[データベースの選択]** ブレードで、サーバー名と認証情報を入力または選択します。 **[接続]**をクリックします。

5.  選択したサーバー上のデータベースが一覧表示されます。 分析するデータベースを選択してください。 **[選択]**をクリックします。  
  
6.  **[Stretch Database Advisor の実行]** ブレードで、 **[実行]**をクリックします。  分析が実行されます。  
  
## <a name="review-the-results"></a>結果の確認  
  
1.  分析が完了したら、 **[Analyzed databases (データベースの分析)]** ブレードで、分析したデータベースのいずれかを選択し、 **[分析結果]** ブレードを表示します。  
  
     **[分析結果]** ブレードには、既定の推奨基準に適合する、選択されたデータベースの推奨テーブルが一覧表示されます。 
  
2.  **[分析結果]** ブレード上のテーブルの一覧で、推奨テーブルのいずれかを選択し、 **[テーブル結果]** ブレードを表示します。  
  
     ブロック問題がある場合は、 **[テーブル結果]** ブレードに、選択されたテーブルのブロック問題が一覧表示されます。 Stretch Database Advisor によって検出されるブロック問題については、「 [Stretch Database の制限事項](../../sql-server/stretch-database/limitations-for-stretch-database.md)」を参照してください。  
  
3.  **[テーブル結果]** ブレード上のブロック問題の一覧で、問題のいずれかを選択すると、選択した問題の詳細情報が表示され、軽減手順が提案されます。 選択したテーブルを Stretch Database 用に構成する場合は、推奨される軽減手順を実行します。  
  
## <a name="next-step"></a>次の手順  
 Stretch Database を有効にします。  
  
-   **データベース**の Stretch Database を有効にするには、「 [Enable Stretch Database for a database](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md)」を参照してください。  
  
-   Stretch が データベースで既に有効な場合に、別の **テーブル**の Stretch Database を有効にするには、「 [Enable Stretch Database for a table](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md)」を参照してください。 
  
## <a name="see-also"></a>参照  
 [Stretch Database の制限事項](../../sql-server/stretch-database/limitations-for-stretch-database.md)   
 [Enable Stretch Database for a database](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md)   
 [テーブルに対して Stretch Database を有効にする](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md)  
  
  

