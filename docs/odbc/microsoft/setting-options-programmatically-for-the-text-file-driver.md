---
title: "プログラムによってテキスト ファイルのドライバーのオプションの設定 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text file driver [ODBC], setting options programmatically
- ODBC desktop database drivers [ODBC], text file driver
- desktop database drivers [ODBC], text file driver
- Jet-based ODBC drivers [ODBC], text file driver
ms.assetid: cbde2ca1-5d4e-4444-a371-a72f3ac4d92a
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5b8127a7249f9f878dcd3d15b9afa874def8c64a
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="setting-options-programmatically-for-the-text-file-driver"></a>プログラムによってテキスト ファイルのドライバーのオプションの設定
|オプション|Description|方法|  
|------------|-----------------|------------|  
|Data Source Name|給与担当者など、データ ソースを識別する名前。|このオプションを動的に設定するには、使用、 **DSN**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)です。|  
|書式を定義します。|表示、**テキスト形式の定義** ダイアログ ボックス データ ソース ディレクトリ内の個々 のテーブルのスキーマを指定することができます。|このオプションへの呼び出しによって動的に設定することはできません[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)です。|  
|Description|データ ソース内のデータの説明 (オプション)たとえば、「雇用日、給与履歴、およびすべての従業員の現在のレビューします。」|このオプションを動的に設定するには、使用、**説明**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)です。|  
|ディレクトリ|対象となるディレクトリを選択します。|このオプションを動的に設定するには、使用、 **DEFAULTDIR**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)です。|  
|拡張機能の一覧|データ ソース上のテキスト ファイルのファイル名拡張子の一覧を表示します。 テキストのドライバーを使用する場合、CREATE TABLE ステートメントを実行する名前に拡張子を持たない拡張子のないファイルが作成されます。 その他のドライバーは、拡張子が指定されていない場合、既定の拡張子を持つファイルを作成します。 .Txt 拡張子を持つファイルを作成するには、名前で、拡張機能を含める必要があります。 拡張子のないファイルを表示する、**テキスト形式の定義**ダイアログ ボックスで、"* です"。 拡張機能の一覧に追加する必要があります。|このオプションを動的に設定するには、使用、**拡張**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)です。|  
|[読み取り専用]|読み取り専用で、データベースを指定します。|このオプションを動的に設定するには、使用、 **READONLY**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)です。|  
|スキャンする行数|各列のデータ型を決定するをスキャンする行の数。 検出データの種類の最大数を指定されたデータ型が決定されます。 データは、検出した場合、列のデータ型に一致しないデータ型は、NULL 値として返されます。<br /><br /> テキスト ドライバーの可能性があります番号を入力する、1 から 32767 まで; をスキャンする行の数ただし、この値は常に既定値 25。 (制限外の数値はエラーを返します。)|このオプションを動的に設定するには、使用、 **MAXSCANROWS**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)です。|  
|ディレクトリを選択します。|アクセスするファイルを含むディレクトリを選択 ダイアログ ボックスが表示されます。<br /><br /> データ ソース ディレクトリを定義すると、最もよく使用されているファイル ディレクトリをどのように指定する場合は、配置されます。 ODBC ドライバーは、このディレクトリを既定のディレクトリとして使用します。 頻繁に使用される場合は、その他のファイルをこのディレクトリにコピーします。 または、ディレクトリの名前で、SELECT ステートメント内のファイル名を修飾することができます。`SELECT * FROM C:\MYDIR\EMP`<br /><br /> またはを使用して新しい既定のディレクトリを指定することができます、 **SQLSetConnectOption**関数 SQL_CURRENT_QUALIFIER オプションを使用します。|このオプションを動的に設定するには、使用、 **DEFAULTDIR**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)です。|
