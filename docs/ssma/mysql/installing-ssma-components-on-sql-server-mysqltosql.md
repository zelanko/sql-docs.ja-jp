---
title: SQL Server での SSMA コンポーネントのインストール (MySQLToSql) |Microsoft Docs
description: Ssma 拡張パックと MySQL プロバイダーを含む SSMA での MySQL データベースの変換をサポートするために、SQL Server を実行するサーバーにコンポーネントをインストールします。
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- SSMA extension pack, Installation
ms.assetid: 6772d0c5-258f-4d7b-afb0-b5f810e71af1
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 502f42a961cfbd64b0dcd6ac6c6867d0cdcf501a
ms.sourcegitcommit: 59cda5a481cfdb4268b2744edc341172e53dede4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "84293789"
---
# <a name="installing-ssma-components-on-sql-server-mysqltosql"></a>SQL Server での SSMA コンポーネントのインストール (MySQLToSql)
SSMA のインストールに加えて、を実行しているコンピューターにコンポーネントをインストールする必要もあり [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 これらのコンポーネントには、データの移行をサポートする SSMA 拡張パックと、サーバーとサーバー間の接続を有効にする MySQL プロバイダーが含まれます。  
  
## <a name="ssma-for-mysql-extension-pack"></a>SSMA for MySQL Extension Pack  
SSMA 拡張パックは、指定されたインスタンスにデータベース**sysdb**を追加し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 このデータベースには、データの移行に必要なテーブルとストアドプロシージャが含まれています。  
  
また、データをに移行するときに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、サーバー側のデータ移行エンジンを使用してデータを移行するときに、ssma によってエージェントジョブが作成され [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
### <a name="prerequisites"></a>前提条件  
SSMA for MySQL サーバーコンポーネントをにインストールする前に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、コンピューターが次の要件を満たしていることを確認してください。  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows インストーラー3.1 以降のバージョン。  
  
-   MySQL クライアントプロバイダーと、移行する MySQL データベースへの接続。 プロバイダーは、MySQL 製品メディアまたは MySQL Web サイトからインストールできます。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インストール中に Browser サービスが実行されている必要があります。 これは、セットアップウィザードでのインスタンスの一覧を設定するために使用され [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 インストール後に Browser サービスを無効にすることができ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
    > [!NOTE]  
    > [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Browser サービスが実行されていても、セットアップにインスタンスの一覧が表示されない場合は、UDP ポート1434のブロックを解除する必要があります。 Windows ファイアウォールを使用して、一時的にポートのブロックを解除することも、Windows ファイアウォールを一時的に無効にすることもできます。 また、ウイルス対策ソフトウェアを一時的に無効にすることが必要になる場合もあります。 インストール後に、ファイアウォールとウイルス対策ソフトウェアが有効になっていることを確認してください。  
  
### <a name="installing-the-extension-pack"></a>拡張機能パックのインストール  
にデータを移行する前に、いつでも拡張機能パックをインストールでき [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
> [!IMPORTANT]  
> 拡張機能パックをインストールするには、のインスタンスの**sysadmin**サーバーロールのメンバーである必要があり [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
**拡張機能パックをインストールするには**  
  
1.  SSMA for MySQL Extension Pack をコピーします。*n*.Install.exe。 *n*はビルド番号であり、を実行しているコンピューターに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] なります。  
  
2.  SSMA for MySQL Extension Pack をダブルクリックします。*n*.Install.exe。  
  
3.  [ようこそ] ダイアログボックスで、[**次へ**] をクリックします。  
  
4.  [使用許諾契約書] ダイアログボックスで、使用許諾契約書を確認します。 同意する場合は、[**使用許諾契約書に同意し**ます] チェックボックスをオンにして、[**次へ**] をクリックします。  
  
5.  [セットアップの種類の選択] ダイアログボックスで、[**標準**] をクリックします。  
  
6.  [インストールの準備完了] ダイアログボックスで、[**インストール**] をクリックします。  
  
7.  [インストールの最初の手順を完了しました] ダイアログボックスで、[**次へ**] をクリックします。  
  
    新しいダイアログボックスが表示されます。このダイアログボックスで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 拡張機能パックのインストール用のインスタンスを選択します。  
  
8.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]MySQL スキーマを移行するのインスタンスを選択し、[**次へ**] をクリックします。  
  
    既定のインスタンスには、コンピューターと同じ名前が付けられています。 名前付きインスタンスの後には、円記号とインスタンス名が続きます。  
  
9. [接続] ダイアログボックスで、認証方法を選択し、[**次へ**] をクリックします。  
  
    Windows 認証では、Windows 資格情報を使用してのインスタンスにログオンしようとし [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 [認証] を選択した場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログイン名とパスワードを入力する必要があり [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
10. 次のダイアログボックスで、[ **Install Utilities Database** *n*] を選択します。ここで、 *n*はバージョン番号です。次に、[**次へ**] をクリックします。  
  
    **Sysdb**データベースは、(サーバー側のデータ移行エンジンを使用して) データ移行に必要なテーブルとストアドプロシージャがデータベースに作成されて作成されます。  
  
11. の別のインスタンスにユーティリティをインストールするには、[はい] を選択し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [**次へ**] をクリックします。 **Yes** または、ウィザードを終了するには、[**いいえ**] をクリックします。  
  
## <a name="see-also"></a>参照  
[SSMA for MySQL クライアント &#40;MySQLToSQL&#41;のインストール](../../ssma/mysql/installing-ssma-for-mysql-client-mysqltosql.md)  
[MySQL データベースの SQL Server への移行-Azure SQL DB &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
