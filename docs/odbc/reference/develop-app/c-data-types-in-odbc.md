---
title: "ODBC における C データ型 |Microsoft ドキュメント"
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
- data types [ODBC], C data types
- C data types [ODBC], about C data types
- C data types [ODBC]
ms.assetid: c91bef31-3794-4736-966a-d50997b2233c
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 65a5bd882462dbd72c39c751dcfed52c61ab194c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="c-data-types-in-odbc"></a>ODBC における C データ型
ODBC では、アプリケーション変数とその対応する型識別子で使用される C データ型を定義します。 これらは、結果セットの列とステートメントのパラメーターにバインドされているバッファーで使用されます。 たとえば、アプリケーションが文字形式で結果セット列からデータを取得しようとします。 SQLCHAR を持つ変数を宣言して * データ型であり、結果セット列と SQL_C_CHAR の種類の識別子にこの変数をバインドします。 C データ型と型識別子の一覧については、次を参照してください。[付録 d: データ型](../../../odbc/reference/appendixes/appendix-d-data-types.md)です。  
  
 ODBC では、各 SQL データ型から C データ型に対する既定のマッピングも定義します。 たとえば、データ ソース内の 2 バイトの整数は、アプリケーションで 2 バイト整数にマップされます。 既定のマッピングを使用するのには、アプリケーションは SQL_C_DEFAULT 型識別子を指定します。 ただし、この識別子の使用が相互運用上の理由から推奨されません。  
  
 ODBC 1 で定義されているすべての整数値 C データ型*.x*が署名されています。 符号なしの C データ型と、対応する型識別子は、ODBC 2.0 で追加されました。 このため、アプリケーションやドライバーでなければならない 1 を処理する場合に特に注意*.x*バージョン。  
  
## <a name="c-data-type-extensibility"></a>C データ型の機能拡張  
 ODBC 3.8 では、ドライバー固有の C データ型を指定できます。 これを呼び出すとき、SQL 型を ODBC アプリケーションで、ドライバー固有の C 型としてバインドすることできます[SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)、 [SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)、または[SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)です。 これは、既存の C データ型が、新しいサーバーのデータ型を正しく表現していないため、新しいサーバーの型をサポートするため役立ちます。 ドライバー固有の C 型を使用すると、ドライバーが実行できる変換の数を増やすことができます。  
  
 たとえば、データベース管理システム (DBMS) に導入された新しい SQL 型**DATETIMEOFFSET**を日付と時刻のタイム ゾーン情報を示します。 なかったでしょう固有の C 型に対応します odbc **DATETIMEOFFSET**です。 アプリケーションがバインドする必要があります**DATETIMEOFFSET** SQL_C_BINARY およびキャストとしてユーザー定義のデータを入力します。 ODBC 3.8 以降のデータ型の C 拡張機能では、ドライバーは対応する C の新しい型を定義できます。 たとえば、新しい SQL 型 DATETIMEOFFSET のドライバーが SQL_C_DATETIMEOFFSET など、新しいの対応する C 型を定義できます。 次に、アプリケーションでは、ドライバー固有の C 型として新しい SQL 型をバインドすることができます。  
  
 C データ型は、次のように、ドライバーで定義されます。  
  
-   アプリケーション、ODBC ドライバー、およびドライバー マネージャーを ODBC 準拠のレベルは、3.8 (またはそれ以降) です。  
  
-   ドライバー固有の C 型のデータの範囲では、0x4000 ~ 0x7FFF です。  
  
-   ドライバーでは、C 型に対応するデータの構造を定義します。  これにより、ドライバー固有の SDK にあります。  
  
 ドライバー マネージャーは 0x4000 および 0x7FFF; の範囲で定義された C 型を検証できません。検証と任意のデータ型変換は、ドライバーが実行されます。 ドライバー マネージャーが、C データ型を検証、ドライバー マネージャーに渡される C 型のデータ範囲が 0x0000 とから 0x3FFF 間か 0x8000 ~ 0 xffff の場合は、します。  
  
> [!NOTE]  
>  ドライバー固有の C データ型は、ドライバーのドキュメントで説明されている必要があります。  
  
 アプリケーションを呼び出す ODBC 3.8 のコンプライアンス レベルを指定する[SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md)属性を設定する、またと**SQL_OV_ODBC3_80**です。 ドライバーのバージョンを確認するには、アプリケーションが呼び出す**SQLGetInfo** SQL_DRIVER_ODBC_VER とします。  
  
 ODBC 3.8 の詳細については、次を参照してください。 [ODBC 3.8 新](../../../odbc/reference/what-s-new-in-odbc-3-8.md)です。  
  
## <a name="see-also"></a>参照  
 [C データ型](../../../odbc/reference/appendixes/c-data-types.md)

