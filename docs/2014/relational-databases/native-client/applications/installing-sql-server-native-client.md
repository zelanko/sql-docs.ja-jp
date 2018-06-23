---
title: SQL Server Native Client をインストールする |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client, uninstalling
- SQLNCLI, installing
- SQLNCLI, uninstalling
- Setup [SQL Server Native Client]
- uninstalling SQL Server Native Client
- data access [SQL Server Native Client], uninstalling SQL Server Native Client
- installing SQL Server Native Client
- SQL Server Native Client, installing
- data access [SQL Server Native Client], installing SQL Server Native Client
- removing SQL Server Native Client
ms.assetid: c6abeab2-0052-49c9-be79-cfbc50bff5c1
caps.latest.revision: 43
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ca4e2935a8b1ff0ef8ed2571d0e1791206a492bd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36179297"
---
# <a name="installing-sql-server-native-client"></a>SQL Server Native Client のインストール
  Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 がインストールするときにインストールされている[!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)]です。 [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] Native Client は存在しません。 詳細については、次を参照してください。 [SQL Server Native Client の新](../sql-server-native-client.md)です。 SQL Server 2012 Feature Pack の web ページから sqlncli.msi を取得することもできます。 SQL Server Native Client の最新バージョンをダウンロードするには[Microsoft® SQL Server® 2012 SP2 用 Feature Pack](http://www.microsoft.com/en-us/download/details.aspx?id=43339)です。 以前のバージョンの場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ネイティブ クライアント コンピューターで、SQL Server 2012 がインストールされてもよりも早く[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client 11.0 は以前のバージョンと並列でインストール済みになります。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client のファイル (sqlncli11.dll、sqlnclir11.rll、および s11ch_sqlncli.chm) は、次の場所にインストールされます。  
  
 `%SYSTEMROOT%\system32\`  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーと [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーのすべてのレジストリ設定は、インストール処理の一環として適切に行われます。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ヘッダー ファイルとライブラリ ファイル (sqlncli.h と sqlncli11.lib) は、次の場所にインストールされます。  
  
 `%PROGRAMFILES%\Microsoft SQL Server\110\SDK`  
  
 インストールするだけでなく[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ネイティブ クライアントの一環として、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]インストールもには、sqlncli.msi をという名前の再頒布可能パッケージのインストール プログラムがある、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]次の場所にインストール ディスク`%CD%\Setup\`。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client は、sqlncli.msi を使用して配布できます。 アプリケーションを配置する場合は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client をインストールする必要があります。 チェイナーとブートストラップのテクノロジを使用すると、ユーザーが 1 回のインストール手順に従うだけで複数のパッケージをまとめてインストールできるようになります。 詳細については、次を参照してください。 [Visual Studio 2005 用のカスタム ブートス トラップ パッケージの作成](http://go.microsoft.com/fwlink/?LinkId=115667)と[カスタムの必須コンポーネントを追加する](http://go.microsoft.com/fwlink/?LinkId=115668)です。  
  
 x64 バージョンと Itanium バージョンの sqlncli.msi では、32 ビット バージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client もインストールされます。 アプリケーションが、開発時に使用したものとは異なるプラットフォームを対象としている場合、Microsoft ダウンロード センターから x64、Itanium、および x86 用のバージョンの sqlncli.msi をダウンロードできます。  
  
 sqlncli.msi を呼び出すと、既定ではクライアント コンポーネントだけがインストールされます。 クライアント コンポーネントは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client を使用して開発されたアプリケーションの実行をサポートするファイルです。 SDK コンポーネントもインストールするには、コマンド ラインで `ADDLOCAL=All` を指定します。 以下に例を示します。  
  
 `msiexec /i sqlncli.msi ADDLOCAL=ALL APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  
  
## <a name="silent-install"></a>サイレント インストール  
 msiexec で /passive、/qn、/qb、または /qr オプションを指定する場合、IACCEPTSQLNCLILICENSETERMS=YES も指定して、使用許諾契約の条件に同意することを明示的に指定する必要があります。 このオプションは、すべて大文字で指定する必要があります。  
  
## <a name="uninstalling-sql-server-native-client"></a>SQL Server Native Client のアンインストール  
 などのアプリケーション[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]サーバーおよび[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ツールによって異なります[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client は、アンインストールする重要なは[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ネイティブ クライアントすべてに依存するアプリケーションがアンインストールされるまでです。 警告メッセージに依存するアプリケーションがプロバイダーのユーザーに[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client、APPGUID インストール オプションを使用、MSI で次のようにします。  
  
 `msiexec /i sqlncli.msi APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  
  
 APPGUID に渡す値は、特定の製品コードです。 Microsoft インストーラーを使用してアプリケーションのセットアップ プログラムをバンドルするときは、製品コードを作成する必要があります。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client でアプリケーションの構築](installing-sql-server-native-client.md)   
 [インストール方法に関するトピック](../../../sql-server/install/installation-how-to-topics.md)  
  
  