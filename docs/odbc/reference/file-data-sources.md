---
title: ファイルデータソース |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], file
- file data sources [ODBC]
ms.assetid: db245c80-981a-4638-bd03-69d04bc67af0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0661aa424a7a118b8b12f4bf8433987ff83bd788
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306653"
---
# <a name="file-data-sources"></a>[ファイル データ ソース]
*ファイルデータソース*はファイルに格納され、接続情報が1人のユーザーによって繰り返し使用されるか、複数のユーザー間で共有されます。 ファイルデータソースを使用すると、ドライバーマネージャーは、dsn ファイルの情報を使用してデータソースへの接続を行います。 このファイルは、他のファイルと同様に操作できます。 ファイルデータソースには、マシンデータソースと同じようにデータソース名がなく、1つのユーザーまたはコンピューターに登録されていません。  
  
 ファイルデータソースは接続プロセスを合理化します。これは、 **SQLDriverConnect**関数を呼び出すために作成する必要のある接続文字列が dsn ファイルに含まれているためです。 Dsn ファイルのもう1つの利点は、任意のコンピューターにコピーできることです。そのため、適切なドライバーがインストールされていれば、同一のデータソースを多くのコンピューターで使用できます。 ファイルデータソースは、アプリケーションで共有することもできます。 共有可能なファイルデータソースは、ネットワーク上に配置して、複数のアプリケーションで同時に使用することができます。  
  
 また、dsn ファイルを unshareable することもできます。 Unshareable ファイルは、1台のコンピューター上に存在し、コンピューターのデータソースを指します。 Unshareable file データソースは、主に、コンピューターのデータソースをファイルデータソースに簡単に変換できるようにするために存在します。これにより、ファイルデータソースだけで動作するようにアプリケーションを設計できます。 ドライバーマネージャーは、unshareable file データソース内の情報を送信するときに、必要に応じて、dsn ファイルが指すマシンデータソースに接続します。  
  
 ファイルデータソースの詳細については、「[ファイルデータソースを使用した接続](../../odbc/reference/develop-app/connecting-using-file-data-sources.md)」または「 [SQLDriverConnect](../../odbc/reference/syntax/sqldriverconnect-function.md)関数の説明」を参照してください。
