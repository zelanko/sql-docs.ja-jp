---
title: "SQL Server (MySQLToSql) へ SSMA コンポーネントのインストール |Microsoft ドキュメント"
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
helpviewer_keywords:
- SSMA extension pack, Installation
ms.assetid: 6772d0c5-258f-4d7b-afb0-b5f810e71af1
caps.latest.revision: 9
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 9544fb62402871b9a93284df88e0082f62fec582
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="installing-ssma-components-on-sql-server-mysqltosql"></a>SQL server (MySQLToSql) SSMA コンポーネントのインストール
SSMA をインストールするだけでなくする必要がありますコンポーネントもインストールを実行しているコンピューターで[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 これらのコンポーネントには、データの移行、およびサーバーからサーバーへの接続を有効にする MySQL プロバイダーをサポートする、SSMA 拡張機能パックが含まれます。  
  
## <a name="ssma-for-mysql-extension-pack"></a>SSMA for MySQL の拡張機能パック  
SSMA の拡張機能パックは、データベースを追加**sysdb**のインスタンスを指定する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 このデータベースには、テーブルとデータを移行するために必要なストアド プロシージャが含まれています。  
  
データを移行する場合にも、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、SSMA 作成[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]サーバー側のデータ移行のエンジンがデータを移行するために使用されるときに、エージェント ジョブ。  
  
### <a name="prerequisites"></a>前提条件  
SSMA for MySQL server のコンポーネントをインストールする前に[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]コンピューターが、次の要件を満たしていることを確認します。  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows インストーラー 3.1 以降。  
  
-   MySQL クライアント プロバイダー、および移行する MySQL データベースへの接続。 プロバイダーは、MySQL 製品メディアまたは MySQL の Web サイトからインストールできます。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Browser サービスをインストール中に実行する必要があります。 インスタンスの一覧を設定するのに使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]セットアップ ウィザードでします。 無効にすることができます、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Browser サービスのインストール後にします。  
  
    > [!NOTE]  
    > 場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Browser サービスが実行されているが、まだ、セットアップ時にインスタンスの一覧表示されない、UDP ポート 1434 のブロックを解除する必要があります。 Windows ファイアウォールを使用するには、ポートに一時的にブロックを解除するか、Windows ファイアウォールを一時的に無効にすることができます。 ウイルス対策ソフトウェアを一時的に無効にすることもあります。 インストール後にファイアウォールとウイルス対策ソフトウェアを有効にすることを確認してください。  
  
### <a name="installing-the-extension-pack"></a>拡張機能パックをインストールします。  
拡張機能パックをインストールするとデータを移行する前にいつでも[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
> [!IMPORTANT]  
> 拡張機能パックをインストールするには、メンバーである、 **sysadmin**サーバーの役割のインスタンスを[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
**拡張機能パックをインストールするには**  
  
1.  MySQL 拡張機能パックには、SSMA をコピーします。*n*.Install.exe、場所 *n* を実行しているコンピューターに、ビルド番号は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
2.  MySQL 拡張機能パックには、SSMA をダブルクリックします。*n*.Install.exe です。  
  
3.  [ようこそ] ダイアログ ボックスで、をクリックして**次**です。  
  
4.  [使用許諾契約書] ダイアログ ボックスで、使用許諾契約書を読み取る。 同意する場合は、選択、**ライセンス契約の条項に同意**チェック ボックスをクリックして**次**です。  
  
5.  セットアップの種類の選択 ダイアログ ボックスで、をクリックして**標準**です。  
  
6.  準備完了のインストール ダイアログ ボックスで、をクリックして**インストール**です。  
  
7.  最初のステップのインストール ダイアログ ボックスの完了 で、をクリックして**次**です。  
  
    インスタンスを選択して、新しいダイアログ ボックスが表示されます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]拡張機能パックをインストールするためです。  
  
8.  インスタンスを選択して[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、MySQL スキーマを移行し、をクリックして**次**です。  
  
    既定のインスタンスには、コンピューターと同じ名前があります。 名前付きインスタンスの後に、円記号とインスタンス名が指定されます。  
  
9. [接続] ダイアログ ボックスで、認証方法を選択し、をクリックして**次**です。  
  
    Windows 認証は、Windows 資格情報を使用してのインスタンスにログオンしよう[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 選択した場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]を入力する必要があります、認証、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ログイン名とパスワード。  
  
10. [次へ] ダイアログ ボックスで、次のように選択します。**ユーティリティ データベースのインストール**  *n*ここで、  *n* バージョン番号は、[] をクリック**次**です。  
  
    **Sysdb**テーブルを持つデータベースが作成され (エンジンを使用してサーバー側のデータの移行) データの移行に必要なストアド プロシージャは、そのデータベースに作成されます。  
  
11. 別のインスタンスにユーティリティをインストールする[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **[はい]**、順にクリック**[次へ]**です。 またはをクリックしてウィザードを終了するには、**いいえ**です。  
  
## <a name="see-also"></a>参照  
[SSMA の MySQL クライアント &#40; のインストールMySQLToSQL &#41;](../../ssma/mysql/installing-ssma-for-mysql-client-mysqltosql.md)  
[SQL Server - Azure SQL DB &#40; への MySQL データベースの移行MySQLToSql &#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  

