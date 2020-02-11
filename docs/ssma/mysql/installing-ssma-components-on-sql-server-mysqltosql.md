---
title: SQL Server での SSMA コンポーネントのインストール (MySQLToSql) |Microsoft Docs
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
ms.openlocfilehash: 64040f4a0caf8253e6d6e8a3b00ff21e0cebe6d9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68075348"
---
# <a name="installing-ssma-components-on-sql-server-mysqltosql"></a>SQL Server での SSMA コンポーネントのインストール (MySQLToSql)
SSMA のインストールに加えて、を実行[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]しているコンピューターにコンポーネントをインストールする必要もあります。 これらのコンポーネントには、データの移行をサポートする SSMA 拡張パックと、サーバーとサーバー間の接続を有効にする MySQL プロバイダーが含まれます。  
  
## <a name="ssma-for-mysql-extension-pack"></a>SSMA for MySQL Extension Pack  
SSMA 拡張パックは、指定されたインスタンスにデータベース**sysdb**を追加[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 このデータベースには、データの移行に必要なテーブルとストアドプロシージャが含まれています。  
  
また、データをに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]移行するときに、サーバー [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]側のデータ移行エンジンを使用してデータを移行するときに、ssma によってエージェントジョブが作成されます。  
  
### <a name="prerequisites"></a>前提条件  
SSMA for MySQL サーバーコンポーネントをに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インストールする前に、コンピューターが次の要件を満たしていることを確認してください。  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows インストーラー3.1 以降のバージョン。  
  
-   MySQL クライアントプロバイダーと、移行する MySQL データベースへの接続。 プロバイダーは、MySQL 製品メディアまたは MySQL Web サイトからインストールできます。  
  
-   インストール[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中に Browser サービスが実行されている必要があります。 これは、セットアップウィザードでの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスの一覧を設定するために使用されます。 インストール後に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスを無効にすることができます。  
  
    > [!NOTE]  
    > [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスが実行されていても、セットアップにインスタンスの一覧が表示されない場合は、UDP ポート1434のブロックを解除する必要があります。 Windows ファイアウォールを使用して、一時的にポートのブロックを解除することも、Windows ファイアウォールを一時的に無効にすることもできます。 また、ウイルス対策ソフトウェアを一時的に無効にすることが必要になる場合もあります。 インストール後に、ファイアウォールとウイルス対策ソフトウェアが有効になっていることを確認してください。  
  
### <a name="installing-the-extension-pack"></a>拡張機能パックのインストール  
にデータを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]移行する前に、いつでも拡張機能パックをインストールできます。  
  
> [!IMPORTANT]  
> 拡張機能パックをインストールするには、の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスの**sysadmin**サーバーロールのメンバーである必要があります。  
  
**拡張機能パックをインストールするには**  
  
1.  SSMA for MySQL Extension Pack をコピーします。*n*。を実行[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]しているコンピューターに、.exe ( *n*はビルド番号) をインストールします。  
  
2.  SSMA for MySQL Extension Pack をダブルクリックします。*n*。.Exe をインストールします。  
  
3.  [ようこそ] ダイアログボックスで、[**次へ**] をクリックします。  
  
4.  [使用許諾契約書] ダイアログボックスで、使用許諾契約書を確認します。 同意する場合は、[**使用許諾契約書に同意し**ます] チェックボックスをオンにして、[**次へ**] をクリックします。  
  
5.  [セットアップの種類の選択] ダイアログボックスで、[**標準**] をクリックします。  
  
6.  [インストールの準備完了] ダイアログボックスで、[**インストール**] をクリックします。  
  
7.  [インストールの最初の手順を完了しました] ダイアログボックスで、[**次へ**] をクリックします。  
  
    新しいダイアログボックスが表示されます。このダイアログボックスで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]拡張機能パックのインストール用のインスタンスを選択します。  
  
8.  MySQL スキーマを移行[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]するのインスタンスを選択し、[**次へ**] をクリックします。  
  
    既定のインスタンスには、コンピューターと同じ名前が付けられています。 名前付きインスタンスの後には、円記号とインスタンス名が続きます。  
  
9. [接続] ダイアログボックスで、認証方法を選択し、[**次へ**] をクリックします。  
  
    Windows 認証では、Windows 資格情報を使用しての[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスにログオンしようとします。 [認証] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を選択した場合は[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、ログイン名とパスワードを入力する必要があります。  
  
10. 次のダイアログボックスで、[ **Install Utilities Database** *n*] を選択します。ここで、 *n*はバージョン番号です。次に、[**次へ**] をクリックします。  
  
    **Sysdb**データベースは、(サーバー側のデータ移行エンジンを使用して) データ移行に必要なテーブルとストアドプロシージャがデータベースに作成されて作成されます。  
  
11. の別の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスにユーティリティをインストールするには、[**はい**] を選択し、[**次へ**] をクリックします。 または、ウィザードを終了するには、[**いいえ**] をクリックします。  
  
## <a name="see-also"></a>参照  
[SSMA for MySQL クライアント &#40;MySQLToSQL&#41;のインストール](../../ssma/mysql/installing-ssma-for-mysql-client-mysqltosql.md)  
[MySQL データベースの SQL Server への移行-Azure SQL DB &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
