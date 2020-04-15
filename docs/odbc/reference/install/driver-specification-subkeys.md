---
title: ドライバ仕様サブキー |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- subkeys [ODBC], driver specification subkeys
- driver specification subkeys [ODBC]
- registry entries for components [ODBC], driver specification subkeys
- drivers subkey [ODBC]
ms.assetid: b4d802ef-b199-4e64-b7a5-6f2b3e5e2c80
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 47aa75f647e5fd8a88168611a3b21284962c70a4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280582"
---
# <a name="driver-specification-subkeys"></a>ドライバーの仕様のサブキー
ODBC ドライバ サブキーに表示される各ドライバには、独自のサブキーがあります。 このサブキーは、ODBC ドライバ サブキーの下の対応する値と同じ名前を持ちます。 このサブキーの値には、ドライバーとドライバーセットアップ DLL の完全なパス **、SQLDrivers**によって返されるドライバー キーワードの値、および使用カウントが一覧表示されます。 値の形式は、次の表に示すとおりです。  
  
|名前|データ型|Data|  
|----------|---------------|----------|  
|アピレレベル|REG_SZ|**0** &#124; **1** &#124; **2**|  
|関数を接続する|REG_SZ|{**Y**&#124;**N**}**Y**&#124;**N**}**Y**&#124;**N**}|  
|DSN を作成します。|REG_SZ|*ドライバーの説明*|  
|Driver|REG_SZ|*ドライバ DLL パス*|  
|DriverODBCVer|REG_SZ|*nn.nn*|  
|ファイルの拡張|REG_SZ|**\*.** *ファイル拡張子1*[**\*, .** *ファイル拡張子2]*...|  
|ファイルの使用法|REG_SZ|**0** &#124; **1** &#124; **2**|  
|セットアップ|REG_SZ|*DLL パスのセットアップ*|  
|SQL レベル|REG_SZ|**0** &#124; **1** &#124; **2**|  
|使用カウント|REG_DWORD|*count*|  
  
 各キーワードの使用を次の表に示します。  
  
|Keyword|使用法|  
|-------------|-----------|  
|**アピレレベル**|ドライバがサポートする ODBC インターフェイスの準拠レベルを示す数値。<br /><br /> 0 = なし<br /><br /> 1 = レベル 1 がサポートされる<br /><br /> 2 = レベル 2 がサポートされています<br /><br /> これは **、SQLGetInfo**の SQL_ODBC_INTERFACE_CONFORMANCE オプションに対して返される値と同じである必要があります。|  
|**DSN を作成します。**|ドライバーのインストール時に作成される 1 つ以上のデータ ソースの名前。 システム情報には **、CreateDSN**キーワードでリストされた各データ・ソースごとに、1 つのデータ・ソース仕様セクションが含まれている必要があります。 これらのセクションには、ドライバーの仕様のセクションで指定されているが、ダイアログ ボックスを表示せずにデータ ソースの仕様を作成するドライバー のセットアップ DLL の**ConfigDSN**関数のための十分な情報を含める必要があるため **、Driver**キーワードを含めないようにする必要があります。 データ ソース仕様のセクションの形式については、「[データ ソース仕様サブキー](../../../odbc/reference/install/data-source-specification-subkeys.md)」を参照してください。|  
|**関数を接続する**|ドライバーが**SQL 接続、SQL**ドライバー接続、および**SQLBrowseConnect**をサポートしているかどうかを示す 3 文字の文字列。 **SQLDriverConnect** ドライバーが**SQLConnect**をサポートしている場合、最初の文字は "Y" です。それ以外の場合は"N"です。 ドライバーが**SQLDriverConnect**をサポートしている場合、2 番目の文字は "Y" です。それ以外の場合は"N"です。 ドライバーが**SQLBrowseConnect**をサポートしている場合、3 番目の文字は "Y" です。それ以外の場合は"N"です。 たとえば、ドライバーが SQL**接続**と**SQL ドライバー接続**をサポートしているが **、SQLBrowseConnect**をサポートしていない場合、3 文字の文字列は "YYN" です。|  
|**DriverODBCVer**|ドライバーがサポートする ODBC のバージョンを含む文字列。 バージョンは*nn.nn*の形式で、最初の 2 桁はメジャー バージョンで、次の 2 桁はマイナー バージョンです。 このマニュアルで説明されている ODBC のバージョンでは、ドライバーは"03.00"を返す必要があります。<br /><br /> これは **、SQLGetInfo**の SQL_DRIVER_ODBC_VER オプションに対して返される値と同じである必要があります。|  
|**ファイルの拡張**|ファイル ベースのドライバーの場合は、ドライバーが使用できるファイルの拡張子のコンマ区切りの一覧。 たとえば、dBASE ドライバーが .dbf を指定\*し、書式設定されたテキスト ファイル\*ドライバーが\*.txt、.csv を指定する場合があります。 アプリケーションがこの情報をどのように使用するかを示す例については **、FileUsage**キーワードを参照してください。|  
|**ファイルの使用法**|ファイル ベースのドライバーがデータ ソース内のファイルを直接処理する方法を示す数値。<br /><br /> 0 = ドライバはファイル ベースのドライバではありません。 たとえば、ORACLE ドライバは DBMS ベースのドライバです。<br /><br /> 1 = ファイルベースのドライバは、データソース内のファイルをテーブルとして扱います。 たとえば、Xbase ドライバは、各 Xbase ファイルをテーブルとして扱います。<br /><br /> 2 = ファイルベースのドライバは、データ ソース内のファイルをカタログとして扱います。 たとえば、Access ® ドライバは、各 Access ファイルを完全なデータベースとして扱います。<br /><br /> アプリケーションでは、これを使用して、ユーザーがデータを選択する方法を決定できます。 たとえば、Xbase および Paradox ユーザーはデータをファイルに格納すると考えることがよくありますが、ORACLE および Access ユーザーは通常、データをテーブルに格納すると考えます。<br /><br /> ユーザーが [**ファイル]** メニューの **[データ ファイルを開く**] を選択すると、アプリケーションで **[Windows ファイルを開く]** コモン ダイアログ ボックスが表示される場合があります。 ファイルの種類の一覧では **、FileUsage**値 1 と "Y" を指定するドライバーの**FileExtns**キーワードで指定されたファイル拡張子を ConnectFunctions キーワードの値の 2 番目の文字として使用します。 **FileUsage** ユーザーがファイルを選択すると、アプリケーションは **、ドライバー**キーワードを使用して**SQLDriverConnect**を呼び出し、**\**テーブル名*** の SELECT を実行します。<br /><br /> ユーザーが **[ファイル]** メニューから **[データのインポート**] を選択すると、**アプリケーションは、FileUsage**値 0 または 2 を指定し **、ConnectFunctions**キーワードの値の 2 番目の文字として "Y" を指定するドライバーの説明の一覧を表示できます。 ユーザーがドライバーを選択すると、アプリケーションは **、ドライバー**キーワードを使用して**SQLDriverConnect**を呼び出し、カスタム**テーブルの選択**ダイアログ ボックスを表示します。|  
|**SQL レベル**|ドライバーでサポートされている SQL-92 文法を示す数値:<br /><br /> 0 = SQL-92 エントリ<br /><br /> 1 = FIPS127-2 移行期<br /><br /> 2 = SQL-92 中間体<br /><br /> 3 = SQL-92 フル<br /><br /> これは **、SQLGetInfo**のSQL_SQL_CONFORMANCE オプションに対して返される値と同じである必要があります。|  
  
 使用カウントの詳細については、このセクションの「[使用カウント](../../../odbc/reference/install/usage-counting.md)」を参照してください。  
  
 アプリケーションでは、使用カウントを設定しないでください。 ODBC はこのカウントを維持します。  
  
 たとえば、フォーマットされたテキスト ファイルのドライバーに、Text.dll という名前のドライバ DLL が含まれ、Txtsetup.dll という別のドライバ セットアップ DLL があり、3 回インストールされているとします。 ドライバーがレベル 1 API 準拠レベルをサポートし、最小 SQL 文法準拠レベルをサポートし、ファイルをテーブルとして扱い、.txt および .csv 拡張子のファイルを使用できる場合、Text サブキーの下の値は次のようになります。  
  
```  
APILevel : REG_SZ : 1  
ConnectFunctions : REG_SZ : YYN  
Driver : REG_SZ : C:\WINDOWS\SYSTEM32\TEXT.DLL  
DriverODBCVer : REG_SZ : 03.00.00  
FileExtns : REG_SZ : *.txt,*.csv  
FileUsage : REG_SZ : 1  
Setup : REG_SZ : C:\WINDOWS\SYSTEM32\TXTSETUP.DLL  
SQLLevel : REG_SZ : 0  
UsageCount : REG_DWORD : 0x3  
```
