---
title: Azure SQL DB への接続 (SybaseToSQL) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 96538007-1099-40c8-9902-edd07c5620ee
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 68fbac69959d423477750a69bb6e5b06ab62af2b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68083471"
---
# <a name="connect-to-azure-sql-db--sybasetosql"></a>Azure SQL DB への接続 (SybaseToSQL)
[Azure SQL DB への接続] ダイアログボックスを使用して、移行する Azure SQL DB データベースに接続します。  
  
このダイアログボックスにアクセスするには、[**ファイル**] メニューの [ **Azure SQL DB への接続**] をクリックします。 以前に接続している場合は、コマンドが**AZURE SQL DB に再接続されます。**  
  
## <a name="options"></a>オプション  
**サーバー名**  
  
Azure SQL DB に接続するためのサーバー名を選択または入力します。  
  
**[データベース]**  
  
データベース名を選択、入力、または**参照**します。  
  
> [!IMPORTANT]  
> SSMA for Sybase は、Azure SQL DB の master データベースへの接続をサポートしていません。  
  
**ユーザー名**  
  
SSMA が Azure SQL DB データベースへの接続に使用するユーザー名を入力します  
  
**パスワード**  
  
入力されたユーザー名のパスワードを入力します。  
  
**暗号化**  
  
SSMA では、Azure SQL DB への暗号化接続を推奨しています。  
  
## <a name="create-azure-database"></a>Azure データベースの作成  
Azure SQL DB アカウントにデータベースがない場合は、最初のデータベースを作成できます。  
  
初めて新しいデータベースを作成するには、次の手順に従います。  
  
1.  [Azure SQL DB への接続] ダイアログボックスに表示されている [参照] ボタンをクリックします。  
  
2.  データベースが存在しない場合は、次の2つのメニュー項目が表示されます。  
  
    1.  **(データベースが見つかりません)** が無効化され、常にグレー表示になっている  
  
    2.  **新しいデータベースを作成**します。これは、AZURE SQL DB アカウントにデータベースが存在しない場合にのみ有効になります。 このメニュー項目をクリックすると、[Azure データベースの作成] ダイアログボックスにデータベースの名前とサイズが表示されます。  
  
3.  データベースの作成時には、次の2つのパラメーターが入力として指定されます。  
  
    1.  **データベース名:** データベース名を入力します。  
  
    2.  **データベースサイズ:** Azure SQL DB アカウントで作成する必要のあるデータベースのサイズを選択します。  
  
