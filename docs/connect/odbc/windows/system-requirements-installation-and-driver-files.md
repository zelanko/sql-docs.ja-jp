---
title: システム要件、インストール、およびドライバー ファイル |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/14/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d90fa182-1dab-4d6f-bd85-a04dd1479986
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 7a6ce94207d79c58c5d615be723b3d44d69cdaf9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="system-requirements-installation-and-driver-files"></a>インストール、ドライバー ファイルの基本的なシステム要件
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] は、SQL Server 2014、SQL Server 2012 R2、 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro_md.md)]、 [!INCLUDE[ssKatmai](../../../includes/sskatmai_md.md)]、 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005_md.md)]への接続をサポートします。  
  
ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] on Windows は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Native Client の 1 つまたは複数のバージョンもインストールされているコンピューターにインストールできます。  
  
ODBC Driver 13 およびの 13.1 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]、上記に加え、SQL Server 2016 をサポートします。 

場合、ODBC ドライバーが 17[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]サポート上のすべてのものとも SQL Server 2017 です。
  
接続文字列で指定するドライバー名は`ODBC Driver 11 for SQL Server`または`ODBC Driver 13 for SQL Server`(13 との両方の 13.1) または`ODBC Driver 17 for SQL Server`です。
  
## <a name="supported-operating-systems"></a>サポートされるオペレーティング システム

次の Windows オペレーティング システムのドライバーでアプリケーションを実行できます。  

-   Windows Server 2008 R2 
-   Windows Server 2012
-   Windows Server 2012 R2    
-   Windows Vista SP2 *(ODBC Driver 11 のみ)*  
-   Windows 7  
-   Windows 8
-   Windows 8.1
-   Windows 10
  
## <a name="installing-microsoft-odbc-driver-for-sql-server"></a>SQL Server 用 Microsoft ODBC Driver をインストールします。

実行すると、ドライバーがインストールされている`msodbcsql.msi`から、次のリンクのいずれか。

