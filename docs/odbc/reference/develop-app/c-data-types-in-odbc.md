---
title: Odbc C データ型 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], C data types
- C data types [ODBC], about C data types
- C data types [ODBC]
ms.assetid: c91bef31-3794-4736-966a-d50997b2233c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5472595383c7e4fcf448374c1fd85587246328f7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63199213"
---
# <a name="c-data-types-in-odbc"></a>ODBC の C データ型
ODBC では、アプリケーション変数とその対応する型識別子で使用される C データ型を定義します。 これらは、結果セットの列とステートメントのパラメーターにバインドされているバッファーが使用されます。 たとえば、アプリケーションが文字形式で結果セット列からデータを取得しようとします。 SQLCHAR を持つ変数を宣言します * データ型で、この変数を SQL_C_CHAR の型識別子を持つ結果セット列にバインドします。 C データ型と型識別子の完全な一覧を参照してください[付録 d:。データ型](../../../odbc/reference/appendixes/appendix-d-data-types.md)します。  
  
 ODBC では、各 SQL データ型から C データ型に既定のマッピングも定義します。 たとえば、データ ソース内の 2 バイト整数は、アプリケーションで 2 バイトの整数にマップされます。 既定のマッピングを使用するには、アプリケーションは、SQL_C_DEFAULT 型の識別子を指定します。 ただし、この識別子の使用は相互運用性上の理由から推奨されません。  
  
 ODBC 1 で定義されているすべての整数値 C データ型 *.x*が署名されています。 符号なしの C データ型とその対応する型識別子は、ODBC 2.0 で追加されました。 このため、アプリケーションとドライバーの必要がある 1 を扱う場合に特に注意する *.x*バージョン。  
  
## <a name="c-data-type-extensibility"></a>C データ型の機能拡張  
 ODBC 3.8、ドライバー固有の C データ型を指定できます。 これにより、SQL 型を呼び出すときに ODBC アプリケーションで、ドライバー固有の C 型としてバインド[SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)、 [SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)、または[SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)します。 既存の C データ型が新しいサーバーのデータ型を正しく表現していないため、新しいサーバーの型をサポートするための便利なできます。 ドライバー固有の C 型を使用すると、ドライバーを実行できる変換の数を増やすことができます。  
  
 たとえば、データベース管理システム (DBMS) には、新しい SQL 型が導入された**DATETIMEOFFSET**日付と時刻のタイム ゾーン情報を表すため。 なくなる C の特定の型に対応する odbc **DATETIMEOFFSET**します。 アプリケーションがバインドする必要があります**DATETIMEOFFSET** SQL_C_BINARY、およびキャストとしてユーザー定義のデータを入力します。 ODBC 3.8 以降のデータ型の C 拡張機能では、ドライバーは、対応する C の新しい型を定義できます。 たとえば、新しい SQL 型 DATETIMEOFFSET ドライバーは、SQL_C_DATETIMEOFFSET などの新しい対応する C 型を定義できます。 次に、アプリケーションでは、ドライバー固有の C 型として、新しい SQL 型をバインドすることができます。  
  
 C データ型は、次のように、ドライバーで定義されます。  
  
-   アプリケーション、ODBC ドライバー、およびドライバー マネージャーを ODBC 準拠のレベルは、3.8 (またはそれ以降)。  
  
-   ドライバー固有の C 型のデータの範囲では、0x4000 ~ 0x7FFF です。  
  
-   ドライバーは、C 型に対応するデータの構造を定義します。  これにより、ドライバー固有の SDK にあります。  
  
 ドライバー マネージャーは 0x4000 と 0x7FFF; の範囲で定義された C 型を検証できません。ドライバーは、検証と任意のデータ型の変換を実行します。 ドライバー マネージャーが、C データ型を検証 0x0000 とから 0x3FFF 間または 0x8000 と 0 xffff のドライバー マネージャーに渡される C 型のデータ範囲である場合。  
  
> [!NOTE]  
>  ドライバーのドキュメントでは、ドライバー固有の C データ型を記述する必要があります。  
  
 アプリケーションを呼び出す ODBC 3.8 のコンプライアンス レベルを指定する[SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md)属性を設定する、SQL_ATTR_ODBC_VERSION に**SQL_OV_ODBC3_80**します。 ドライバーのバージョンを確認するには、アプリケーションが呼び出す**SQLGetInfo** SQL_DRIVER_ODBC_VER とします。  
  
 ODBC 3.8 の詳細については、次を参照してください。[で ODBC 3.8 新](../../../odbc/reference/what-s-new-in-odbc-3-8.md)します。  
  
## <a name="see-also"></a>参照  
 [C データ型](../../../odbc/reference/appendixes/c-data-types.md)
