---
title: "MySQL (MySQLToSQL) への接続 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 94099d01-ab19-4d58-a172-340c86b4a0f3
caps.latest.revision: 9
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: eb5ded86bf30a942aaece3f7d1404df781c24112
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="connect-to-mysql-mysqltosql"></a>MySQL (MySQLToSQL) への接続します。
使用して、 **MySQL への接続**を移行する MySQL データベースに接続する ダイアログ ボックス。  
  
このダイアログ ボックスにアクセスする、**ファイル**メニューの  **MySQL への接続**です。 以前接続した場合、コマンドは**MySQL への再接続**です。  
  
## <a name="options"></a>オプション  
**プロバイダー**  
  
使用可能な MySQL プロバイダーは、MySQL 5.1 Odbc (信頼関係) です。  
  
**モード**  
  
既定のモードは、標準モードです。 標準モードでは、入力または、MySQL、サーバー名、サーバーのポート、ユーザー名およびパスワードの値を選択します。  
  
**サーバー名**  
  
MySQL サーバーの名前を入力します。 標準モードのオプションです。  
  
**[サーバー ポート]**  
  
サーバーのポートを入力します。 既定のサーバーのポートは、3306 です。 標準モードのオプションです。  
  
**ユーザー名**  
  
SSMA は、MySQL データベースへの接続に使用されるユーザー名を入力します。  
  
**Password**  
  
ユーザー名に対応するパスワードを入力します。  
  
**SSL**  
  
MySQL に安全に接続する場合は、利用の Secure Socket Layer (SSL) をチェックして、 **SSL**チェック ボックスをオンします。  
  
**構成します。**  
  
MySQL Secure Socket Layer (SSL) を介してへの接続を構成するオプションを提供します。  
  
> [!NOTE]  
> 有効にする**構成**に SSL を設定する必要があります**True**です。  
  
[構成] ボタンをクリックすると、ダイアログ ボックスが表示されます。 MySQL データベースを次の 3 つの証明書ファイル] ダイアログ ボックス内に存在するパスに接続する必要があります中に暗号化を使用するには、[プライバシー強化メール証明書 (PEM)] に定義されています。  
  
-   **SSL 証明機関:**信頼の SSL の Ca の一覧で、ファイルへのパスを指定します。  
  
-   **SSL 証明書:**をセキュリティで保護された接続の確立に使用する SSL 証明書ファイルの名前を指定します。  
  
-   **SSL キー:**セキュリティで保護された接続の確立に使用する SSL のキー ファイルの名前を指定します。  
  
> [!NOTE]  
> -   **OK**必要な情報が提供されているときにボタンが有効にします。 ファイルのパスのいずれかの情報が有効でない場合は、[OK] ボタンが無効になります。  
> -   **キャンセル**ボタンがダイアログ ボックスを閉じますと**をオフに**SSL オプションで、メイン接続フォーム。  
  