- [SQL Server on Windows 用 Microsoft ODBC Driver 17 をダウンロードします。](https://www.microsoft.com/download/details.aspx?id=56567)
- [SQL Server on Windows 用 Microsoft ODBC Driver 13.1 をダウンロードします。](https://www.microsoft.com/download/details.aspx?id=53339)
- [SQL Server on Windows 用 Microsoft ODBC Driver 13 をダウンロードします。](https://www.microsoft.com/download/details.aspx?id=50420)
- [SQL Server on Windows 用 Microsoft ODBC Driver 11 をダウンロード](https://www.microsoft.com/download/details.aspx?id=36434)です。 

並列でインストール済みであることができます[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]Native Client です。  

呼び出した場合`msodbcsql.msi`既定ではクライアント コンポーネントだけがインストールされます。 クライアント コンポーネントは、ドライバーを使用して開発されたアプリケーションの実行をサポートするファイルです。 SDK コンポーネントをインストールするには指定`ADDLOCAL=ALL`コマンド ラインでします。 以下に例を示します。  
  
```  
msiexec /i msodbcsql.msi ADDLOCAL=ALL  
```  
  
 指定`IACCEPTMSODBCSQLLICENSETERMS=YES`を使用する場合は、エンド ユーザー ライセンスの条項を受け入れるように、 `/passive`、 `/qn`、 `/qb`、または`/qr`をインストールするオプションです。 このオプションは、すべて大文字で指定する必要があります。 以下に例を示します。  
  
```  
msiexec /quiet /passive /qn /i msodbcsql.msi IACCEPTMSODBCSQLLICENSETERMS=YES ADDLOCAL=ALL  
```  
  
 サイレント アンインストールを行うには:  
  
```  
msiexec /quiet /passive /qn /uninstall msodbcsql.msi  
```  
  
アプリケーションでは、ドライバーを使用するときに、アプリケーションが示されるはずインストール オプションを使ってドライバーに依存している`APPGUID`です。 これにより、ドライバーのインストーラーをレポートに依存するアプリケーションをアンインストールする前にできます。 ドライバーの依存関係を指定するには、設定、`APPGUID`コマンド ライン パラメーターを製品コード、ドライバーをサイレント モードでインストールするときにします。 (製品コードする必要がある作成してアプリケーションのセットアップ プログラムをバンドルする Microsoft インストーラーを使用する場合)。以下に例を示します。  
  
```  
msiexec /i msodbcsql.msi APPGUID={ <Your dependent application's APPGUID> }  
```  

## <a name="command-line-tools-sqlcmdexe-and-bcpexe"></a>コマンド ライン ツール: sqlcmd.exe および bcp.exe

`bcp.exe`と`sqlcmd.exe`でダウンロードできます、ドライバーで使用するためのツール[Microsoft Command Line Utilities 11 for SQL Server](http://www.microsoft.com/download/details.aspx?id=36433)、 [Microsoft コマンド ライン ユーティリティ 13 for SQL Server](https://www.microsoft.com/download/details.aspx?id=52680)、または[Microsoft Command Line Utilities 13.1 for SQL Server](https://www.microsoft.com/download/details.aspx?id=53591)です。 前提条件をインストールするにはドライバーが`sqlcmd.exe`と`bcp.exe`です。
  
`bcp.exe` `sqlcmd.exe`がインストールされている、`110\Tools`のサブフォルダー`%PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC`バージョン 11、および`130\Tools`13 と 13.1 です。

BCP 関数を使用するアプリケーションには、アプリケーションのコンパイルに使用されるライブラリとヘッダー ファイルで提供されている同じバージョンのドライバーをする必要がありますを指定します。  

ODBC アプリケーションをコンパイルするときに、`msodbcsql11.lib`と`msodbcsql.h`を使用して"ドライバー = {ODBC Driver 11 for SQL Server}"接続文字列にします。

## <a name="components-of-the-microsoft-odbc-driver-for-includessnoversionincludesssnoversionmdmd-on-windows"></a>コンポーネントの Microsoft ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] windows 
 Windows 上の ODBC ドライバーには、次のコンポーネントが含まれています。
 
|コンポーネント|Description|  
|---------------|-----------------|  
|msodbcsql17.dll or <br> msodbcsql13.dll or <br> msodbcsql11.dll|ドライバーのすべての機能を含む DLL (ダイナミック リンク ライブラリ) ファイル。 このファイルは、%SYSTEMROOT%\System32 にインストールされます。|  
|msodbcdiag17.dll または <br> msodbcdiag13.dll または <br> msodbcdiag11.dll|ドライバーの診断 (トレース) インターフェイスが含まれるダイナミック リンク ライブラリ (DLL) ファイル。 このファイルは、%SYSTEMROOT%\System32 にインストールされます。|
|msodbcsqlr17.rll or <br> msodbcsqlr13.rll or <br> msodbcsqlr11.rll|ドライバー ライブラリに付随するリソース ファイル。 このファイルは、SYSTEMROOT%\System32\1033 にインストールされます。| 
|s13ch_msodbcsql.chm or <br> s11ch_msodbcsql.chm |ドライバーのデータ ソースを作成する方法が説明されているデータ ソース ウィザードのヘルプ ファイルです。 このファイルは %SYSTEMROOT%\System32\1033 にインストールします。 <br /> <br /> **注:** ODBC ドライバーの 17 chm ファイルはありません。 |  
|msodbcsql.h|すべてのドライバーを使用するために必要な新しい定義を含むヘッダー ファイル。<br /><br /> **注:**  msodbcsql.h と odbcss.h を同じプログラムで参照することはできません。<br /><br /> ODBC ドライバーの 17 または 13 msodbcsql.h は %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\130\SDK にインストールされます。 <br /> ODBC Driver 11 の msodbcsql.h は %PROGRAMFILES%\Microsoft SQL Server\Client \odbc\110\sdk にインストールされます。| 
|msodbcsql17.lib or <br> msodbcsql13.lib or <br> msodbcsql11.lib|呼び出しに必要なライブラリ ファイル、 **bcp**ユーティリティ関数は、ドライバーの一部であります。<br /><br /> **注:** プログラムでこのライブラリ ファイルを参照する場合は、システム パスでは、アプリケーションを使用してこれらのシステム パスにあることを確認してください。<br /><br /> msodbcsql17.lib or msodbcsql13.lib is installed in %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\130\SDK.<br /> msodbcsql11.lib は %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\110\SDK にインストールされます。|

  
## <a name="see-also"></a>参照  
 [Microsoft ODBC Driver for SQL Server on Windows](../../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)  
  
  
