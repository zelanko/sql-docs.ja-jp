---
title: "SSMA の MySQL クライアント (MySQLToSQL) のインストール |Microsoft ドキュメント"
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
- Installing client,Licensing
ms.assetid: ede3128c-370d-45a5-a815-3d94eecaea30
caps.latest.revision: 22
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: eafef1f4a4f16f704b76b31aa77d3c93f84d5821
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="installing-ssma-for-mysql-client-mysqltosql"></a>インストールの SSMA for MySQL クライアント (MySQLToSQL)
SSMA for MySQL クライアントは、次のタスクを実行するプログラム ファイルで構成されます。  
  
-   MySQL データベースに接続します。  
  
-   インスタンスに接続[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。  
  
-   MySQL のデータベース オブジェクトへの変換、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure オブジェクト。  
  
-   オブジェクトを読み込む[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。  
  
-   データを移行して[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。  
  
このトピックでは、インストールの前提条件と SSMA の MySQL クライアントのインストール手順を提供します。  
  
## <a name="prerequisites"></a>前提条件  
SSMA for MySQL は MySQL 4.1 またはそれ以降のバージョンとすべてのエディションの SQL Server 2005、SQL Server 2008、SQL Server 2012、SQL Server 2014、SQL Server 2016 および Azure SQL DB を使用するよう設計されています。  
  
SSMA をインストールする前に、コンピューターが、次の要件を満たしていることを確認してください。  
  
-   Windows 7 またはそれ以降のバージョンまたは Windows Server 2008 以降のバージョン。  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows インストーラー 3.1 以降。  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)]バージョン 4.0 またはそれ以降のバージョン。 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)]バージョン 4.0 は、SQL Server の製品メディアで使用します。 取得することも、 [.NET Framework Developer Center](http://go.microsoft.com/fwlink/?LinkId=48882)です。  
  
-   MySQL 5.1 Odbc と移行先の MySQL データベースへの接続。 MySQL の Web サイトから MySQL をインストールすることができます。 接続の詳細については、次を参照してください[MySQL &#40; に接続する。MySQLToSQL &#41;](../../ssma/mysql/connecting-to-mysql-mysqltosql.md)  
  
-   アクセスと SQL Server の場所はで移行するデータベース オブジェクトとデータのターゲット インスタンスをホストするコンピューターに十分なアクセス許可。 詳細については、次を参照してください[SQL Server &#40; に接続する。MySQLToSQL &#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
  
-   SQL Azure プロジェクトの場合へのアクセスと Azure SQL DB がする移行のインスタンスに十分なアクセス許可はデータベース オブジェクトとデータになります。 詳細については、次を参照してください[Azure SQL DB &#40; に接続する。MySQLToSQL &#41;](../../ssma/mysql/connecting-to-azure-sql-db-mysqltosql.md).  
  
-   4 GB の RAM (推奨)。  
  
## <a name="installing-ssma-for-mysql-client"></a>SSMA の MySQL クライアントのインストール  
SSMA は Web からダウンロードします。 最新バージョンをダウンロードするを参照してください。、 [SQL Server Migration Assistant のダウンロード ページ](http://aka.ms/ssmaformysql)です。  
  
最新バージョンをダウンロードした後は、SSMA をインストールする前に、インストール ファイルを抽出する必要があります。  
  
**SSMA クライアントをインストールするには**  
  
1.  SSMA for MySQL をダブルクリック *n*です。Install.exe、場所 *n* ビルド番号です。  
  
2.  [ようこそ] ページで、をクリックして**次**です。  
  
    前提条件がインストールされていない場合は、必要なコンポーネントをインストールする必要があります最初を示すメッセージが表示されます。 インストール プログラムをもう一度実行する前にすべての前提条件をインストールしてあることを確認します。  
  
3.  使用許諾契約書を読み取る。 同意する場合は、選択**ライセンス契約の条項に同意**、順にクリック**次**です。  
  
4.  セットアップの種類の選択 ページで、をクリックして**標準**です。  
  
5.  **[インストール]**をクリックします。  
  
> [!IMPORTANT]  
> 1.  新しいバージョンをインストールする前に、mysql SSMA のすべての以前のバージョンをアンインストールしてください。  
  
既定のインストール場所は C:\Program files \microsoft SQL Server Migration Assistant for MySQL です。  
  
64 ビットの Windows コンピューターで、製品がインストールされてで C:\Microsoft SQL Server Migration Assistant for MySQL です。  
  
## <a name="see-also"></a>参照  
[SQL Server - Azure SQL DB &#40; への MySQL データベースの移行MySQLToSql &#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  

