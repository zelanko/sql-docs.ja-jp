---
title: "SSMA の Oracle クライアント (OracleToSQL) のインストール |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-oracle
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Licensing SSMA
ms.assetid: d5d4903d-e296-4bbf-8780-63674c4d62d5
caps.latest.revision: "19"
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: On Demand
ms.openlocfilehash: 90e1f2b745ef0a093fb7a5b2ebf662aa969154f1
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="installing-ssma-for-oracle-client-oracletosql"></a>SSMA の Oracle クライアント (OracleToSQL) のインストール
SSMA クライアントは、次のタスクを実行するプログラム ファイルで構成されます。  
  
-   Oracle データベースに接続します。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] のインスタンスに接続する。  
  
-   Oracle データベース オブジェクトに変換[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]構文です。  
  
-   オブジェクトを読み込む[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]します。  
  
-   データを移行して[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
このトピックでは、インストールの前提条件と SSMA をインストールするための指示を提供します。  
  
## <a name="prerequisites"></a>Prerequisites  
SSMA は、Oracle 9、またはそれ以降のバージョンとのすべてのエディションを使用するように設計された[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
SSMA をインストールする前に、コンピューターが、次の要件を満たしていることを確認してください。  
  
-   Windows 7 またはそれ以降のバージョンまたは Windows Server 2008 以降のバージョン。  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows インストーラー 3.1 以降。  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)]バージョン 4.0 またはそれ以降のバージョン。 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)]バージョン 4.0 は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]製品メディア。 取得することも、 [.NET Framework Developer Center](http://go.microsoft.com/fwlink/?LinkId=48882)です。  
  
-   Oracle クライアント 9.0 または以降のバージョンとを移行する Oracle データベースへの接続。 Oracle クライアント バージョンは、バージョンと同じ、または Oracle データベースのバージョンより新しいバージョンにする必要があります。  
  
    Oracle 製品メディアまたは Oracle Web サイトからは、Oracle クライアントをインストールすることができます。 接続の詳細については、次を参照してください。 [Oracle データベース &#40;OracleToSQL&#41; への接続](../../ssma/oracle/connecting-to-oracle-database-oracletosql.md)です。  
  
-   アクセスおよびのターゲット インスタンスをホストするコンピューターに十分なアクセス許可[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB の場所はで移行するデータベース オブジェクトとデータ。 詳細については、次を参照してください。 [SQL Server &#40;OracleToSQL&#41; への接続](../../ssma/oracle/connecting-to-sql-server-oracletosql.md)です。  
  
-   4 GB の RAM (推奨)。  
  
## <a name="installing-the-ssma-for-oracle-client"></a>SSMA の Oracle クライアントのインストール  
SSMA は Web からダウンロードします。 最新バージョンをダウンロードするを参照してください。、 [SQL Server Migration Assistant のダウンロード ページ](http://aka.ms/ssmafororacle)です。  
  
最新バージョンをダウンロードした後は、SSMA をインストールする前のインストール ファイルを抽出する必要があります。  
  
**SSMA クライアントをインストールするには**  
  
1.  SSMA for Oracle をダブルクリック *n*です。Install.exe、場所 *n* ビルド番号です。  
  
2.  [ようこそ] ページで、をクリックして**次**です。  
  
    インストールの前提条件がないとすると必要なコンポーネントをインストールする必要があります最初を示すメッセージが表示されます。 すべての前提条件がインストールされているし、インストール プログラムをもう一度実行していることを確認してください。  
  
3.  使用許諾契約書を読み取る。 同意する場合は、選択**ライセンス契約の条項に同意**、順にクリック**次**です。  
  
4.  セットアップの種類の選択 ページで、をクリックして**標準**です。  
  
5.  **[インストール]**をクリックします。  
  
> [!IMPORTANT]  
> 1.  SSMA for Oracle のすべての以前のバージョンを新しいバージョンをインストールする前にアンインストールしてください。  
  
既定のインストール場所は C:\Program files \microsoft SQL Server Migration Assistant for Oracle です。  
  
SSMA のプログラム ファイルに加えてもにインストールする必要 SSMA for Oracle の拡張機能パック[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 詳細については、次を参照してください。 [SQL Server &#40;OracleToSQL&#41; SSMA コンポーネントのインストール中](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md)です。  
  
## <a name="see-also"></a>参照  
[SQL Server &#40;OracleToSQL&#41; SSMA コンポーネントをインストールします。](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md)  
[SQL Server &#40;OracleToSQL&#41; への Oracle データベースの移行](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
