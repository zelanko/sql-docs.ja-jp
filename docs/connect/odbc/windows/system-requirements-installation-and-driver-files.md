---
title: システム要件、インストール、およびドライバー ファイル | Microsoft Docs
ms.custom: ''
ms.date: 02/14/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d90fa182-1dab-4d6f-bd85-a04dd1479986
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cfbf0ef8a02695a2bc3a1870a2660cf2bff23b7d
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2018
ms.locfileid: "42785186"
---
# <a name="system-requirements-installation-and-driver-files"></a>インストール、ドライバー ファイルの基本的なシステム要件
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は、SQL Server 2014、SQL Server 2012 R2、 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssKatmai](../../../includes/sskatmai_md.md)]、 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]への接続をサポートします。  
  
ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on Windows は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client の 1 つまたは複数のバージョンもインストールされているコンピューターにインストールできます。  
  
ODBC Driver 13 および 13.1 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]、上記のほか、SQL Server 2016 をサポートしています。 

ODBC Driver 17 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] SQL Server 2017 と上記のすべてのものをサポートしています。
  
接続文字列で指定したドライバー名は`ODBC Driver 11 for SQL Server`または`ODBC Driver 13 for SQL Server`(13 と 13.1 の両方) に対してまたは`ODBC Driver 17 for SQL Server`します。
  
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
  
## <a name="installing-microsoft-odbc-driver-for-sql-server"></a>Microsoft ODBC Driver for SQL Server のインストール

実行すると、ドライバーがインストールされている`msodbcsql.msi`から、次のリンクのいずれか。

