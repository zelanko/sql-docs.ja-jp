---
title: Unicode アプリケーション |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Unicode [ODBC], compiling as Unicode application
- Unicode [ODBC], functions
- compiling Unicode applications [ODBC]
- functions [ODBC], Unicode functions
ms.assetid: 7986c623-2792-4e77-bfee-c86cbf84f08d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 94bd5211c878904453624adb2acd0fe435ebc812
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298948"
---
# <a name="unicode-applications"></a>Unicode アプリケーション
アプリケーションは、次の2つの方法のいずれかで、Unicode アプリケーションとして再コンパイルできます。  
  
-   Sqlucode .h ヘッダーファイルに格納されている Unicode **#define**をアプリケーションに含めます。  
  
-   コンパイラの Unicode オプションを使用して、アプリケーションをコンパイルします。 (このオプションは、コンパイラによって異なります)。  
  
 ANSI アプリケーションを Unicode アプリケーションに変換するには、Unicode データを格納して渡すアプリケーションを記述します。 また、SQLPOINTER 引数をサポートする関数への呼び出しは、バイト数を使用するように変換する必要があります。  
  
 アプリケーションが Unicode アプリケーションとしてコンパイルされた後、アプリケーションが (サフィックスなしで) ODBC API 関数を呼び出すと、ドライバーマネージャーはアプリケーションを Unicode アプリケーションとして認識し、基になるドライバーが Unicode をサポートしている場合は、関数呼び出しを ( *W*サフィックスを持つ) unicode 関数に変換します。 ANSI アプリケーションがサフィックスなしで関数呼び出しを行う場合、ドライバーマネージャーは、基になるドライバーが ANSI をサポートしている場合、その関数を ANSI に変換します。 アプリケーションとドライバーの両方で同じ文字エンコーディングがサポートされている場合は、ドライバーマネージャーが呼び出しをドライバーに渡します (ANSI アプリケーションの特定の例外があります)。  
  
 アプリケーションで*は、* *(サフィックスが*付いているかに関係なく) Unicode 関数と ANSI 関数の両方を呼び出すことができます。 Unicode および ANSI 関数の呼び出しは、混在させることができます。 ただし、カーソルライブラリを使用する場合は、Unicode および ANSI 関数の呼び出しを混在させることはできません。 カーソルライブラリは、混合ではなく、Unicode または ANSI のいずれかです。  
  
 アプリケーションは、Unicode アプリケーションまたは ANSI アプリケーションとしてコンパイルできるように記述できます。 この場合、文字データ型は SQL_C_TCHAR として宣言できます。 これは、アプリケーションが Unicode アプリケーションとしてコンパイルされている場合は SQL_C_WCHAR を挿入するマクロで、ANSI アプリケーションとしてコンパイルされる場合は SQL_C_CHAR を挿入します。 アプリケーションプログラマは、SQLPOINTER を引数として受け取る関数に注意する必要があります。これは、アプリケーションが ANSI または Unicode のどちらであるかによって、長さ引数のサイズが (文字列データ型の場合) 変更されるためです。  
  
 関数は、次の3つの方法のいずれかで呼び出すことができます。 ( *W*サフィックスを持つ) Unicode のみの関数呼び出し、ANSI*のみの関数呼び出し (サフィックスあり*)、またはサフィックスなしの ODBC 関数呼び出し。 関数の3つの形式の引数は同じです。 SQLCHAR \* arguments または文字列を指す sqlpointer 引数を持つ関数だけが、UNICODE および ANSI 形式を必要とします。 **SQLBindCol**や**SQLGetData**など、文字型として宣言できる引数を持つ関数の場合 (unicode および ansi 形式がない場合) は、引数を unicode 型、ANSI 型、または C 型引数の場合は SQL_C_TCHAR マクロとして宣言できます。 詳細については、「 [Unicode データ](../../../odbc/reference/develop-app/unicode-data.md)」を参照してください。  
  
 Unicode ドライバーが使用できない場合でも、アプリケーションを Unicode アプリケーションとして書き込むことができます。 ドライバーマネージャーは、Unicode 関数とデータ型を ANSI にマップします。 実行可能な Unicode から ANSI へのマッピングにはいくつかの制限があります。 Unicode アプリケーションの操作に Unicode ドライバーが存在すると、パフォーマンスが向上し、Unicode から ANSI へのマッピングに固有の制限がなくなります。
