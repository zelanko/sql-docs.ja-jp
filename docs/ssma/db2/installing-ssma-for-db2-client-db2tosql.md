---
title: SSMA for DB2 クライアント (DB2ToSQL) のインストール |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 3ae2a470-6afd-4512-b6d1-fcbe6afe88ad
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: d67b52a75f3c5b2a96bf17b5ee039e08a38a5875
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67989482"
---
# <a name="installing-ssma-for-db2-client-db2tosql"></a>SSMA for DB2 クライアント (DB2ToSQL) のインストール
SSMA クライアントは、次のタスクを実行するプログラム ファイルで構成されます。  
  
-   DB2 データベースに接続します。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続する。  
  
-   DB2 データベース オブジェクトを変換[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]構文。  
  
-   オブジェクトを読み込む[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  
  
-   データを移行して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  
  
このトピックでは、インストールの前提条件との SSMA のインストール手順を説明します。  
  
## <a name="prerequisites"></a>前提条件  
SSMA は Z/OS バージョン 9.0、10.0 で DB2 または LUW バージョン 9.8 と 10.1 以降のバージョンの DB2 を使用するように設計および[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2012 と[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2014 です。  
  
SSMA をインストールする前に、コンピューターが、次の要件を満たしていることを確認します。  
  
-   Windows 7 またはそれ以降のバージョンまたは Windows Server 2008 以降のバージョン。  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows インストーラー 3.1 またはそれ以降のバージョン。  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)]バージョン 4.0 またはそれ以降のバージョン。 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)]バージョン 4.0 は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]製品メディア。 取得することも、 [.NET Framework Developer Center](https://go.microsoft.com/fwlink/?LinkId=48882)します。  
  
-   DB2 バージョン 5 または以降のバージョンと移行する DB2 データベースへの接続用の Microsoft OLEDB プロバイダー。  
  
-   アクセスとのターゲット インスタンスをホストするコンピューターに十分なアクセス許可[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または Azure SQL DB が、移行するデータベース オブジェクトとデータ。 詳細については、次を参照してください。 [SQL Server に接続する&#40;DB2eToSQL&#41;](../../ssma/db2/connecting-to-sql-server-db2etosql.md)します。  
  
-   4 GB の RAM を推奨します。  
  
## <a name="microsoft-oledb-provider-for-db2"></a>Microsoft ole DB Provider for DB2  
OLEDB provider for DB2 バージョン 5.0 をダウンロードする」に進んでください[Microsoft® SQL Server® 2014 Feature Pack](https://www.microsoft.com/download/details.aspx?id=42295)します。  
  
SSMA は、Web からダウンロードします。 最新バージョンをダウンロードするを参照してください。、 [SQL Server Migration Assistant のダウンロード ページ](https://aka.ms/ssmafordb2)します。  
  
最新バージョンをダウンロードした後は、SSMA をインストールする前からインストール ファイルを抽出する必要があります。  
  
**SSMA クライアントをインストールするには**  
  
1.  SSMA for DB2 をダブルクリックします*n*します。Install.exe、場所*n*ビルド番号です。  
  
2.  [ようこそ] ページで、次のようにクリックします。**次**します。  
  
    前提条件がインストールされていない場合に必要なコンポーネントをインストールする必要がありますまずを示すメッセージが表示されます。 すべての前提条件をインストールし、インストール プログラムをもう一度実行してください。  
  
3.  エンド ユーザー ライセンス契約を読みます。 同意する場合は、選択 **、使用許諾契約書に同意**、順にクリックします**次**します。  
  
4.  セットアップの種類の選択 ページで、次のようにクリックします。**標準**します。  
  
5.  **[インストール]** をクリックします。  
  
> [!IMPORTANT]  
> 1.  新しいバージョンをインストールする前に、DB2 用の SSMA のすべての旧バージョンをアンインストールしてください。  
  
既定のインストール場所は C:\Program files \microsoft SQL Server Migration Assistant for DB2 です。  
  
## <a name="see-also"></a>参照  
[SQL Server での SSMA コンポーネントのインストール&#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-components-on-sql-server-db2tosql.md)  
[SQL Server にデータベースを移行する DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
  
