---
title: Azure SQL DB (AccessToSQL) への接続 |Microsoft ドキュメント
ms.prod: sql
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Connect to SQL Azure dialog box
ms.assetid: bf44b236-d9be-41ae-a5fd-bd73038e505f
caps.latest.revision: 17
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: d61eab04dffa1723c6d77a118033eee535a917e2
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34773448"
---
# <a name="connect-to-azure-sql-db-accesstosql"></a>Azure SQL DB (AccessToSQL) への接続します。
SQL Azure ダイアログ ボックスに接続を使用すると、移行する SQL Azure データベースへの接続します。  
  
このダイアログ ボックスにアクセスする、**ファイル**メニューの  **SQL Azure への接続**です。 以前接続した場合、コマンドは**SQL Azure に再接続します。**  
  
## <a name="options"></a>および  
**[サーバー名]**  
  
選択するか、SQL Azure に接続するためのサーバー名を入力します。  
  
**[データベース]**  
  
選択し、入力または**参照**データベース名。  
  
> [!IMPORTANT]  
> SSMA のアクセスは、SQL Azure で master データベースへの接続をサポートしていません。  
  
**ユーザー名**  
  
SSMA は、SQL Azure データベースへの接続を使用してユーザー名を入力します。  
  
**Password**  
  
ユーザー名に対応するパスワードを入力します。  
  
**Encrypt**  
  
SSMA は、SQL Azure に暗号化された接続をお勧めします。  
  
## <a name="create-azure-database"></a>Azure のデータベースを作成します。  
新しい azure データベースを作成するには次の手順に従います  
  
1.  SQL Azure ダイアログ ボックスに、接続に存在する 参照 ボタンをクリックします。  
  
2.  データベースが存在しない場合は、次の 2 つのメニュー項目が表示されます。  
  
    1.  **(データベースが見つかりません)** は無効になっているし、すべての時間がグレーで表示されます。  
  
    2.  **新しいデータベースを作成**を常が有効な SQL Azure アカウントに新しい azure データベースを作成するユーザーを有効にするとします。 このメニュー項目をクリックすると、次のように作成します。 azure データベース ダイアログ ボックスがデータベースの名前とサイズが存在します。  
  
3.  データベースの作成時に、これら 2 つのパラメーターを入力として指定します。  
  
    1.  **データベース名:** データベース名を入力します。  
  
    2.  **データベース サイズ:** SQL Azure アカウントで作成する必要のあるデータベースのサイズを選択します。  
  
