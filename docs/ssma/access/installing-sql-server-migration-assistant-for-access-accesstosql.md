---
title: アクセスのための SQL Server Migration Assistant のインストール (アクセス可能な SQL) |Microsoft Docs
description: SQL Server Migration Assistant (SSMA) にアクセスするためのインストールの前提条件と、インストール、ライセンス、アップグレード、およびアンインストールの方法について説明します。
ms.prod: sql
ms.custom: ''
ms.date: 08/15/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
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
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 5ca42e406bb7483617afe6364027014650e838f2
ms.sourcegitcommit: 59cda5a481cfdb4268b2744edc341172e53dede4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "84293759"
---
# <a name="installing-sql-server-migration-assistant-for-access-accesstosql"></a>アクセスのための SQL Server Migration Assistant のインストール (アクセス可能な SQL)
[!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Access の Migration Assistant (SSMA) は、Windows インストーラーベースのウィザードを使用してインストールされます。 このトピックでは、インストールの前提条件、SSMA の最新バージョンへのリンク、SSMA のインストール、ライセンス、アンインストール、およびアップグレードの手順について説明します。  
  
## <a name="prerequisites"></a>前提条件  
SSMA をインストールする前に、システムが次の要件を満たしていることを確認してください。  
  
-   Windows 7 以降のバージョン、または Windows Server 2008 以降のバージョン。  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows インストーラー3.1 以降のバージョン。  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)].NET Framework バージョン4.0 以降のバージョン。 .NET Framework バージョン4.0 は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 製品ディスクと、 [Microsoft .NET ガイド](https://docs.microsoft.com/dotnet/framework/)の情報を使用して入手できます。
  
-   にアクセスし、データベースオブジェクトとデータの移行先となる、SQL Azure DB のターゲットインスタンスをホストするコンピューターに対する十分なアクセス許可を付与し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
-   Microsoft Data Access Object (DAO) プロバイダーバージョン12.0 または14.0。 Microsoft Office 2010/2007 製品から DAO プロバイダーをインストールするか、Microsoft web サイトからダウンロードすることができます。  
  
-   SQL Azure への移行については、SQL Server ネイティブアクセスクライアント (SNAC) バージョン10.5 以降。 最新バージョンの SNAC は、 [Microsoft® SQL Server® 2008 R2 Feature Pack](https://www.microsoft.com/download/details.aspx?id=44272)から入手できます。  
  
-   4 GB の RAM (推奨)。  
  
## <a name="installing-ssma"></a>SSMA のインストール  
SSMA は Web からダウンロードできます。 最新バージョンをダウンロードするには、 [SQL Server Migration Assistant のダウンロードページ](https://aka.ms/ssmaforaccess)を参照してください。  
  
最新バージョンをダウンロードした後は、SSMA をインストールする前にからインストールファイルを抽出する必要があります。

> [!IMPORTANT]  
> -   新しいバージョンをインストールする前に、アクセスするために SSMA の以前のバージョンをすべてアンインストールしてください。  
  
**SSMA をインストールするには**  
  
1.  SSMA for Access *n*をダブルクリックします。 *n*はビルド番号です。  
  
2.  [ようこそ] ページで **[次へ]** をクリックします。  
  
    前提条件がインストールされていない場合は、最初に必要なコンポーネントをインストールする必要があることを示すメッセージが表示されます。 すべての前提条件がインストールされていることを確認してから、インストールプログラムを再実行してください。  
  
3.  使用許諾契約書をお読みください。同意する場合は、 **[同意する] を選択し**、[**次へ**] をクリックします。  
  
4.  [セットアップの種類の選択] ページで、[**標準**] をクリックします。  
  
5.  **[インストール]** をクリックします。  
  
既定のインストール場所は、Access の場合は C:\Program の SQL Server Migration Assistant です。  
  
## <a name="uninstalling-ssma-for-access"></a>SSMA をアンインストールしてアクセスできるようにする  
コントロールパネルの [**プログラムの追加と削除**] を使用して ssma をアンインストールします。 プログラムをアンインストールしても、SSMA プロジェクトファイルまたはログファイルは削除されないことに注意してください。  
  
**SSMA をアンインストールするには**  
  
1.  [**スタート**]、[**コントロール パネル**]、[**プログラムの追加と削除**] の順にクリックします。  
  
2.  [**アクセス] に Microsoft SQL Server Migration Assistant**を選択し、[**削除**] をクリックします。  
  
## <a name="upgrading-to-a-later-version"></a>新しいバージョンへのアップグレード  
Access 用に新しいバージョンの SSMA にアップグレードする場合は、まず SSMA をアンインストールしてから新しいバージョンをインストールする必要があります。 SSMA for Access のアンインストールに関するセクションの手順に従って、このプロセスを完了します。  
  
SSMA の以前のバージョンで作成したプロジェクトを開くと、プロジェクトを新しいバージョンに変換するかどうかを確認するメッセージが表示されます。 新しいバージョンの SSMA でプロジェクトを使用する場合は、[**はい**] をクリックします。  
  
## <a name="see-also"></a>関連項目  
[Access データベースの移行の準備](preparing-access-databases-for-migration-accesstosql.md)  
[Access データベースの SQL Server への移行](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
[Access アプリケーションの SQL Server へのリンク](linking-access-applications-to-sql-server-azure-sql-db-accesstosql.md)  
  
