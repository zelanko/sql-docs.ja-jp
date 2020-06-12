---
title: SSMA for MySQL クライアントのインストール (MySQLToSQL) |Microsoft Docs
description: SQL Server Migration Assistant (SSMA) for MySQL クライアントのインストールの前提条件と、のインストール方法について説明します。
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Installing client,Licensing
ms.assetid: ede3128c-370d-45a5-a815-3d94eecaea30
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: bf1a3c8c5a01bb2553f773d5b650805667c116a3
ms.sourcegitcommit: 59cda5a481cfdb4268b2744edc341172e53dede4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "84293899"
---
# <a name="installing-ssma-for-mysql-client-mysqltosql"></a>SSMA for MySQL クライアントのインストール (MySQLToSQL)
SSMA for MySQL クライアントは、次のタスクを実行するプログラムファイルで構成されています。  
  
-   MySQL データベースに接続します。  
  
-   のインスタンス [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または SQL Azure に接続します。  
  
-   MySQL データベースオブジェクトを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または SQL Azure オブジェクトに変換します。  
  
-   オブジェクトを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または SQL Azure に読み込みます。  
  
-   または SQL Azure にデータを移行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] します。  
  
このトピックでは、SSMA for MySQL クライアントをインストールするための前提条件と手順について説明します。  
  
## <a name="prerequisites"></a>前提条件  
SSMA for MySQL は、MySQL 4.1 以降のバージョンと、SQL Server 2005、SQL Server 2008、SQL Server 2012、SQL Server 2014、SQL Server 2016、SQL Server 2017、Azure SQL DB のすべてのエディションで動作するように設計されています。  
  
SSMA をインストールする前に、コンピューターが次の要件を満たしていることを確認してください。  
  
-   Windows 7 以降のバージョン、または Windows Server 2008 以降のバージョン。  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows インストーラー3.1 以降のバージョン。  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] バージョン4.0 以降のバージョン。 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)]バージョン4.0 は、SQL Server 製品メディアにあります。 また、 [.NET Framework デベロッパーセンター](https://go.microsoft.com/fwlink/?LinkId=48882)から入手することもできます。  
  
-   MySQL ODBC 5.1 ドライバーと、移行する MySQL データベースへの接続。 Mysql は、MySQL Web サイトからインストールできます。 接続の詳細については、「 [MySQL への接続 &#40;MySQLToSQL](../../ssma/mysql/connecting-to-mysql-mysqltosql.md) 」を参照してください&#41;  
  
-   にアクセスし、データベースオブジェクトとデータを移行する SQL Server のターゲットインスタンスをホストするコンピューターに対して十分なアクセス許可を付与します。 詳細については、「 [SQL Server &#40;MySQLToSQL への接続](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)」を参照してください&#41;  
  
-   SQL Azure のプロジェクトの場合は、データベースオブジェクトとデータを移行する Azure SQL DB インスタンスへのアクセス権と十分なアクセス許可を付与します。 詳細については、「 [AZURE SQL DB への接続 &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-azure-sql-db-mysqltosql.md)」を参照してください。  
  
-   4 GB の RAM を推奨します。  
  
## <a name="installing-ssma-for-mysql-client"></a>SSMA for MySQL クライアントのインストール  
SSMA は Web からダウンロードできます。 最新バージョンをダウンロードするには、 [SQL Server Migration Assistant のダウンロードページ](https://aka.ms/ssmaformysql)を参照してください。  
  
最新バージョンをダウンロードした後は、SSMA をインストールする前に、インストールファイルを抽出する必要があります。  
  
**SSMA クライアントをインストールするには**  
  
1.  SSMA for MySQL *n*.Install.exe をダブルクリックします。ここで、 *n*はビルド番号です。  
  
2.  [ようこそ] ページで **[次へ]** をクリックします。  
  
    前提条件がインストールされていない場合は、必要なコンポーネントを最初にインストールする必要があることを示すメッセージが表示されます。 インストールプログラムを再実行する前に、すべての前提条件がインストールされていることを確認してください。  
  
3.  使用許諾契約書を確認します。 同意する場合は、[**使用許諾契約書に同意**します] を選択し、[**次へ**] をクリックします。  
  
4.  [セットアップの種類の選択] ページで、[**標準**] をクリックします。  
  
5.  **[インストール]** をクリックします。  
  
> [!IMPORTANT]  
> 1.  新しいバージョンをインストールする前に、SSMA for MySQL の以前のバージョンをすべてアンインストールしてください。  
  
既定のインストール場所は、MySQL の場合は C:\Program の SQL Server Migration Assistant です。  
  
64ビットの Windows コンピューターでは、製品は C:\ Microsoft SQL Server Migration Assistant for MySQL にインストールされます。  
  
## <a name="see-also"></a>参照  
[MySQL データベースの SQL Server への移行-Azure SQL DB &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
