---
title: 文字データの自動変換 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC], autotranslating character data
- data types [ODBC], autotranslating character data
- ACPs
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- AutoTranslate feature
- ANSI code pages
- character data autotranslation [ODBC]
- autotranslating character data
- SQL Server Native Client ODBC driver, data types
- ODBC data types, autotranslating character data
ms.assetid: 86a8adda-c5ad-477f-870f-cb370c39ee13
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2a8672f748af8d643fa39038be030efa5d434dc8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297882"
---
# <a name="autotranslation-of-character-data"></a>文字データの自動変換
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  文字データ **(SQL_C_CHAR**で宣言された ANSI 文字変数、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**または**char 型 、 **varchar**型 、 テキストデータ型を使用して格納されたデータなど ) は、限られた文字数しか表されません。 1 文字ごとに 1 バイトを使用して保存される文字データでは、256 文字しか表現できません。 SQL_C_CHAR 変数に格納される値は、クライアント コンピューターの ANSI コード ページ (ACP) を使用して解釈されます。 サーバー上の**char**型 **、varchar**型、または**テキスト**データ型を使用して格納された値は、サーバーの ACP を使用して評価されます。  
  
 サーバーとクライアントの両方が同じ ACP を持っている場合、SQL_C_CHAR、char **、varchar、** または**char****text**オブジェクトに格納されている値の解釈に問題はありません。 サーバーとクライアントの ARP が異なる場合、クライアントからのSQL_C_CHARデータは **、char** **、varchar** **、テキスト列**、変数、またはパラメーターで使用されている場合、サーバー上で別の文字として解釈されます。 たとえば、0xA5 という値の文字バイトは、コード ページ 437 を使用するコンピューターでは &#xD1; という文字に解釈されますが、コード ページ 1252 を使用するコンピューターでは円記号 (\) として解釈されます。  
  
 Unicode データは、1 文字あたり 2 バイトを使用して格納されます。 Unicode の仕様は、すべての拡張文字を網羅しています。したがって、すべての Unicode 文字は、すべてのコンピューターで同じ文字に解釈されます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント ODBC ドライバーの自動変換機能は、異なるコード ページを持つクライアントとサーバー間で文字データを移動する場合の問題を最小限に抑えようとします。 自動変換は[、SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqldriverconnect.md)の構成文字列内の SQLDriverConnect[SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md)の接続文字列で設定するか、または ODBC アドミニスト[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]レーターを使用してネイティブ クライアント ODBC ドライバーのデータ ソースを構成するときに設定できます。  
  
 AutoTranslate が "no" に設定されている場合、クライアントの SQL_C_CHAR変数と **、データベース**の char **、varchar**、または**テキスト**列、変数、またはパラメーターの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]間で移動されるデータに対して変換は行われません。 この場合、データに拡張文字が含まれていて、クライアント コンピューターとサーバー コンピューターのコード ページが異なっていると、ビット パターンはクライアントとサーバーでは異なって解釈される可能性があります。 クライアントとサーバーが同じコード ページを使用している場合は、データは同じ文字に解釈されます。  
  
 AutoTranslate が "yes" に設定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]されている場合、ネイティブ クライアント ODBC ドライバは Unicode を使用して、クライアントの SQL_C_CHAR変数と **、クライアント**の変数と char [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **、varchar**、または**テキスト**列、変数、またはデータベース内のパラメータの間で移動されたデータを変換します。  
  
-   クライアントのSQL_C_CHAR変数[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]からデータベース内の**char** **、varchar**、または**text**列、変数、またはパラメーターにデータが送信されると、ODBC ドライバーはまず、クライアントの ACP を使用してSQL_C_CHARから Unicode に変換し、次にサーバーの ACP を使用して Unicode から文字に変換します。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース内の**char** **、varchar**、または**text**列、変数、またはパラメーターからクライアント上のSQL_C_CHAR変数にデータが送信[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]されると、ネイティブ クライアント ODBC ドライバーはまず、サーバーの ACP を使用して文字から Unicode に変換し、次にクライアントの ACP を使用して Unicode からSQL_C_CHARに変換します。  
  
 これらの変換はすべてクライアントで実行される[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント ODBC ドライバによって実行されるため、サーバー ACP はクライアント コンピュータにインストールされているコード ページの 1 つでなければなりません。  
  
 Unicode を使用して文字を変換することで、両方のコード ページに存在しているすべての文字を適切に変換できます。 ただし、一方のコード ページにあっても、他方のコード ページにない文字の場合は、変換先のコード ページでは表現できません。 たとえば、コード ページ 1252 には登録商標記号 (&#xAE;) がありますが、コード ページ 437 にはこの記号がありません。  
  
 AutoTranslate の設定は、次の変換には影響しません。  
  
-   文字SQL_C_CHARクライアント変数と、データベース内の Unicode **nchar** **、nvarchar**、または**ntext** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]列、変数、またはパラメーター間でデータを移動します。  
  
-   クライアント変数と文字**文字 、 varchar**、**varchar**または**テキスト**列、変数、またはデータベース内のパラメーターを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]SQL_C_WCHAR、Unicode 間でデータを移動します。  
  
 文字から Unicode にデータが移動される場合、データは必ず変換されます。  
  
## <a name="see-also"></a>参照  
 [ODBC&#41;&#40;結果の処理](../../relational-databases/native-client-odbc-results/processing-results-odbc.md)   
 [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md)  
  
  
