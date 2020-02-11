---
title: SSMA for Sybase クライアントのインストール (SybaseToSQL) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: e770c2f2-52b9-4471-a207-0d35df41399c
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 8680685640b234e47f6e68d7fb802fc7e2f5d81c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68029023"
---
# <a name="installing-ssma--for-sybase-client-sybasetosql"></a>SSMA for Sybase クライアントのインストール (SybaseToSQL)
SSMA クライアントは、Sybase Adaptive Server Enterprise (ASE) データベースサーバーへの接続、または azure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sql db のインスタンスへの接続、ASE データベースオブジェクトのまたは azure sql db 構文[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]への変換、または azure sql db へのデータの移行、または azure SQLDB へ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のデータの移行に使用されるプログラムファイルで構成されています。  
  
このトピックでは、SSMA のインストールの前提条件と手順について説明します。  
  
## <a name="prerequisites"></a>前提条件  
SSMA は、ASE 11.9.2 以降のバージョンおよびのすべての[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エディションで動作するように設計されています。  
  
SSMA をインストールする前に、コンピューターが次の要件を満たしていることを確認してください。  
  
-   Windows 7 以降のバージョン、または Windows Server 2008 以降のバージョン。  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows インストーラー3.1 以降のバージョン。  
  
-   .NET Framework [!INCLUDE[msCoName](../../includes/msconame_md.md)]バージョン4.0 以降のバージョン。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]製品メディアでは、.NET Framework バージョン4.0 を利用できます。 また、 [.NET Framework デベロッパーセンター](https://go.microsoft.com/fwlink/?LinkId=48882)から入手することもできます。  
  
-   Sybase OLEDB/ADO.Net/ODBC プロバイダーと、移行するデータベースが格納されている Sybase ASE データベースサーバーへの接続。 Sybase ASE 製品メディアからプロバイダーをインストールすることができます。 接続の詳細については、「 [SYBASE ASE &#40;SybaseToSQL&#41;への接続](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md)」を参照してください。  
  
-   にアクセスし、データベースオブジェクトとデータの移行先となる、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または AZURE SQL DB のターゲットインスタンスをホストするコンピューターに対して十分なアクセス許可を付与します。 詳細については、「 [Azure sql DB &#40;sybasetosql&#41;に接続](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md)するための[SQL Server &#40;sybasetosql&#41;](../../ssma/sybase/connecting-to-sql-server-sybasetosql.md) /への接続」を参照してください。  
  
-   4 GB の RAM を推奨します。  
  
## <a name="installing-the-ssma-for-sybase-client"></a>SSMA for Sybase クライアントのインストール  
SSMA は Web からダウンロードできます。 最新バージョンをダウンロードするには、 [SQL Server Migration Assistant のダウンロードページ](https://aka.ms/ssmaforsybase)を参照してください。  
  
最新バージョンをダウンロードした後は、SSMA をインストールする前にからインストールファイルを抽出する必要があります。  
  
**SSMA クライアントをインストールするには**  
  
1.  [SSMA for Sybase *n*] をダブルクリックします。Setup.exe をインストールします。ここで、 *n*はビルド番号です。  
  
2.  [ようこそ] ページで **[次へ]** をクリックします。  
  
    前提条件がインストールされていない場合は、最初に必要なコンポーネントをインストールする必要があることを示すメッセージが表示されます。 すべての前提条件がインストールされていることを確認してから、インストールプログラムを再実行してください。  
  
3.  使用許諾契約書を確認します。 同意する場合は、[**使用許諾契約書に同意**します] を選択し、[**次へ**] をクリックします。  
  
4.  [セットアップの種類の選択] ページで、[**標準**] をクリックします。  
  
5.  
  **[インストール]** をクリックします。  
  
> [!IMPORTANT]  
> 1.  新しいバージョンをインストールする前に、SSMA for Sybase の以前のバージョンをすべてアンインストールしてください。  
  
既定のインストール場所は、Sybase の場合は C:\Program の SQL Server Migration Assistant です。  
  
SSMA プログラムファイルに加えて、SSMA for Sybase Extension Pack もインストールする必要があり[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ます。 詳細については、「 [SQL Server &#40;SybaseToSQL&#41;での SSMA コンポーネントのインストール](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[SSMA コンポーネントの SQL Server &#40;SybaseToSQL&#41;のインストール](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)  
[Sybase ASE データベースの SQL Server への移行-Azure SQL DB &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
