---
title: ファイル データ ソース |マイクロソフトドキュメント
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306653"
---
# <a name="file-data-sources"></a>[ファイル データ ソース]
*ファイル データ ソース*はファイルに格納され、接続情報を 1 人のユーザーが繰り返し使用したり、複数のユーザー間で共有したりできます。 ファイル データ ソースを使用すると、ドライバー マネージャーは、.dsn ファイルの情報を使用してデータ ソースに接続します。 このファイルは、他のファイルと同様に操作できます。 ファイル データ ソースには、コンピューターのデータ ソースと同様に、データ ソース名が含まれていないため、1 人のユーザーまたはコンピューターに登録されません。  
  
 ファイル データ ソースは、.dsn ファイルに **、SQLDriverConnect**関数の呼び出しに対して構築する必要がある接続文字列が含まれているため、接続プロセスを効率化します。 dsn ファイルのもう 1 つの利点は、任意のマシンにコピーできるため、適切なドライバがインストールされていれば、多くのマシンで同一のデータ ソースを使用できることです。 ファイル データ ソースは、アプリケーションで共有することもできます。 共有可能なファイル データ ソースは、ネットワーク上に配置し、複数のアプリケーションで同時に使用できます。  
  
 dsn ファイルは共有不可にすることもできます。 共有できない .dsn ファイルは、単一のマシン上に存在し、マシンのデータ ソースを指します。 共有できないファイル データ ソースは、主にマシン データ ソースをファイル データ ソースに簡単に変換できるため、アプリケーションはファイル データ ソースのみを使用するように設計できます。 ドライバー マネージャーは、共有できないファイル のデータ ソース内の情報を送信すると、必要に応じて、.dsn ファイルが指すコンピューター のデータ ソースに接続します。  
  
 ファイル データ ソースの詳細については、「[ファイル データ ソースを使用した接続](../../odbc/reference/develop-app/connecting-using-file-data-sources.md)」または[SQLDriverConnect](../../odbc/reference/syntax/sqldriverconnect-function.md)関数の説明を参照してください。
