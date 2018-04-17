---
title: SQL Server Express LocalDB ヘッダーとバージョン情報 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: localdb
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apilocation:
- sqluserinstance.dll
ms.assetid: 506b5161-b902-4894-b87b-9192d7b1664a
caps.latest.revision: 16
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e261b75d2746ac24cd8520d67ebc3d6d7d5c09f2
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sql-server-express-localdb-header-and-version-information"></a>SQL Server Express LocalDB ヘッダーとバージョン情報
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  SQL Server Express LocalDB インスタンス API には、独立したヘッダー ファイルはありません。LocalDB の関数署名とエラー コードは、SQL Server Native Client ヘッダー ファイル (sqlncli.h) に定義されています。 LocalDB インスタンス API を使用するには、プロジェクトに sqlncli.h ヘッダー ファイルをインクルードする必要があります。  
  
## <a name="localdb-versioning"></a>LocalDB のバージョン管理  
 LocalDB インストールでは、主要な SQL Server バージョンごとの単一のバイナリ セットを使用します。 これらの LocalDB バージョンは維持され、個別にパッチが適用されます。 つまり、ユーザーはどの LocalDB ベースライン リリース (主要な SQL Server バージョン) を使用するのかを指定する必要があるということです。 バージョンは、.NET Framework で定義されている標準バージョンの形式で指定される**System.Version**クラス。  
  
 *[.revision]*  
  
 バージョン文字列の最初の 2 つの番号 (*メジャー*と*マイナー*) は必須です。 バージョン文字列の最後の 2 つの番号 (*ビルド*と*リビジョン*) はオプションであり場合は、ユーザーが既定で 0 にします。つまり、ユーザーが LocalDB バージョン番号として "12.2" だけを指定した場合、"12.2.0.0" と指定したように扱われます。  
  
 LocalDB インストールのバージョンは、SQL Server インスタンス レジストリ キーの下の MSSQLServer\CurrentVersion レジストリ キーに定義されます。次に例を示します。  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\MSSQL13E.LOCALDB\ MSSQLServer\CurrentVersion: "CurrentVersion"="12.0.2531.0"  
```  
  
 同じ 1 台のワークステーション上で複数の LocalDB バージョンが同時にサポートされます。 ただし、ユーザー コード常に使用して、利用可能な最新**SQLUserInstance** LocalDB インスタンスに接続するローカル コンピューター上の DLL。  
  
## <a name="locating-the-sqluserinstance-dll"></a>SQLUserInstance DLL の検索  
 検索する、 **SQLUserInstance** DLL は、クライアント プロバイダーが次のレジストリ キーを使用します。  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server Local DB\Installed Versions]  
```  
  
 このキーの下に、キーのリストがあります。このコンピューターにインストールされている LocalDB のバージョンごとに 1 つのキーがあります。 形式で LocalDB バージョン番号を持つ名前はこれらの各キー *\<メジャー バージョン >*.*\<マイナー バージョン >* (たとえば、キーを[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]13.0.< をという名前)。 各バージョン キーの下に、`InstanceAPIPath` の名前と値のペアが 1 つあります。このペアは、そのバージョンでインストールされた SQLUserInstance.dll ファイルの絶対パスを定義します。 次の例は、LocalDB バージョン 11.0 と 13.0.< がインストールされているコンピューターのレジストリ エントリを示しています。  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server Local DB\Installed Versions\13.0]  
"InstanceAPIPath"="C:\\Program Files\\Microsoft SQL Server\\130\\LocalDB\\Binn\\SqlUserInstance.dll"  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server Local DB\Installed Versions\13.0]  
"InstanceAPIPath"="C:\\Program Files\\Microsoft SQL Server\\130\\LocalDB\\Binn\\SqlUserInstance.dll"]  
```  
  
 クライアント プロバイダーがインストールされているすべてのバージョンおよびロードの中で最新バージョンを見つける必要があります、 **SQLUserInstance** DLL ファイルが関連付けられている`InstanceAPIPath`値。  
  
### <a name="wow64-mode-on-64-bit-windows"></a>64 ビット版 Windows 上の WOW64 モード  
 LocalDB の 64 ビット インストールには、追加のレジストリ キー セットがあるため、Windows-32-on-Windows-64 (WOW64) モードで実行される 32 ビット版アプリケーションで LocalDB を使用することができます。 具体的には、64 ビット版 Windows では、LocalDB MSI が次のレジストリ キーを作成します。  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wow6432Node\Microsoft SQL Server Local DB\Installed Versions\13.0]  
"InstanceAPIPath"="C:\\Program Files (x86)\\Microsoft SQL Server\\130\\LocalDB\\Binn\\SqlUserInstance.dll"  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wow6432Node\Microsoft SQL Server Local DB\Installed Versions\13.0]  
"InstanceAPIPath"="C:\\Program Files (x86)\\Microsoft SQL Server\\130\\LocalDB\\Binn\\SqlUserInstance.dll"]  
  
```  
  
 読み取る 64 ビット プログラム、`Installed Versions`キーは 64 ビット バージョンを指す値を参照してください、 **SQLUserInstance** DLL、32 ビット プログラム (WOW64 モードの 64 ビット Windows で実行されている) が自動的にリダイレクトするときに、`Installed Versions`キーの下にある、 `Wow6432Node` hive します。 このキーには、32 ビット バージョンを指す値が含まれています、 **SQLUserInstance** DLL です。  
  
## <a name="using-localdbdefineproxyfunctions"></a>LOCALDB_DEFINE_PROXY_FUNCTIONS の使用  
 LocalDB インスタンス API は、の検出と読み込みを自動化する LOCALDB_DEFINE_PROXY_FUNCTIONS という名前の定数を定義、 **SqlUserInstance** DLL です。  
  
 この定数によって有効化されるコードのセクションにより、各 LocalDB API のプロキシが実装されます。 プロキシの実装では、共通の関数を使用して、最新バージョンがインストールされている内のエントリ ポイントをバインド**SqlUserInstance** DLL、要求を転送します。  
  
 プロキシ関数が有効化されるのは、定数 LOCALDB_DEFINE_PROXY_FUNCTIONS がユーザー コードで定義された後に、sqlncli.h ファイルがインクルードされた場合だけです。 この定数は、すべての API エントリ ポイントの外部関数名を定義するので、1 つのソース モジュール (.cpp ファイル) だけに定義する必要があります。 この定数により、各 LocalDB API のプロキシが実装されます。  
  
 次のコード例では、ネイティブの C++ コードのマクロを使用する方法を示します。  
  
```  
// Define the LOCALDB_DEFINE_PROXY_FUNCTIONS constant to enable the LocalDB proxy functions   
// The #define has to take place BEFORE the API header file (sqlncli.h) is included  
#define LOCALDB_DEFINE_PROXY_FUNCTIONS  
#include <sqlncli.h>  
…  
HRESULT hr = S_OK;  
  
// Create LocalDB instance by calling the create API proxy function included by macro  
if (FAILED(hr = LocalDBCreateInstance( L"12.0", L"name", 0)))  
{  
…  
}  
…  
  
```  
  
  