- [Windows で Microsoft ODBC Driver 17 for SQL Server をダウンロードする](https://www.microsoft.com/download/details.aspx?id=56567)
- [Microsoft ODBC Driver 13.1 for SQL Server on Windows のダウンロード](https://www.microsoft.com/download/details.aspx?id=53339)
- [Microsoft ODBC Driver 13 for SQL Server on Windows のダウンロード](https://www.microsoft.com/download/details.aspx?id=50420)
- [Microsoft ODBC Driver 11 for SQL Server on Windows のダウンロード](https://www.microsoft.com/download/details.aspx?id=36434)。 

[!NOTE]
ドライバー インストール 17.1.0.1 を持っているものをお勧め、それをアンインストールする手動でドライバー 17.2.0.1 をインストールする前に、またはの上

[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client とサイド バイ サイドでインストールできます。  

`msodbcsql.msi` を呼び出すと、既定ではクライアント コンポーネントのみがインストールされます。 クライアント コンポーネントは、ドライバーを使用して開発されたアプリケーションの実行をサポートするファイルです。 SDK コンポーネントをインストールするには、コマンド ラインで `ADDLOCAL=ALL` を指定します。 例 :  
  
```  
msiexec /i msodbcsql.msi ADDLOCAL=ALL  
```  
  
 `/passive`、`/qn`、`/qb`、または `/qr` オプションを使用してインストールする場合は、`IACCEPTMSODBCSQLLICENSETERMS=YES` を指定してエンド ユーザー ライセンスの条項に同意します。 このオプションは、すべて大文字で指定する必要があります。 例 :  
  
```  
msiexec /quiet /passive /qn /i msodbcsql.msi IACCEPTMSODBCSQLLICENSETERMS=YES ADDLOCAL=ALL  
```  
  
 サイレント アンインストールを行うには:  
  
```  
msiexec /quiet /passive /qn /uninstall msodbcsql.msi  
```  
  
アプリケーションでは、ドライバーを使用する場合、`APPGUID` インストール オプションを使ってドライバーに依存していることを示す必要があります。 これにより、ドライバーのインストーラーは、アンインストールの前に依存するアプリケーションに通知できます。 ドライバーの依存関係を指定するには、ドライバーのサイレント インストールを行うときに `APPGUID` コマンド ライン パラメーターをご利用の製品コードに設定します  (Microsoft インストーラーを使用してアプリケーションのセットアップ プログラムをバンドルするときは、製品コードを作成する必要があります)。例 :  
  
```  
msiexec /i msodbcsql.msi APPGUID={ <Your dependent application's APPGUID> }  
```  

## <a name="command-line-tools-sqlcmdexe-and-bcpexe"></a>コマンド ライン ツール: sqlcmd.exe および bcp.exe

`bcp.exe`と`sqlcmd.exe`ドライバーで使用でダウンロード用のツールは[SQL Server 用 Microsoft Command Line Utilities 11](http://www.microsoft.com/download/details.aspx?id=36433)、 [Microsoft コマンド ライン ユーティリティ 13 for SQL Server](https://www.microsoft.com/download/details.aspx?id=52680)、または[Microsoft Command Line Utilities 13.1 for SQL Server](https://www.microsoft.com/download/details.aspx?id=53591)します。 ドライバーをインストールする前提条件は、`sqlcmd.exe`と`bcp.exe`します。
  
`bcp.exe` `sqlcmd.exe`にインストールされている、`110\Tools`のサブフォルダー`%PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC`バージョン 11、および`130\Tools`13 と 13.1 します。

BCP 関数を使用するアプリケーションでは、アプリケーションのコンパイルに使用したヘッダー ファイルおよびライブラリに付属するものと同じバージョンのドライバーを指定する必要があります。  

ODBC アプリケーションをコンパイルすると、`msodbcsql11.lib`と`msodbcsql.h`を使用して、"ドライバー = {ODBC Driver 11 for SQL Server}"接続文字列にします。

## <a name="components-of-the-microsoft-odbc-driver-for-includessnoversionincludesssnoversion-mdmd-on-windows"></a>Microsoft ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on Windows のコンポーネント 
 Windows 上の ODBC ドライバーには、次のコンポーネントが含まれています。
 
|コンポーネント|[説明]|  
|---------------|-----------------|  
|msodbcsql17.dll または <br> msodbcsql13.dll または <br> msodbcsql11.dll|ドライバーのすべての機能を含む DLL (ダイナミック リンク ライブラリ) ファイル。 このファイルは、SYSTEMROOT%\System32 にインストールされます。|  
|msodbcdiag17.dll または <br> msodbcdiag13.dll または <br> msodbcdiag11.dll|ドライバーの診断 (トレース) インターフェイスが含まれるダイナミック リンク ライブラリ (DLL) ファイル。 このファイルは、SYSTEMROOT%\System32 にインストールされます。|
|msodbcsqlr17.rll または <br> msodbcsqlr13.rll または <br> msodbcsqlr11.rll|ドライバー ライブラリに付随するリソース ファイル。 このファイルは、SYSTEMROOT%\System32\1033 にインストールされます。| 
|s13ch_msodbcsql.chm または <br> s11ch_msodbcsql.chm |ドライバーのデータ ソースを作成する方法が説明されているデータ ソース ウィザードのヘルプ ファイル。 このファイルは %SYSTEMROOT%\System32\1033 にインストールされます。 <br /> <br /> **注:** ODBC Driver 17 for chm ファイルはありません。 |  
|msodbcsql.h|ドライバーを使用するために必要な新しい定義がすべて含まれているヘッダー ファイル。<br /><br /> **注:**  msodbcsql.h と odbcss.h を同じプログラムで参照することはできません。<br /><br /> ODBC Driver 11 用の msodbcsql.h は、%PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\110\SDK にインストールされます。 <br /> ODBC Driver 11 用の msodbcsql.h は、%PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\110\SDK にインストールされます。| 
|msodbcsql17.lib または <br> msodbcsql13.lib または <br> msodbcsql11.lib|ドライバーの一部である **bcp** ユーティリティ関数を呼び出すために必要なライブラリ ファイル。<br /><br /> **注:**  ご利用のプログラムでこのライブラリ ファイルを参照する場合は、ライブラリ ファイルがシステム パス、およびアプリケーションを使用するプログラムのシステム パスに含まれることを確認してください。<br /><br /> msodbcsql17.lib や msodbcsql13.lib は、%PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\130\SDK にインストールされます。<br /> msodbcsql11.lib は %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\110\SDK にインストールされます。|

  
## <a name="see-also"></a>参照  
 [Microsoft ODBC Driver for SQL Server on Windows](../../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)  
  
  
