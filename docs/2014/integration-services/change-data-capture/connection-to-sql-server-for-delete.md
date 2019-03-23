---
title: 削除用の SQLServer への接続 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 030b10c2-6b88-4c2c-bf67-22994be25a60
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: acb755f8cc1e425e38714013511948f7b5b4c580
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2019
ms.locfileid: "58392940"
---
# <a name="connection-to-sql-server-for-delete"></a>削除用の SQLServer への接続
  MSXDBCDC データベースに対する書き込み権限を含むデータベース ロール (**db_owner** ロールなど) を持たないログインが Oracle CDC インスタンスの削除を試みると、[SQL Server への接続] ダイアログ ボックスが表示されます。  
  
 Oracle CDC インスタンスを削除するには、このダイアログ ボックスに、 **db_owner** データベース ロールなど、MSXDBCDC データベースに対する書き込み権限を持つログインの資格情報を入力する必要があります。  
  
 [SQL Server への接続] ダイアログ ボックスに次の情報を入力します。  
  
 **[サーバー名]**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が存在するサーバーの名前を入力します。  
  
 **[認証]**  
 次のいずれかを選択します。  
  
-   **[Windows 認証]**  
  
-   **SQL Server 認証**:このオプションを選択する場合は入力、**ログイン**と**パスワード**内のユーザーに対して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に接続しています。  
  
 **[オプション]**  
 矢印をクリックして、構成するオプションを表示します。 これらのオプションを既定値のままにすることもできます。 使用可能なオプションは次のとおりです。  
  
-   **接続タイムアウト**:プログラムが待機する時間 (秒) を入力、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]接続がタイムアウト エラーを生成する前に確立されています。 既定値は **15**です。  
  
-   **実行タイムアウト**:プログラムが SQL コマンドの実行がタイムアウト エラーを生成する前に完了するを待機する秒単位で時間を入力します。 既定値は、 **30**です。  
  
-   **接続を暗号化**:選択**暗号化接続**ことを確認する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]確立されているプライバシーを保証するために暗号化された接続。  
  
-   **[詳細設定]**:必要に応じて、 **[詳細設定]** をクリックし、[高度な接続プロパティ] ダイアログ ボックスに追加の接続プロパティを入力します。  
  
## <a name="see-also"></a>参照  
 [CDC Service で使用する SQL Server 接続に必要な権限](sql-server-connection-required-permissions-for-the-cdc-service.md)  
  
  
