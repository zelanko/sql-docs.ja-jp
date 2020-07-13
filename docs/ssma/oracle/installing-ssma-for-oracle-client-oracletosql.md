---
title: SSMA for Oracle クライアントのインストール (OracleToSQL) |Microsoft Docs
description: Oracle クライアント用の SQL Server Migration Assistant (SSMA) のインストールの前提条件と、のインストール方法について説明します。
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Licensing SSMA
ms.assetid: d5d4903d-e296-4bbf-8780-63674c4d62d5
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: be5f48508c44dc456c2d19e1ff1eba985b982111
ms.sourcegitcommit: 59cda5a481cfdb4268b2744edc341172e53dede4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "84293919"
---
# <a name="installing-ssma-for-oracle-client-oracletosql"></a>SSMA for Oracle クライアントのインストール (OracleToSQL)
SSMA クライアントは、次のタスクを実行するプログラムファイルで構成されています。  
  
-   Oracle データベースに接続します。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続する。  
  
-   Oracle データベースオブジェクトを構文に変換 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] します。  
  
-   オブジェクトをに読み込み [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
-   データをに移行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] します。  
  
このトピックでは、SSMA のインストールの前提条件と手順について説明します。  
  
## <a name="prerequisites"></a>前提条件  
SSMA は、Oracle 9 以降のバージョンおよびのすべてのエディションで動作するように設計されてい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
SSMA をインストールする前に、コンピューターが次の要件を満たしていることを確認してください。  
  
-   Windows 7 以降のバージョン、または Windows Server 2008 以降のバージョン。  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows インストーラー3.1 以降のバージョン。  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] バージョン4.0 以降のバージョン。 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)]バージョン4.0 は、製品メディアで入手でき [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 また、 [.NET Framework デベロッパーセンター](https://go.microsoft.com/fwlink/?LinkId=48882)から入手することもできます。  
  
-   Oracle クライアント9.0 以降のバージョン、および移行する Oracle データベースへの接続。 Oracle クライアントのバージョンは、Oracle データベースのバージョンと同じバージョン、またはそれ以降のバージョンである必要があります。  
  
    Oracle クライアントは、oracle 製品メディアまたは Oracle Web サイトからインストールできます。 接続の詳細については、「 [Oracle Database &#40;OracleToSQL&#41;への接続](../../ssma/oracle/connecting-to-oracle-database-oracletosql.md)」を参照してください。  
  
-   にアクセスし、データベースオブジェクトとデータの移行先となる、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または AZURE SQL DB のターゲットインスタンスをホストするコンピューターに対して十分なアクセス許可を付与します。 詳細については、「 [SQL Server &#40;OracleToSQL&#41;への接続](../../ssma/oracle/connecting-to-sql-server-oracletosql.md)」を参照してください。  
  
-   4 GB の RAM を推奨します。  
  
## <a name="installing-the-ssma-for-oracle-client"></a>SSMA for Oracle クライアントのインストール  
SSMA は Web からダウンロードできます。 最新バージョンをダウンロードするには、 [SQL Server Migration Assistant のダウンロードページ](https://aka.ms/ssmafororacle)を参照してください。  
  
最新バージョンをダウンロードした後は、SSMA をインストールする前にからインストールファイルを抽出する必要があります。  
  
**SSMA クライアントをインストールするには**  
  
1.  SSMA for Oracle *n*.Install.exe をダブルクリックします。 *n*はビルド番号です。  
  
2.  [ようこそ] ページで **[次へ]** をクリックします。  
  
    前提条件がインストールされていない場合は、最初に必要なコンポーネントをインストールする必要があることを示すメッセージが表示されます。 すべての前提条件がインストールされていることを確認してから、インストールプログラムを再実行してください。  
  
3.  使用許諾契約書を確認します。 同意する場合は、[**使用許諾契約書に同意**します] を選択し、[**次へ**] をクリックします。  
  
4.  [セットアップの種類の選択] ページで、[**標準**] をクリックします。  
  
5.  **[インストール]** をクリックします。  
  
> [!IMPORTANT]  
> 1.  新しいバージョンをインストールする前に、SSMA for Oracle の以前のバージョンをすべてアンインストールしてください。  
  
既定のインストール場所は、Oracle の場合は C:\Program の SQL Server Migration Assistant です。  
  
SSMA プログラムファイルに加えて、SSMA for Oracle extension pack もインストールする必要があり [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 詳細については、「 [SQL Server &#40;OracleToSQL&#41;での SSMA コンポーネントのインストール](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[SQL Server &#40;OracleToSQL&#41;での SSMA コンポーネントのインストール](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md)  
[Oracle データベースの SQL Server &#40;OracleToSQL&#41;への移行](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
