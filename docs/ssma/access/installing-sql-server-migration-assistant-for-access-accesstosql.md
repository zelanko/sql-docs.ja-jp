---
title: "SQL Server Migration Assistant for Access (AccessToSQL) をインストールする |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-access
ms.custom: 
ms.date: 08/15/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- installing SSMA
- instructions, installation
- instructions, upgrade
- licensing SSMA
- prerequisites for installing SSMA
- procedure, installation
- procedure, licensing
- procedure, upgrading
- removing SSMA
- Setup
- uninstalling SSMA
- upgrading SSMA
ms.assetid: dd50eebd-75df-4e0d-8c4d-88b511aae4c7
caps.latest.revision: "31"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 0ed2247057865624d0e365a5cac24e390295975a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="installing-sql-server-migration-assistant-for-access-accesstosql"></a>SQL Server Migration Assistant for Access (AccessToSQL) をインストールします。
[!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant (SSMA) for Access は Windows インストーラー ベースのウィザードを使用してインストールします。 このトピックでは、インストール前提条件については、SSMA の最新バージョンへのリンクとインストール、ライセンス、アンインストール、および SSMA をアップグレードするための手順を提供します。  
  
## <a name="prerequisites"></a>Prerequisites  
SSMA をインストールする前に、システムが、次の要件を満たしていることを確認してください。  
  
-   Windows 7 以降のバージョンまたは Windows Server 2008 またはそれ以降のバージョン。  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows インストーラー 3.1 以降。  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] .NET Framework バージョン 4.0 またはそれ以降のバージョン。 .NET Framework バージョン 4.0 で使用できる、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]製品ディスク、およびで情報を使用して、 [Microsoft .NET ガイド](https://docs.microsoft.com/en-us/dotnet/framework/)です。
  
-   アクセスおよびのターゲット インスタンスをホストするコンピューターに十分なアクセス許可[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]SQL Azure DB が移行される先があるデータベース オブジェクトとデータ。  
  
-   Microsoft データ アクセス オブジェクト (DAO) 12.0 または 14.0 プロバイダーのバージョン。 Microsoft Office 2010/2007 製品から DAO プロバイダーをインストールしたり、Microsoft web サイトからダウンロードできます。  
  
-   SQL Server Native Access Client (SNAC) バージョン 10.5 以降の SQL Azure に移行します。 SNAC の最新バージョンを取得する[Microsoft® SQL Server® 2008 R2 用 Feature Pack](http://go.microsoft.com/fwlink/?LinkId=196940)  
  
-   4 GB の RAM (推奨)。  
  
## <a name="installing-ssma"></a>SSMA のインストール  
SSMA は Web からダウンロードします。 最新バージョンをダウンロードするを参照してください。、 [SQL Server Migration Assistant のダウンロード ページ](http://aka.ms/ssmaforaccess)です。  
  
最新バージョンをダウンロードした後は、SSMA をインストールする前のインストール ファイルを抽出する必要があります。

> [!IMPORTANT]  
> -   SSMA for Access の以前のバージョンをすべてを新しいバージョンをインストールする前にアンインストールしてください。  
  
**SSMA をインストールするには**  
  
1.  SSMA for Access をダブルクリックして *n* .msi、場所 *n* ビルド番号です。  
  
2.  [ようこそ] ページで、をクリックして**次**です。  
  
    インストールの前提条件がない、必要なコンポーネントをインストールする必要があります最初を示すメッセージが表示されます。 すべての前提条件がインストールされているし、インストール プログラムをもう一度実行していることを確認してください。  
  
3.  読み取り、使用許諾契約書です。同意する場合は、選択**同意**、順にクリック**[次へ]**です。  
  
4.  セットアップの種類の選択 ページで、をクリックして**標準**です。  
  
5.  **[インストール]**をクリックします。  
  
既定のインストール場所は C:\Program files \microsoft SQL Server Migration Assistant for Access です。  
  
## <a name="uninstalling-ssma-for-access"></a>アンインストールの SSMA for Access  
SSMA を使用してアンインストール**プログラム追加と削除**コントロール パネルの します。 プログラムのアンインストールはありません SSMA プロジェクト ファイルを削除するファイルまたはログ ファイルに注意してください。  
  
**SSMA をアンインストールするには**  
  
1.  をクリックして**開始**、] をクリックして**コントロール パネルの [**、順にクリック**プログラム追加と削除**です。  
  
2.  選択**Microsoft SQL Server Migration Assistant for Access**、クリックして**削除**です。  
  
## <a name="upgrading-to-a-later-version"></a>以降のバージョンにアップグレードします。  
SSMA for Access の以降のバージョンにアップグレードする場合は、まず SSMA for Access をアンインストールして、新しいバージョンをインストールします。 アンインストールする SSMA でこのプロセスを完了するアクセス セクションの手順に従います。  
  
SSMA for Access の以前のバージョンで作成されたプロジェクトを開くと、SSMA は、プロジェクトを新しいバージョンに変換するかどうかを確認します。 をクリックして**はい**SSMA の新しいバージョンでプロジェクトを使用します。  
  
## <a name="see-also"></a>参照  
[Access データベースの移行の準備](http://msdn.microsoft.com/9b80a9e0-08e7-4b4d-b5ec-cc998d3f5114)  
[SQL Server へのアクセス データベースの移行](http://msdn.microsoft.com/76a3abcf-2998-4712-9490-fe8d872c89ca)  
[SQL Server へのリンクの Access アプリケーション](http://msdn.microsoft.com/82374ad2-7737-4164-a489-13261ba393d4)  
  
