---
title: Azure SQL DB への接続 (アクセス先) |Microsoft Docs
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
ms.openlocfilehash: 0b26ddaef1373544e0df2fd9186cdf56fdafd801
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68040631"
---
# <a name="connect-to-azure-sql-db-accesstosql"></a>Azure SQL DB への接続 (アクセス先)
[SQL Azure への接続] ダイアログボックスを使用して、移行する SQL Azure データベースに接続します。  
  
このダイアログボックスにアクセスするには、[**ファイル**] メニューの [ **SQL Azure に接続**] を選択します。 以前に接続している場合、コマンドは**SQL Azure に再接続します。**  
  
## <a name="options"></a>オプション  
**サーバー名**  
  
SQL Azure に接続するためのサーバー名を選択または入力します。  
  
**[データベース]**  
  
データベース名を選択、入力、または**参照**します。  
  
> [!IMPORTANT]  
> SSMA for Access は、SQL Azure の master データベースへの接続をサポートしていません。  
  
**ユーザー名**  
  
SSMA が SQL Azure データベースへの接続に使用するユーザー名を入力します。  
  
**パスワード**  
  
入力されたユーザー名のパスワードを入力します。  
  
**暗号化**  
  
SSMA では、SQL Azure への暗号化接続を推奨しています。  
  
## <a name="create-azure-database"></a>Azure データベースの作成  
新しい azure データベースを作成するには、次の手順に従います。  
  
1.  [SQL Azure への接続] ダイアログボックスに表示されている [参照] ボタンをクリックします。  
  
2.  データベースが存在しない場合は、2つのメニュー項目が表示されます。  
  
    1.  **(データベースが見つかりません)** が無効化され、常にグレー表示になっている  
  
    2.  常に有効になっている**新しいデータベースを作成**し、ユーザーが SQL Azure アカウントで新しい azure データベースを作成できるようにします。 このメニュー項目をクリックすると、[azure データベースの作成] ダイアログボックスにデータベースの名前とサイズが表示されます。  
  
3.  データベースの作成時に、これらの2つのパラメーターは入力として指定されます。  
  
    1.  **データベース名:** データベース名を入力します。  
  
    2.  **データベースサイズ:** SQL Azure アカウントで作成する必要のあるデータベースのサイズを選択します。  
  
