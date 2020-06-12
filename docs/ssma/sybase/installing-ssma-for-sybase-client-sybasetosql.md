---
title: SSMA for SAP ASE クライアントのインストール (SybaseToSQL) |Microsoft Docs
description: SAP Adaptive Server Enterprise (ASE) 用の SQL Server Migration Assistant (SSMA) のインストールの前提条件と、のインストール方法について説明します。
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: e770c2f2-52b9-4471-a207-0d35df41399c
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 1325e9ba882bed76ecfc1b11f8ca1c379ca74bb4
ms.sourcegitcommit: 6593b3b6365283bb76c31102743cdccc175622fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "84306251"
---
# <a name="installing-ssma-for-sap-ase-client-sybasetosql"></a>SSMA for SAP ASE クライアントのインストール (SybaseToSQL)

SSMA クライアントは、SAP Adaptive Server Enterprise (ASE) データベースサーバーへの接続、または azure SQL db のインスタンスへの接続、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ASE データベースオブジェクトのまたは AZURE sql db 構文への変換、または AZURE SQL db への Azure SQL Database データの移行を行うために使用されるプログラムファイルで構成されて [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] います。  
  
このトピックでは、SSMA のインストールの前提条件と手順について説明します。  
  
## <a name="prerequisites"></a>前提条件

SSMA は、ASE 11.9.2 以降のバージョンおよびのすべてのエディションで動作するように設計されてい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
SSMA をインストールする前に、コンピューターが次の要件を満たしていることを確認してください。  
  
- Windows 7 以降のバージョン、または Windows Server 2008 以降のバージョン。  
- [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows インストーラー3.1 以降のバージョン。  
- [!INCLUDE[msCoName](../../includes/msconame_md.md)].NET Framework バージョン4.0 以降のバージョン。 製品メディアでは、.NET Framework バージョン4.0 を利用でき [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 また、 [.NET Framework デベロッパーセンター](https://go.microsoft.com/fwlink/?LinkId=48882)から入手することもできます。  
- Sybase OLEDB/ADO.Net/ODBC プロバイダーと、移行するデータベースが格納されている Sybase ASE データベースサーバーへの接続。 Sybase ASE 製品メディアからプロバイダーをインストールすることができます。 接続の詳細については、「 [SYBASE ASE &#40;SybaseToSQL&#41;への接続](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md)」を参照してください。  
- にアクセスし、データベースオブジェクトとデータの移行先となる、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または AZURE SQL DB のターゲットインスタンスをホストするコンピューターに対して十分なアクセス許可を付与します。 詳細については[ ](../../ssma/sybase/connecting-to-sql-server-sybasetosql.md)、「 / [Azure sql DB &#40;sybasetosql&#41;に接続](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md)するための SQL Server &#40;sybasetosql&#41;への接続」を参照してください。  
- 4 GB の RAM を推奨します。  
  
## <a name="installing-the-ssma-for-sybase-client"></a>SSMA for Sybase クライアントのインストール

SSMA は Web からダウンロードできます。 最新バージョンをダウンロードするには、 [SQL Server Migration Assistant のダウンロードページ](https://aka.ms/ssmaforsybase)を参照してください。  
  
最新バージョンをダウンロードした後は、SSMA をインストールする前にからインストールファイルを抽出する必要があります。  
  
**SSMA クライアントをインストールするには**
  
1. [SSMA for Sybase *n*.Install.exe] をダブルクリックします。ここで、 *n*はビルド番号です。  
  
2. [ようこそ] ページで **[次へ]** をクリックします。  
  
    前提条件がインストールされていない場合は、最初に必要なコンポーネントをインストールする必要があることを示すメッセージが表示されます。 すべての前提条件がインストールされていることを確認してから、インストールプログラムを再実行してください。  
  
3. 使用許諾契約書を確認します。 同意する場合は、[**使用許諾契約書に同意**します] を選択し、[**次へ**] をクリックします。  
  
4. [セットアップの種類の選択] ページで、[**標準**] をクリックします。  
  
5. **[インストール]** をクリックします。  
  
> [!IMPORTANT]  
> 1. 新しいバージョンをインストールする前に、SSMA for Sybase の以前のバージョンをすべてアンインストールしてください。
  
既定のインストール場所は、Sybase の場合は C:\Program の SQL Server Migration Assistant です。  
  
SSMA プログラムファイルに加えて、SSMA for Sybase Extension Pack もインストールする必要があり [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 詳細については、「 [SQL Server &#40;SybaseToSQL&#41;での SSMA コンポーネントのインストール](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)」を参照してください。  
  
## <a name="see-also"></a>参照

[SSMA コンポーネントの SQL Server &#40;SybaseToSQL&#41;のインストール](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)  
[Sybase ASE データベースの SQL Server への移行-Azure SQL DB &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
