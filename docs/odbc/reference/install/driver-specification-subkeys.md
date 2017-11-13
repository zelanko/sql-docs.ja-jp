---
title: "ドライバーの仕様のサブキー |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- subkeys [ODBC], driver specification subkeys
- driver specification subkeys [ODBC]
- registry entries for components [ODBC], driver specification subkeys
- drivers subkey [ODBC]
ms.assetid: b4d802ef-b199-4e64-b7a5-6f2b3e5e2c80
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f45130c81f9fc4f669cf95d4bde72155f519c1aa
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="driver-specification-subkeys"></a>ドライバーの仕様のサブキー
ODBC ドライバーのサブキーに表示されている各ドライバーでは、独自のサブキーがあります。 このサブキーは、ODBC ドライバーのサブキーの下の対応する値として同じ名前を持ちます。 このサブキーの下の値は、ドライバーとドライバーのセットアップ Dll の場合、によって返されるドライバー キーワードの値の完全パスを一覧表示**SQLDrivers**、および使用状況カウントします。 値の形式は、次の表に示すようにします。  
  
|名前|データ型|data|  
|----------|---------------|----------|  
|APILevel|REG_SZ|**0** &#124; **1** &#124; **2**|  
|ConnectFunctions|REG_SZ|{**Y**&#124;**N**} {**Y**&#124;**N**} {**Y**&#124;**N**}|  
|CreateDSN|REG_SZ|*ドライバーの説明*|  
|Driver|REG_SZ|*ドライバー DLL パス*|  
|DriverODBCVer|REG_SZ|*nn.nn*|  
|FileExtns|REG_SZ|**\*.** *ファイル extension1*[**、\*です。** *ファイル extension2*].|  
|FileUsage|REG_SZ|**0** &#124; **1** &#124; **2**|  
|セットアップ|REG_SZ|*セットアップ DLL パス*|  
|SQLLevel|REG_SZ|**0** &#124; **1** &#124; **2**|  
|UsageCount|REG_DWORD|*count*|  
  
 各キーワードの使用は、次の表に表示されます。  
  
|Keyword|使用方法|  
|-------------|-----------|  
|**APILevel**|ODBC を示す数値インターフェイスのドライバーでサポートされている準拠レベル。<br /><br /> 0 = なし<br /><br /> 1 = レベル 1 のサポート<br /><br /> 2 レベル 2 のサポートを =<br /><br /> SQL_ODBC_INTERFACE_CONFORMANCE オプションに返される値と同じでなければなりません**SQLGetInfo**です。|  
|**CreateDSN**|ドライバーのインストール時に作成される 1 つまたは複数のデータ ソースの名前。 システム情報と共に一覧表示するデータ ソースごとに 1 つのデータ ソースの仕様セクションを含める必要があります、 **CreateDSN**キーワード。 これらのセクションを含めることはできません、**ドライバー**キーワード、ドライバの仕様のセクションで指定されたのに十分な情報を含める必要がありますこのため、 **ConfigDSN**ドライバーで関数すべてのダイアログ ボックスを表示することがなくデータ ソースの指定を作成する DLL をセットアップします。 データ ソースの仕様のセクションの形式の場合、次を参照してください。[データ ソースの仕様のサブキー](../../../odbc/reference/install/data-source-specification-subkeys.md)です。|  
|**ConnectFunctions**|ドライバーをサポートするかどうかを示す 3 文字の文字列**SQLConnect**、 **SQLDriverConnect**、および**SQLBrowseConnect**です。 ドライバーがサポートする場合は**SQLConnect**、最初の文字"Y"です。 それ以外の場合は"N"です。 ドライバーがサポートする場合は**SQLDriverConnect**、2 番目の文字"Y"です。 それ以外の場合は"N"です。 ドライバーがサポートする場合は**SQLBrowseConnect**、3 番目の文字"Y"です。 それ以外の場合は"N"です。 たとえば、ドライバーをサポートしている場合**SQLConnect**と**SQLDriverConnect**ではなく**SQLBrowseConnect**、3 文字の文字列は"YYN"です。|  
|**DriverODBCVer**|ドライバーがサポートする ODBC のバージョンと文字の文字列。 形式は、バージョン*nn.nn*、ここで最初の 2 つの数字、メジャー バージョンとは、次の 2 つの数字はマイナー バージョン。 このマニュアルで説明されている ODBC のバージョン、ドライバーは「03.00」返す必要があります。<br /><br /> SQL_DRIVER_ODBC_VER オプションに返される値と同じでなければなりません**SQLGetInfo**です。|  
|**FileExtns**|ファイル ベースのドライバーでは、ファイルの拡張子のコンマ区切りの一覧、ドライバー使用できます。 たとえば、dBASE ドライバー指定\*.dbf と書式設定されたテキスト ファイルのドライバーを指定する\*.txt、\*.csv です。 アプリケーションがこの情報の使用方法の例は、次を参照してください。、 **FileUsage**キーワード。|  
|**FileUsage**|ファイル ベースのドライバーが直接データ ソース内のファイルを扱う方法を示す数値です。<br /><br /> 0 = ドライバーは、ファイル ベースのドライバーではありません。 たとえば、ORACLE ドライバは、DBMS に基づいたドライバーです。<br /><br /> 1 = テーブルとしてのデータ ソースのドライバーのファイル ベース扱いますファイル。 たとえば、Xbase ドライバーでは、各 Xbase ファイルがテーブルとして扱われます。<br /><br /> 2 = カタログとしてデータ ソース内のファイル ベースのドライバー扱いますファイル。 たとえば、Microsoft® Access ドライバーでは、Microsoft Access の各ファイルが完全なデータベースとして扱われます。<br /><br /> アプリケーションは、ユーザーがデータを選択する方法を決定するのにこれを使用できます。 たとえば、Xbase および Paradox ユーザーは、ORACLE および Microsoft Access のユーザーと考えることデータのテーブルに格納されているときに、ファイルでは、格納されているデータの多くの場合、想定できます。<br /><br /> ユーザーが選択すると**データ ファイルを開く**から、**ファイル**] メニューの [アプリケーションの表示をでした、 **Windows File Open**コモン ダイアログ ボックス。 ファイルの種類の一覧がで指定されたファイル拡張子を使用して、 **FileExtns**キーワードを指定するドライバーに対して、 **FileUsage** 1 と 2 番目の文字の値として"Y"の値、 **ConnectFunctions**キーワード。 アプリケーションを呼び出すと、ユーザーは、ファイルを選択し、 **SQLDriverConnect**で、**ドライバー**キーワードし、実行、**選択\*FROM*テーブル名*** ステートメントです。<br /><br /> ユーザーが選択すると**データのインポート**から、**ファイル**] メニューの [アプリケーション表示を指定するドライバーの説明の一覧、 **FileUsage** 0 または 2、および"Y"の値値の 2 番目の文字として、 **ConnectFunctions**キーワード。 アプリケーションを呼び出すと、ユーザーは、ドライバーを選択し、 **SQLDriverConnect**で、**ドライバー**キーワードと、表示するカスタム**テーブルの選択** ダイアログ ボックス。|  
|**SQLLevel**|ドライバーでサポートされている SQL 92 文法を示す数値。<br /><br /> 0 = SQL 92 エントリ<br /><br /> 1 = FIPS127-2 の移行<br /><br /> 2 = SQL 92 中間<br /><br /> 3 = sql-92 Full<br /><br /> SQL_SQL_CONFORMANCE オプションに返される値と同じでなければなりません**SQLGetInfo**です。|  
  
 使用状況カウントの詳細については、次を参照してください。[使用状況カウント](../../../odbc/reference/install/usage-counting.md)このセクションで前述しました。  
  
 アプリケーションでは、使用率カウントは設定しないでください。 ODBC では、この数が維持されます。  
  
 たとえば、書式設定されたテキスト ファイル用のドライバーをドライバー Text.dll をという名前の DLL があると仮定します個別のドライバー セットアップ DLL Txtsetup.dll、という名前し、3 回がインストールされています。 場合、ドライバー レベル 1 の API への準拠レベルをサポートして、Minimum SQL 文法の準拠レベルをサポートしているはファイル テーブルとして扱います .txt、.csv の拡張子を持つファイルを使用することができます、テキストのサブキーの下の値可能性がありますとおり。  
  
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

