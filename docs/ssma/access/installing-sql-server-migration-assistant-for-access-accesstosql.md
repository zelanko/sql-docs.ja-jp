---
title: SQL Server Migration Assistant for Access (AccessToSQL) をインストールする |Microsoft Docs
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
ms.openlocfilehash: 4cd58a535836a82dc6cca660ba745aed58e2c84c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67986325"
---
# <a name="installing-sql-server-migration-assistant-for-access-accesstosql"></a>SQL Server Migration Assistant for Access (AccessToSQL) をインストールします。
[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant (SSMA) のアクセスは、Windows インストーラー ベースのウィザードを使用してインストールされます。 ここでは、インストールの前提条件についての情報、SSMA の最新バージョンへのリンクとインストール、ライセンス、アンインストール、および SSMA をアップグレードする方法について説明します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
SSMA をインストールする前に、システムが、次の要件を満たしていることを確認します。  
  
-   Windows 7 または以降のバージョンまたは Windows Server 2008 またはそれ以降のバージョン。  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows インストーラー 3.1 またはそれ以降のバージョン。  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] .NET Framework バージョン 4.0 またはそれ以降のバージョン。 .NET Framework バージョン 4.0 で使用できる、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]製品ディスクとで情報を使用して、 [Microsoft .NET ガイド](https://docs.microsoft.com/dotnet/framework/)。
  
-   アクセスとのターゲット インスタンスをホストするコンピューターに十分なアクセス許可[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]SQL Azure DB に移行するデータベース オブジェクトとデータ。  
  
-   Microsoft データ アクセス オブジェクト (DAO) プロバイダーのバージョン 12.0 または 14.0 です。 Microsoft Office 2010/2007 製品から DAO プロバイダーをインストールしたり、Microsoft web サイトからダウンロードできます。  
  
-   SQL Server Native Access Client (SNAC) バージョン 10.5 以降の SQL Azure に移行します。 SNAC の最新バージョンを取得する[Microsoft® SQL Server® 2008 R2 用 Feature Pack](https://go.microsoft.com/fwlink/?LinkId=196940)  
  
-   4 GB RAM (推奨)。  
  
## <a name="installing-ssma"></a>SSMA のインストール  
SSMA は、Web からダウンロードします。 最新バージョンをダウンロードするを参照してください。、 [SQL Server Migration Assistant のダウンロード ページ](https://aka.ms/ssmaforaccess)します。  
  
最新バージョンをダウンロードした後は、SSMA をインストールする前からインストール ファイルを抽出する必要があります。

> [!IMPORTANT]  
> -   SSMA for Access のすべての旧バージョンを新しいバージョンをインストールする前にアンインストールしてください。  
  
**SSMA のインストール**  
  
1.  SSMA for Access をダブルクリックして*n*.msi、場所*n*ビルド番号です。  
  
2.  [ようこそ] ページで、次のようにクリックします。**次**します。  
  
    前提条件のインストールがない、必要なコンポーネントをインストールする必要がありますまずことを示すメッセージが表示されます。 すべての前提条件をインストールし、インストール プログラムをもう一度実行してください。  
  
3.  使用許諾契約書に; の読み取り同意する場合は、選択**契約書に同意**、順にクリックします**次**します。  
  
4.  セットアップの種類の選択 ページで、次のようにクリックします。**標準**します。  
  
5.  **[インストール]** をクリックします。  
  
既定のインストール場所は C:\Program files \microsoft SQL Server Migration Assistant for Access です。  
  
## <a name="uninstalling-ssma-for-access"></a>アンインストールの SSMA for Access  
SSMA を使用してアンインストール**プログラム追加と削除**コントロール パネルの します。 あるプログラムをアンインストールする SSMA プロジェクト ファイルを削除またはしませんログ ファイルを認識します。  
  
**SSMA をアンインストールするには**  
  
1.  クリックして**開始**、] をクリックして**コントロール パネルの [** 、順にクリックします**プログラム追加と削除**します。  
  
2.  選択**Microsoft SQL Server Migration Assistant for Access**、 をクリックし、**削除**します。  
  
## <a name="upgrading-to-a-later-version"></a>以降のバージョンにアップグレードします。  
SSMA for Access の以降のバージョンにアップグレードする場合は、SSMA for Access をアンインストールし、新しいバージョンをインストールする必要があります。 アンインストール SSMA のこのプロセスを完了するアクセス セクションの指示に従います。  
  
SSMA for Access の以前のバージョンで作成したプロジェクトを開くには、SSMA は、プロジェクトを新しいバージョンに変換するかどうかを要求します。 クリックして**はい**SSMA の新しいバージョンでプロジェクトを使用します。  
  
## <a name="see-also"></a>関連項目  
[Access データベースの移行の準備](preparing-access-databases-for-migration-accesstosql.md)  
[SQL Server へのアクセス データベースの移行](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
[SQL Server への Access アプリケーションのリンク](linking-access-applications-to-sql-server-azure-sql-db-accesstosql.md)  
  
