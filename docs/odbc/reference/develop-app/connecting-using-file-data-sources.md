---
title: "ファイルのデータ ソースを使用して接続する |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connecting to driver [ODBC], file data sources
- SQLDriverConnect function [ODBC], connecting using file data sources
- connecting to data source [ODBC], SQLDriverConnect
- connecting to driver [ODBC], SQLDriverConnect
- connecting to data source [ODBC], file data sources
- file data sources [ODBC]
ms.assetid: 3003f8c2-8be6-41cc-8d9c-612e9bd0f3ae
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5f8a5d949127e7ad87866a0272fbd285fe12ceed
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="connecting-using-file-data-sources"></a>ファイルのデータ ソースを使用して接続します。
ファイル データ ソースの接続情報は、.dsn ファイルに格納されます。 その結果、接続文字列を 1 人のユーザーによって繰り返し使用または適切なドライバーがインストールされている場合に、いくつかのユーザー間で共有を設定します。 ファイルには、ドライバー名 (または別のデータ ソース名、共有不能なファイルのデータ ソースの場合) が含まれていると、必要に応じて、接続文字列をで使用できる**SQLDriverConnect**です。 ドライバー マネージャーへの呼び出しの接続文字列を構築する**SQLDriverConnect** .dsn ファイル内のキーワードからです。  
  
 ファイル データ ソースにより、アプリケーションで使用する接続文字列を作成することがなく接続オプションを指定する**SQLDriverConnect**です。 通常、ファイル データ ソースが指定して作成された、 **SAVEFILE**キーワードで、ドライバー マネージャーへの呼び出しによって作成された出力接続文字列を保存すると、 **SQLDriverConnect** .dsn ファイルにします。 呼び出して接続文字列を繰り返し使用できること**SQLDriverConnect**で、 **FILEDSN**キーワード。 これにより、接続プロセスを合理化し、接続文字列の永続的なソースを提供します。  
  
 ファイルのデータ ソースを作成することも呼び出すことによって**SQLCreateDataSource**の DLL のインストーラーにします。 情報は、呼び出すことによって、.dsn ファイルに書き込まれることができます**SQLWriteFileDSN**、呼び出すことによって、.dsn ファイルから読み取ると**SQLReadFileDSN**; インストーラー DLL もこれらの関数の両方です。 インストーラーの DLL については、次を参照してください。[データ ソースを構成する](../../../odbc/reference/install/configuring-data-sources.md)です。  
  
 .Dsn ファイルの [ODBC] セクションには、接続情報の使用されるキーワードです。 最低限必要な情報が共有可能 .dsn ファイルは [ODBC] セクションでは、DRIVER キーワードを示します。  
  
```  
DRIVER = SQL Server  
```  
  
 共有可能 .dsn ファイルには通常が含まれています、接続文字列には、次のように。  
  
```  
DRIVER = SQL Server  
UID = Larry  
DATABASE = MyDB  
```  
  
 ファイル データ ソースが共有可能 .dsn ファイルだけを含んだ、 **DSN**キーワード。 ドライバー マネージャーには、データ ソースに共有不能なファイル情報が送信されると、の接続で示されたデータ ソースを必要に応じて、 **DSN**キーワード。 共有不能な .dsn ファイルには、次のキーワードが含まれます。  
  
```  
DSN = MyDataSource  
```  
  
 ファイル データ ソースを使用する接続文字列は .dsn ファイルで指定されたキーワードと呼び出しでは、接続文字列で指定されたキーワードの和集合**SQLDriverConnect**です。 .Dsn ファイル内のキーワードのいずれかの接続文字列のキーワードと競合している場合、ドライバー マネージャーは、どのキーワードの値を使用する必要がありますを決定します。 詳細については、次を参照してください。 [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)です。  
  
## <a name="see-also"></a>参照  
 [http://support.microsoft.com/kb/165866](http://support.microsoft.com/kb/165866)

