---
title: Excel ドライバーのプログラムでオプションの設定 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], Excel driver
- desktop database drivers [ODBC], Excel driver
- ODBC desktop database drivers [ODBC], Excel driver
- Excel driver [ODBC], setting options programmatically
ms.assetid: b5ee3636-4591-427a-a65a-a2d5926fcc1a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c62503611e88435b139a00b180d3e087769b7fda
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47786587"
---
# <a name="setting-options-programmatically-for-the-excel-driver"></a>Excel ドライバーのプログラムでオプションの設定
|オプション|説明|方法|  
|------------|-----------------|------------|  
|Data Source Name|給与または担当者など、データ ソースを識別する名前。|このオプションを動的に設定するには、使用、 **DSN**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md)します。|  
|[データベース]|Microsoft Access データ ソースは、選択するか、データベースを作成することがなく設定できます。 セットアップ時にデータベースが指定されていない場合、ユーザーは、データ ソースに接続するときに、データベース ファイルを選択を求めます。|このオプションを動的に設定するには、使用、 **DBQ**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md)します。|  
|説明|データ ソース内のデータの説明 (オプション)たとえば、"日付、給与履歴、およびすべての従業員の現在のレビュー。 hire"という|このオプションを動的に設定するには、使用、**説明**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md)します。|  
|ディレクトリ|現在選択されているディレクトリが表示されます。<br /><br /> Microsoft Excel 3.0 と 4.0 のファイルのパスの表示はラベルが付けられます"Directory"中に Microsoft Excel 5.0、7.0、または 97 のファイル パスの表示のラベルは「ブック」。|このオプションを動的に設定するには、使用、 **DEFAULTDIR**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md)します。|  
|[読み取り専用]|読み取り専用データベースを指定します。|このオプションを動的に設定するには、使用、 **READONLY**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md)します。|  
|スキャンする行|各列のデータ型を決定するをスキャンする行の数。 検出されたデータの種類の最大数を指定されたデータ型が決定されます。 列のデータ型に一致しないデータが発生した場合、データ型が NULL 値として返されます。<br /><br /> Microsoft Excel ドライバーの場合をスキャンする行を 16 に、1 から番号を入力できます。 値の既定値は 8 です。0 に設定されている場合は、すべての行がスキャンされます。 (上限外の数値はエラーを返します。)|このオプションを動的に設定するには、使用、 **MAXSCANROWS**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md)します。|  
|ディレクトリを選択します|アクセスするファイルを含むディレクトリを選択するダイアログ ボックスが表示されます。<br /><br /> (Microsoft Access を除くすべてのドライバー) のデータ ソース ディレクトリを定義するときに、最もよく使用されるファイルが配置されているディレクトリを指定します。 ODBC ドライバーは、このディレクトリを既定のディレクトリとして使用します。 頻繁に使用される場合は、その他のファイルをこのディレクトリにコピーします。 または、ディレクトリの名前を持つ SELECT ステートメント内のファイル名を修飾することができます。<br /><br /> 選択\*C:\MYDIR\EMP から<br /><br /> 使用して、新しい既定のディレクトリを指定することも、 **SQLSetConnectOption**関数 SQL_CURRENT_QUALIFIER オプションを使用します。<br /><br /> Microsoft Excel 3.0 または 4.0 ファイルの場合は、"Directory"というラベルが付いたパスの表示とパスの選択ボタンは「ディレクトリの選択」というラベルが付いたします。 Microsoft Excel 5.0、7.0、または 97 ファイルの場合「ブック」というラベルが付いたパスの表示とパスの選択ボタンは「ブックの選択」というラベルが付いたします。 データのソース ディレクトリを定義するときに、最もよく使用される Microsoft Excel ファイルがあるは、Microsoft Excel 3.0 または 4.0、ディレクトリまたはブック ファイルが Microsoft Excel 5.0、7.0、または 97 のあるディレクトリを指定します。 **現在のディレクトリを使用して、** for Microsoft Excel 5.0、7.0、および 97 は無効です。|このオプションを動的に設定するには、使用、 **DEFAULTDIR**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md)します。|
