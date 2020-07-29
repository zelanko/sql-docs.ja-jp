---
title: 結果ペイン内の行の削除
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- View Designer, Results pane
- removing rows
- row removal [SQL Server], Visual Database Tools Results pane
- row deletions [SQL Server], Visual Database Tools Results pane
- Query Designer [SQL Server], Results pane
- deleting rows
- Results pane
ms.assetid: a1147905-fe4a-4fac-b576-a17622477e66
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: 71e70000e6a4b1c6208e19f5d233f44fb31b965b
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/06/2020
ms.locfileid: "86008334"
---
# <a name="delete-rows-in-the-results-pane-visual-database-tools"></a>結果ペイン内の行の削除 (Visual Database Tools)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
データベース内のレコードを削除するには、結果ペイン内の行を削除します。 すべての行を削除する場合、削除クエリを使用できます。 詳細については、「 [削除クエリの作成 (Visual Database Tools)](../../ssms/visual-db-tools/create-delete-queries-visual-database-tools.md)」を参照してください。 結果ペインからの行の削除だけを行う場合は、クエリの条件を変更します。 詳細については、「 [検索基準の指定 (Visual Database Tools)](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)」を参照してください。  
  
### <a name="to-delete-a-row-or-rows"></a>1 行または複数の行を削除するには  
  
1.  結果ペイン内で、削除する行の左側にあるボックスを選択します。  
  
2.  Del キーを押します。  
  
3.  確認を要求するメッセージ ボックスで、 **[はい]** をクリックします。  
  
> [!CAUTION]  
> この方法で削除した行は、データベースから完全に削除され、再度呼び出すことはできません。  
  
> [!NOTE]  
> 選択した行をデータベースから削除できない場合、行の削除は行われず、削除できない行を通知するメッセージが表示されます。  
  
## <a name="see-also"></a>参照  
[削除クエリの作成 (Visual Database Tools)](../../ssms/visual-db-tools/create-delete-queries-visual-database-tools.md)  
[検索基準の指定 (Visual Database Tools)](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)  
  
