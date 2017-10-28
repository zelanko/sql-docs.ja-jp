---
title: "SSMA の Sybase クライアント (SybaseToSQL) のインストール |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: e770c2f2-52b9-4471-a207-0d35df41399c
caps.latest.revision: 18
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: c08bd0a90cc7f5820f2f1e9481f2c58c3b12f131
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="installing-ssma--for-sybase-client-sybasetosql"></a>インストールの SSMA for Sybase クライアント (SybaseToSQL)
SSMA クライアントは、Sybase Adaptive Server Enterprise (ASE) データベース サーバーとのインスタンスへの接続に使用されるプログラム ファイルで構成されます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または ASE データベース オブジェクトに変換、Azure SQL DB[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB の構文にオブジェクトを読み込む[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB へのデータを移行してから、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQLDB です。  
  
このトピックでは、インストールの前提条件と SSMA をインストールするための指示を提供します。  
  
## <a name="prerequisites"></a>前提条件  
SSMA は ASE 11.9.2 またはそれ以降のバージョンとのすべてのエディションを使用するように設計された[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
SSMA をインストールする前に、コンピューターが、次の要件を満たしていることを確認してください。  
  
-   Windows 7 またはそれ以降のバージョンまたは Windows Server 2008 以降のバージョン。  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows インストーラー 3.1 以降。  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] .NET Framework バージョン 4.0 またはそれ以降のバージョン。 .NET Framework バージョン 4.0 で使用できる、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]製品メディア。 取得することも、 [.NET Framework Developer Center](http://go.microsoft.com/fwlink/?LinkId=48882)です。  
  
-   移行する、Sybase OLEDB/ADO.Net/ODBC プロバイダーとデータベースを含む Sybase ASE データベース サーバーに接続します。 プロバイダーは、Sybase ASE 製品メディアからインストールできます。 接続の詳細については、次を参照してください[Sybase ASE &#40; に接続する。SybaseToSQL &#41;](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md).  
  
-   アクセスおよびのターゲット インスタンスをホストするコンピューターに十分なアクセス許可[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB の場所はで移行するデータベース オブジェクトとデータ。 詳細については、次を参照してください[SQL Server &#40; に接続する。SybaseToSQL &#41;](../../ssma/sybase/connecting-to-sql-server-sybasetosql.md) / [Azure SQL DB &#40; に接続します。SybaseToSQL &#41;](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md).  
  
-   4 GB の RAM (推奨)。  
  
## <a name="installing-the-ssma-for-sybase-client"></a>Sybase クライアントに対して、SSMA をインストールします。  
SSMA は Web からダウンロードします。 最新バージョンをダウンロードするを参照してください。、 [SQL Server Migration Assistant のダウンロード ページ](http://aka.ms/ssmaforsybase)です。  
  
最新バージョンをダウンロードした後は、SSMA をインストールする前のインストール ファイルを抽出する必要があります。  
  
**SSMA クライアントをインストールするには**  
  
1.  SSMA for Sybase をダブルクリック *n*です。Install.exe、場所 *n* ビルド番号です。  
  
2.  [ようこそ] ページで、をクリックして**次**です。  
  
    インストールの前提条件がないとすると必要なコンポーネントをインストールする必要があります最初を示すメッセージが表示されます。 すべての前提条件がインストールされているし、インストール プログラムをもう一度実行していることを確認してください。  
  
3.  使用許諾契約書を読み取る。 同意する場合は、選択**ライセンス契約の条項に同意**、順にクリック**次**です。  
  
4.  セットアップの種類の選択 ページで、をクリックして**標準**です。  
  
5.  **[インストール]**をクリックします。  
  
> [!IMPORTANT]  
> 1.  新しいバージョンをインストールする前に、for Sybase SSMA のすべての以前のバージョンをアンインストールしてください。  
  
既定のインストール場所は C:\Program files \microsoft SQL Server Migration Assistant for Sybase です。  
  
SSMA のプログラム ファイルに加えてもにインストールする必要 SSMA for Sybase 拡張子 Pack[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 詳細については、次を参照してください[on SQL Server &#40; SSMA コンポーネントのインストール。SybaseToSQL &#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md).  
  
## <a name="see-also"></a>参照  
[SQL Server &#40; SSMA コンポーネントをインストールします。SybaseToSQL &#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)  
[SQL Server - Azure SQL DB &#40; への Sybase ASE データベースの移行SybaseToSQL &#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  

