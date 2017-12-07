---
title: "Azure SQL DB (MySQLToSQL) への接続 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssma-mysql
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 81623d27-25af-444f-9779-1edb8c6fb470
caps.latest.revision: "8"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dadd18eb9f5f2af55b2d68ad69f69fb3c54709fc
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="connect-to-azure-sql-db-mysqltosql"></a>Azure SQL DB (MySQLToSQL) への接続します。
SQL Azure] ダイアログ ボックスに接続を使用すると、移行する SQL Azure データベースへの接続します。  
  
このダイアログ ボックスにアクセスする、**ファイル**メニューの [ **SQL Azure への接続**です。 以前接続した場合、コマンドは**SQL Azure に再接続します。**  
  
## <a name="options"></a>オプション  
**[サーバー名]**  
  
選択するか、SQL Azure に接続するためのサーバー名を入力します。  
  
**データベース**  
  
選択し、入力または**参照**データベース名。  
  
> [!IMPORTANT]  
> SSMA for MySQL は SQL Azure での master データベースへの接続をサポートしていません。  
  
**ユーザー名**  
  
SSMA は、SQL Azure データベースへの接続を使用してユーザー名を入力します。  
  
**Password**  
  
ユーザー名に対応するパスワードを入力します。  
  
**暗号化します。**  
  
SSMA は、SQL Azure に暗号化された接続をお勧めします。  
  
## <a name="create-azure-database"></a>Azure のデータベースを作成します。  
SQL Azure アカウントでにデータベースがない場合は、最初のデータベースを作成できます。  
  
非常に最初に、新しいデータベースを作成するには次の手順に従います  
  
1.  SQL Azure] ダイアログ ボックスに、接続に存在する [参照] ボタンをクリックします。  
  
2.  データベースが存在しない場合は、次の 2 つのメニュー項目が表示されます。  
  
    1.  **(データベースが見つかりません)**は無効になっているし、すべての時間がグレーで表示されます。  
  
    2.  **新しいデータベースを作成**SQL Azure アカウントにデータベースがない場合にのみこれを有効にします。 このメニュー項目をクリックすると、Azure データベースの作成] ダイアログ ボックスがあるデータベースの名前とサイズを使用します。  
  
3.  データベースの作成時に、次の 2 つのパラメーターは入力として指定します。  
  
    1.  **データベース名:**データベース名を入力します。  
  
    2.  **データベース サイズ:** SQL Azure アカウントで作成する必要のあるデータベースのサイズを選択します。  
  
