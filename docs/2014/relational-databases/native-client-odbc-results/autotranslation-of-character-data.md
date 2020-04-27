---
title: 文字データの自動変換 |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5182ab1a72caac4181e50df2199f3e0457d3aaac
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63200211"
---
# <a name="autotranslation-of-character-data"></a>文字データの自動変換
  SQL_C_CHAR で宣言された ANSI 文字変数や、 **CHAR**、 **varchar**、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または**text**データ型を使用してに格納されているデータなどの文字データは、制限された文字数のみを表すことができます。 1 文字ごとに 1 バイトを使用して保存される文字データでは、256 文字しか表現できません。 SQL_C_CHAR 変数に格納される値は、クライアント コンピューターの ANSI コード ページ (ACP) を使用して解釈されます。 サーバーで**char**、 **varchar**、または**text**データ型を使用して格納されている値は、サーバーの ACP を使用して評価されます。  
  
 サーバーとクライアントの両方に同じ ACP がある場合、SQL_C_CHAR、 **CHAR**、 **varchar**、または**text**オブジェクトに格納されている値の解釈に問題はありません。 サーバーとクライアントの ACPs が異なる場合、 **CHAR**、 **varchar**、または**text**型の列、変数、またはパラメーターで使用されている場合、クライアントからの SQL_C_CHAR データはサーバー上で別の文字として解釈される可能性があります。 たとえば、値0xA5 を含む文字バイトは、文字として解釈されますか? コードページ437を使用するコンピューターでは、コードページ1252を実行しているコンピューターでは、円記号 (??) として解釈されます。  
  
 Unicode データは、1 文字あたり 2 バイトを使用して格納されます。 Unicode の仕様は、すべての拡張文字を網羅しています。したがって、すべての Unicode 文字は、すべてのコンピューターで同じ文字に解釈されます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] NATIVE client ODBC ドライバーの autotranslate 機能は、クライアントと異なるコードページを持つサーバー間での文字データの移動に関する問題を最小限に抑えようとしています。 AutoTranslate は、 [SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md)の接続文字列、 [sqlconfigdatasource](../native-client-odbc-api/sqlconfigdatasource.md)の構成文字列、または odbc アドミニストレーターを使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーのデータソースを構成するときに設定できます。  
  
 AutoTranslate が "no [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] " に設定されている場合、クライアントの SQL_C_CHAR 変数と、データベースの**CHAR**、 **varchar**、または**text**型の列、変数、またはパラメーターの間で移動されたデータの変換は行われません。 この場合、データに拡張文字が含まれていて、クライアント コンピューターとサーバー コンピューターのコード ページが異なっていると、ビット パターンはクライアントとサーバーでは異なって解釈される可能性があります。 クライアントとサーバーが同じコード ページを使用している場合は、データは同じ文字に解釈されます。  
  
 AutoTranslate が "yes" に設定されて[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]いる場合、NATIVE client ODBC ドライバーは Unicode を使用して、クライアント上の SQL_C_CHAR 変数と、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース内の**CHAR**、 **varchar**、または**text**型の列、変数、またはパラメーターの間で移動されたデータを変換します。  
  
-   データがクライアントの SQL_C_CHAR 変数から**CHAR**、 **varchar**、または**text**型の列、変数、またはパラメーターに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースで送信されると、ODBC ドライバーはまず、クライアントの acp を使用して SQL_C_CHAR から unicode に変換し、次にサーバーの acp を使用して unicode から文字に変換します。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース内の**char**、 **varchar**、または**text**型の列、変数、またはパラメーターから、データがクライアントの SQL_C_CHAR 変数に送信さ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]れると、Native client ODBC ドライバーは、まずサーバーの acp を使用して文字を unicode に変換し、次に unicode からクライアントの acp を使用して SQL_C_CHAR します。  
  
 これらの変換はすべて、クライアントで実行[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]されている NATIVE Client ODBC ドライバーによって行われるため、サーバーの ACP はクライアントコンピューターにインストールされているコードページの1つである必要があります。  
  
 Unicode を使用して文字を変換することで、両方のコード ページに存在しているすべての文字を適切に変換できます。 ただし、一方のコード ページにあっても、他方のコード ページにない文字の場合は、変換先のコード ページでは表現できません。 たとえば、コードページ1252には、商標記号 (??) が登録されていますが、コードページ437にはありません。  
  
 AutoTranslate の設定は、次の変換には影響しません。  
  
-   データベース内の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]文字 SQL_C_CHAR クライアント変数と Unicode **nchar**、 **nvarchar**、または**ntext**型の列、変数、またはパラメーターの間でデータを移動する。  
  
-   Unicode SQL_C_WCHAR クライアント変数と、データベース内の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]文字**char**、 **varchar**、または**text**型の列、変数、またはパラメーターの間でデータを移動する。  
  
 文字から Unicode にデータが移動される場合、データは必ず変換されます。  
  
## <a name="see-also"></a>参照  
 [ODBC&#41;&#40;結果の処理](processing-results-odbc.md)   
 [照合順序と Unicode のサポート](../collations/collation-and-unicode-support.md)  
  
  
