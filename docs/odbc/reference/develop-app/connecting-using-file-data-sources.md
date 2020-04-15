---
title: ファイル データ ソースを使用して接続する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connecting to driver [ODBC], file data sources
- SQLDriverConnect function [ODBC], connecting using file data sources
- connecting to data source [ODBC], SQLDriverConnect
- connecting to driver [ODBC], SQLDriverConnect
- connecting to data source [ODBC], file data sources
- file data sources [ODBC]
ms.assetid: 3003f8c2-8be6-41cc-8d9c-612e9bd0f3ae
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8c752fc3b09c06c68dcc216cacac63744dc3101b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287412"
---
# <a name="connecting-using-file-data-sources"></a>ファイル データ ソースを使用した接続
ファイル データ ソースの接続情報は、.dsn ファイルに格納されます。 その結果、接続文字列は、1 人のユーザーが繰り返し使用したり、適切なドライバがインストールされている場合は複数のユーザー間で共有したりできます。 ファイルには、ドライバ名 (または共有できないファイル データ ソースの場合は別のデータ ソース名) と、オプションで**SQLDriverConnect**で使用できる接続文字列が含まれています。 ドライバー マネージャーは、.dsn ファイル内のキーワードから**SQLDriverConnect**への呼び出しの接続文字列をビルドします。  
  
 ファイル データ ソースを使用すると、アプリケーションは**SQLDriverConnect**で使用する接続文字列を作成しなくても接続オプションを指定できます。 通常、ファイル データ ソースは**SAVEFILE**キーワードを指定して作成され、ドライバー マネージャーは **、SQLDriverConnect**の呼び出しによって作成された出力接続文字列を .dsn ファイルに保存します。 この接続文字列は **、FILEDSN**キーワードを使用して**SQLDriverConnect**を呼び出すことによって繰り返し使用できます。 これにより、接続プロセスが合理化され、接続文字列の永続的なソースが提供されます。  
  
 ファイル データ ソースは、インストーラー DLL で**SQLCreateDataSource**を呼び出すことによっても作成できます。 情報は **、SQLWriteFileDSN**を呼び出すことによって .dsn ファイルに書き込まれ **、SQLReadFileDSN**を呼び出すことによって .dsn ファイルから読み取ることができます。これらの関数はどちらも、インストーラ DLL に含まれています。 インストーラ DLL の詳細については、「[データ ソースの設定」](../../../odbc/reference/install/configuring-data-sources.md)を参照してください。  
  
 接続情報に使用されるキーワードは、.dsn ファイルの [ODBC] セクションにあります。 共有可能な .dsn ファイルが [ODBC] セクションに含まれる最低限の情報は、DRIVER キーワードです。  
  
```  
DRIVER = SQL Server  
```  
  
 共有可能な .dsn ファイルには、通常、次のように接続文字列が含まれています。  
  
```  
DRIVER = SQL Server  
UID = Larry  
DATABASE = MyDB  
```  
  
 ファイル データ ソースが共有できない場合、.dsn ファイルには**DSN**キーワードのみが含まれます。 ドライバー マネージャーは、共有できないファイルのデータ ソース内の情報を送信すると **、DSN**キーワードで示されるデータ ソースに必要に応じて接続します。 共有できない .dsn ファイルには、次のキーワードが含まれます。  
  
```  
DSN = MyDataSource  
```  
  
 ファイル データ ソースに使用される接続文字列は、.dsn ファイルで指定されたキーワードと **、SQLDriverConnect**の呼び出しで接続文字列で指定されたキーワードの和集合です。 dsn ファイル内のいずれかのキーワードが接続文字列のキーワードと競合する場合、ドライバー マネージャーは、どのキーワード値を使用する必要があります決定します。 詳細については、「[接続」](../../../odbc/reference/syntax/sqldriverconnect-function.md)を参照してください。  
  
## <a name="see-also"></a>参照  
 [https://support.microsoft.com/kb/165866](https://support.microsoft.com/kb/165866)
