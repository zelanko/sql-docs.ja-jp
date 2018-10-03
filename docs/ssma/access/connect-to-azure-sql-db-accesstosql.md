---
title: Azure SQL DB (AccessToSQL) への接続 |Microsoft Docs
ms.prod: sql
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Connect to SQL Azure dialog box
ms.assetid: bf44b236-d9be-41ae-a5fd-bd73038e505f
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 57a745385de80a3040897310ddc5b43b1301ea86
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47717480"
---
# <a name="connect-to-azure-sql-db-accesstosql"></a>Azure SQL DB (AccessToSQL) に接続します。
SQL Azure ダイアログ ボックスに、Connect を使用して、移行する SQL Azure データベースに接続します。  
  
このダイアログ ボックスにアクセスする、**ファイル**メニューの  **SQL Azure への接続**します。 以前接続した場合、コマンドは**SQL Azure に再接続します。**  
  
## <a name="options"></a>および  
**[サーバー名]**  
  
選択するか、SQL Azure に接続するためのサーバー名を入力します。  
  
**[データベース]**  
  
選択、入力または**参照**データベース名。  
  
> [!IMPORTANT]  
> アクセス用の SSMA は、SQL Azure で master データベースへの接続をサポートしていません。  
  
**ユーザー名**  
  
SSMA が SQL Azure データベースへの接続に使用するユーザー名を入力します。  
  
**Password**  
  
ユーザー名に対応するパスワードを入力します。  
  
**Encrypt**  
  
SSMA では、SQL Azure に暗号化された接続をお勧めします。  
  
## <a name="create-azure-database"></a>Azure のデータベースを作成します。  
新しい azure データベースを作成するには、次の手順に従います  
  
1.  SQL Azure ダイアログ ボックスに、Connect に表示される参照ボタンをクリックします  
  
2.  データベースが存在しない場合は、2 つのメニュー項目が表示されます。  
  
    1.  **(データベースが見つかりません)** は無効であるすべての時間が淡色表示になりますが  
  
    2.  **新しいデータベースの作成**常に有効になっています、SQL Azure アカウントに新しい azure データベースを作成するユーザーを有効にします。 このメニュー項目をクリックすると、次のように作成します。 データベース名とサイズで azure データベース ダイアログ ボックスがあります。  
  
3.  データベースの作成時に、これら 2 つのパラメーターは、入力として指定されます。  
  
    1.  **データベース名:** データベース名を入力します。  
  
    2.  **データベースのサイズ:** SQL Azure アカウントに作成する必要があるデータベースのサイズを選択します。  
  
