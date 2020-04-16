---
title: インストール
ms.custom: ''
ms.date: 07/15/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
author: markingmyname
ms.author: maghan
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 77d5bcf0d1000b0ceee182ba043f81b4c1221ae8
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388223"
---
# <a name="installing-sql-server-native-client"></a>SQL Server Native Client のインストール
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]


  Microsoft[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ネイティブ クライアント 11.0 は[!INCLUDE[ssSQL15](../../../includes/sssql15-md.md)]、 をインストールするときにインストールされます。 
 
 SQL Server 2016 ネイティブ クライアントはありません。 詳細については、「 [SQL Server Native Client](../../../relational-databases/native-client/sql-server-native-client.md)」を参照してください。 
 
SQL Server 2012 機能パックの Web ページから sqlncli.msi を取得することもできます。 SQL Server ネイティブ クライアントの最新バージョンをダウンロードするには、[マイクロソフト ® SQL Server ® 2012 機能パック](https://www.microsoft.com/download/confirmation.aspx?id=29065)にアクセスしてください。 SQL Server 2012 より前のネイティブ クライアントの以前の[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]バージョンもコンピューターに[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]インストールされている場合、ネイティブ クライアント 11.0 は、以前のバージョンと並行してインストールされます。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client のファイル (sqlncli11.dll、sqlnclir11.rll、および s11ch_sqlncli.chm) は、次の場所にインストールされます。  
  
 `%SYSTEMROOT%\system32\`  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーと [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーのすべてのレジストリ設定は、インストール処理の一環として適切に行われます。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ヘッダー ファイルとライブラリ ファイル (sqlncli.h と sqlncli11.lib) は、次の場所にインストールされます。  
  
 `%PROGRAMFILES%\Microsoft SQL Server\110\SDK`  
  
 インストールの一部[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]としてネイティブ クライアントを[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]インストールする以外に、 sqlncli.msi[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]という名前の再頒布可能インストール プログラムもあります。 `%CD%\Setup\`  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client は、sqlncli.msi を使用して配布できます。 アプリケーションを配置する場合は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client をインストールする必要があります。 チェイナーとブートストラップのテクノロジを使用すると、ユーザーが 1 回のインストール手順に従うだけで複数のパッケージをまとめてインストールできるようになります。 詳細については、「[Visual Studio 2005 用のカスタム ブートストラップ パッケージの作成](https://go.microsoft.com/fwlink/?LinkId=115667)」および「[カスタムの必須コンポーネントの追加](https://go.microsoft.com/fwlink/?LinkId=115668)」をご覧ください。  
  
 x64 バージョンと Itanium バージョンの sqlncli.msi では、32 ビット バージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client もインストールされます。 アプリケーションが、開発時に使用したものとは異なるプラットフォームを対象としている場合、Microsoft ダウンロード センターから x64、Itanium、および x86 用のバージョンの sqlncli.msi をダウンロードできます。  
  
 sqlncli.msi を呼び出すと、既定ではクライアント コンポーネントだけがインストールされます。 クライアント コンポーネントは、ネイティブ クライアントを使用して[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]開発されたアプリケーションの実行をサポートするファイルです。 SDK コンポーネントもインストールするには、コマンド ラインで `ADDLOCAL=All` を指定します。 次に例を示します。  
  
 `msiexec /i sqlncli.msi ADDLOCAL=ALL APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  
  
## <a name="silent-install"></a>サイレント インストール  
 msiexec で /passive、/qn、/qb、または /qr オプションを指定する場合、IACCEPTSQLNCLILICENSETERMS=YES も指定して、使用許諾契約の条件に同意することを明示的に指定する必要があります。 このオプションは、すべて大文字で指定する必要があります。  
  
## <a name="uninstalling-sql-server-native-client"></a>SQL Server Native Client のアンインストール  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]サーバーや[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ツールなどのアプリケーションはネイティブ クライアントに[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]依存するため、依存するすべてのアプリケーションがアンインストールされるまで[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ネイティブ クライアントをアンインストールしないことが重要です。 アプリケーションがネイティブ クライアントに依存しているという警告をユーザー[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]に提供するには、次のように、MSI で APPGUID インストール オプションを使用します。  
  
 `msiexec /i sqlncli.msi APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  
  
 APPGUID に渡す値は、特定の製品コードです。 Microsoft インストーラーを使用してアプリケーションのセットアップ プログラムをバンドルするときは、製品コードを作成する必要があります。  
  
## <a name="see-also"></a>参照  
 [SQL Server ネイティブ クライアントを使用したアプリケーションのビルド](../../../relational-databases/native-client/applications/installing-sql-server-native-client.md)   
 [インストール方法に関するトピック](https://msdn.microsoft.com/library/59de41e7-557f-462a-8914-53ec35496baa)  
  
  
