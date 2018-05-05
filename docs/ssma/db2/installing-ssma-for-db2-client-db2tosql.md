---
title: SSMA の DB2 クライアント (DB2ToSQL) のインストール |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssma-db2
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 3ae2a470-6afd-4512-b6d1-fcbe6afe88ad
caps.latest.revision: 8
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: d976466251d49f85074864ca39a034a988cbff4f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="installing-ssma-for-db2-client-db2tosql"></a>SSMA の DB2 クライアント (DB2ToSQL) のインストール
SSMA クライアントは、次のタスクを実行するプログラム ファイルで構成されます。  
  
-   DB2 データベースに接続します。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] のインスタンスに接続する。  
  
-   DB2 データベース オブジェクトに変換[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]構文です。  
  
-   オブジェクトを読み込む[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]します。  
  
-   データを移行して[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
このトピックでは、インストールの前提条件と SSMA をインストールするための指示を提供します。  
  
## <a name="prerequisites"></a>前提条件  
SSMA は、Z/OS 9.0、10.0 のバージョンの DB2 または LUW 9.8 と 10.1 以降のバージョンの DB2 を使用するように設計された、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012 と[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2014 です。  
  
SSMA をインストールする前に、コンピューターが、次の要件を満たしていることを確認してください。  
  
-   Windows 7 またはそれ以降のバージョンまたは Windows Server 2008 以降のバージョン。  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows インストーラー 3.1 以降。  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)]バージョン 4.0 またはそれ以降のバージョン。 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)]バージョン 4.0 は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]製品メディア。 取得することも、 [.NET Framework Developer Center](http://go.microsoft.com/fwlink/?LinkId=48882)です。  
  
-   DB2 バージョン 5 や以降のバージョンを移行先の DB2 データベースへの接続用の Microsoft OLEDB プロバイダーです。  
  
-   アクセスおよびのターゲット インスタンスをホストするコンピューターに十分なアクセス許可[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB の場所はで移行するデータベース オブジェクトとデータ。 詳細については、次を参照してください。 [SQL Server に接続する&#40;DB2eToSQL&#41;](../../ssma/db2/connecting-to-sql-server-db2etosql.md)です。  
  
-   4 GB の RAM (推奨)。  
  
## <a name="microsoft-oledb-provider-for-db2"></a>Microsoft OLEDB Provider for DB2  
OLEDB provider for DB2 バージョン 5.0 をダウンロードする」に進んでください[Microsoft® SQL Server® 2014 Feature Pack](http://www.microsoft.com/download/details.aspx?id=42295)です。  
  
SSMA は Web からダウンロードします。 最新バージョンをダウンロードするを参照してください。、 [SQL Server Migration Assistant のダウンロード ページ](http://aka.ms/ssmafordb2)です。  
  
最新バージョンをダウンロードした後は、SSMA をインストールする前のインストール ファイルを抽出する必要があります。  
  
**SSMA クライアントをインストールするには**  
  
1.  SSMA for DB2 をダブルクリック*n*です。Install.exe、場所*n*ビルド番号です。  
  
2.  [ようこそ] ページで、をクリックして**次**です。  
  
    インストールの前提条件がないとすると必要なコンポーネントをインストールする必要があります最初を示すメッセージが表示されます。 すべての前提条件がインストールされているし、インストール プログラムをもう一度実行していることを確認してください。  
  
3.  使用許諾契約書を読み取る。 同意する場合は、選択**ライセンス契約の条項に同意**、順にクリック**次**です。  
  
4.  セットアップの種類の選択 ページで、をクリックして**標準**です。  
  
5.  **[インストール]** をクリックします。  
  
> [!IMPORTANT]  
> 1.  新しいバージョンをインストールする前に、DB2 用 SSMA のすべての以前のバージョンをアンインストールしてください。  
  
既定のインストール場所は C:\Program files \microsoft SQL Server Migration Assistant for DB2 です。  
  
## <a name="see-also"></a>参照  
[SSMA コンポーネントを SQL Server インストール&#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-components-on-sql-server-db2tosql.md)  
[SQL Server にデータベースを移行する DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
  
