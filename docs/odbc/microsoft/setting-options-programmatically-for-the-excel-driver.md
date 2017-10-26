---
title: "Excel ドライバーのプログラムでオプションの設定 |Microsoft ドキュメント"
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
- Jet-based ODBC drivers [ODBC], Excel driver
- desktop database drivers [ODBC], Excel driver
- ODBC desktop database drivers [ODBC], Excel driver
- Excel driver [ODBC], setting options programmatically
ms.assetid: b5ee3636-4591-427a-a65a-a2d5926fcc1a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: da1f2ed6bbca3709c8223713f4841ed34288f5a3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="setting-options-programmatically-for-the-excel-driver"></a>Excel ドライバーのプログラムでオプションの設定
|オプション|Description|方法|  
|------------|-----------------|------------|  
|Data Source Name|給与担当者など、データ ソースを識別する名前。|このオプションを動的に設定するには、使用、 **DSN**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md)です。|  
|データベース|Microsoft Access データ ソースは、選択するか、データベースを作成することがなくを設定できます。 セットアップ時にデータベースが指定されていない場合は、データベース ファイルを選択して、データ ソースに接続するときに、ユーザーが求められます。|このオプションを動的に設定するには、使用、 **DBQ**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md)です。|  
|Description|データ ソース内のデータの説明 (オプション)たとえば、「雇用日、給与履歴、およびすべての従業員の現在のレビューします。」|このオプションを動的に設定するには、使用、**説明**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md)です。|  
|ディレクトリ|現在選択されているディレクトリを表示します。<br /><br /> Excel 3.0 と 4.0 ファイルのパスの表示のラベルは"Directory"、Microsoft Excel 5.0 の中に 7.0、または 97 のファイル パス表示というラベルが付いた「ブック」です。|このオプションを動的に設定するには、使用、 **DEFAULTDIR**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md)です。|  
|[読み取り専用]|読み取り専用で、データベースを指定します。|このオプションを動的に設定するには、使用、 **READONLY**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md)です。|  
|スキャンする行数|各列のデータ型を決定するをスキャンする行の数。 検出データの種類の最大数を指定されたデータ型が決定されます。 データは、検出した場合、列のデータ型に一致しないデータ型は、NULL 値として返されます。<br /><br /> Excel ドライバーをスキャンする行を 16 に、1 から番号を入力できます。 値の既定値は 8 です。0 に設定されている場合は、すべての行がスキャンされます。 (制限外の数値はエラーを返します。)|このオプションを動的に設定するには、使用、 **MAXSCANROWS**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md)です。|  
|ディレクトリを選択します。|アクセスするファイルを含むディレクトリを選択 ダイアログ ボックスが表示されます。<br /><br /> (すべてのドライバー Microsoft Access を除く) のデータ ソース ディレクトリを定義するときに、最もよく使用されるファイルが配置されているディレクトリを指定します。 ODBC ドライバーは、このディレクトリを既定のディレクトリとして使用します。 頻繁に使用される場合は、その他のファイルをこのディレクトリにコピーします。 または、ディレクトリの名前で、SELECT ステートメント内のファイル名を修飾することができます。<br /><br /> 選択\*C:\MYDIR\EMP から<br /><br /> またはを使用して新しい既定のディレクトリを指定することができます、 **SQLSetConnectOption**関数 SQL_CURRENT_QUALIFIER オプションを使用します。<br /><br /> Microsoft Excel 3.0 または 4.0 ファイルは、"Directory"というラベルが付いたパスの表示と"選択 Directory"というラベルが付いたパスの選択 ボタンをクリックします。 5.0、7.0、または 97 Microsoft Excel ファイルの「ブック」というラベルが付いたパスの表示と「ブックの選択」というラベルが付いたパスの選択 ボタンをクリックします。 データ ソース ディレクトリを定義するときに、最もよく使用される Microsoft Excel ファイルがあるディレクトリを Microsoft Excel 3.0 と 4.0、またはブック ファイルが Microsoft Excel 5.0、7.0、または 97 のあるディレクトリを指定します。 **現在のディレクトリを使用して**5.0、7.0、および 97 Microsoft Excel は無効になります。|このオプションを動的に設定するには、使用、 **DEFAULTDIR**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md)です。|

