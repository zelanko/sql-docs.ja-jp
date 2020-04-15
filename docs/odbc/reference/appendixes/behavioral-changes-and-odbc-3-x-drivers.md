---
title: 動作の変更と ODBC 3.x ドライバ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- sql_attr_odbc_version [ODBC]
- backward compatibility [ODBC], behavioral changes
- compatibility [ODBC], behavioral changes
ms.assetid: 88a503cc-bff7-42d9-83ff-8e232109ed06
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4d8343573261d74a6a0c652cf425b12da91f7cb0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292366"
---
# <a name="behavioral-changes-and-odbc-3x-drivers"></a>動作変更および ODBC 3.x ドライバー
環境属性SQL_ATTR_ODBC_VERSION、ODBC *2.x*の動作を示す必要があるか、ODBC *3.x*の動作を示す必要があるかをドライバーに示します。 SQL_ATTR_ODBC_VERSION環境属性の設定方法は、アプリケーションによって異なります。 ODBC *3.x*アプリケーションは **、SQLAllocHandle**を呼び出して環境ハンドルを割り当てた後、接続ハンドルを割り当てる**SQLAllocHandle**を呼び出す前に、この属性を設定するために**SQLSetEnvAttr**を呼び出す必要があります。 この操作が失敗すると、ドライバー マネージャーは SQLState HY010 (関数シーケンス エラー) を返す**SQLAllocHandle**の後者の呼び出し。  
  
> [!NOTE]  
>  動作の変更とアプリケーションの動作の詳細については、「[動作の変更](../../../odbc/reference/develop-app/behavioral-changes.md)」を参照してください。  
  
 ODBC *2.x*アプリケーションと ODBC *3.x*ヘッダー ファイルを使用して再コンパイルされた ODBC *2.x*アプリケーションは **、SQLSetEnvAttr**を呼び出しません。 ただし、環境ハンドルを割り当てるには **、SQLAllocHandle**の代わりに**SQLAllocEnv**を呼び出します。 したがって、ドライバー マネージャーで**アプリケーションが SQLAllocEnv**を呼び出すとき、ドライバー マネージャーは、ドライバーで**SQLAllocHandle**と**SQLSetEnvAttr**を呼び出します。 したがって、ODBC *3.x*ドライバは、この属性が設定されていることを常にカウントできます。  
  
 ODBC_STDコンパイル フラグを使用してコンパイルされた標準準拠のアプリケーションが**SQLAllocEnv**を呼び出す場合 (**これは、SQLAllocEnv**が ISO で非推奨ではないために発生する可能性があります)、呼び出しはコンパイル時に**SQLAllocHandleStd**にマップされます。 実行時に、アプリケーションは**SQLAllocHandleStd**を呼び出します。 ドライバー マネージャーは、SQL_ATTR_ODBC_VERSION環境属性をSQL_OV_ODBC3に設定します。 **SQLAllocHandleStd**の呼び出しは、*ハンドルのSQL_HANDLE_ENVのハンドル型*を持つ**SQLAllocHandle**の呼び出しと、SQL_OV_ODBC3にSQL_ATTR_ODBC_VERSIONを設定する**SQLSetEnvAttr**の呼び出しと同等です。  
  
 特定のドライバ アーキテクチャでは、接続に応じて、ODBC *2.x*ドライバまたは ODBC *3.x*ドライバとしてドライバを表示する必要があります。 この場合、ドライバーは、実際にはドライバーではなく、ドライバー マネージャーと別のドライバーの間に存在するレイヤーである可能性があります。 たとえば、ODBC スパイなどのドライバーを模倣する場合があります。 別の例では、EDA/SQL のようなゲートウェイとして機能する場合があります。 ODBC *3.x*ドライバーとして表示するには、このようなドライバーが**SQLAllocHandle**をエクスポートでき、ODBC *2.x*ドライバーとして表示されるようにする必要**があります。** **SQLAllocConnect** **SQLAllocEnv** 環境、接続、またはステートメントを割り当てる場合、ドライバー マネージャーは、このドライバーが**SQLAllocHandle**をエクスポートするかどうかを確認します。 ドライバーが行うため、ドライバー マネージャーは、ドライバーで**SQLAllocHandle**を呼び出します。 ドライバーが**SQLAllocStmt**ODBC *2.x*ドライバーを使用している場合、ドライバーは、呼び出しを**SQLAllocHandle**に**SQLAllocEnv**対応付ける必要があります。 **SQLAllocConnect** ODBC *2.x*ドライバとして振る舞う場合は **、SQLSetEnvAttr**呼び出しでも何も行う必要はありません。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [Datetime データ型](../../../odbc/reference/appendixes/datetime-data-types.md)  
  
-   [C データ型の下位互換性](../../../odbc/reference/appendixes/backward-compatibility-of-c-data-types.md)  
  
-   [固定長のブックマーク](../../../odbc/reference/appendixes/fixed-length-bookmarks.md)  
  
-   [SQLGetInfo のサポート](../../../odbc/reference/appendixes/sqlgetinfo-support.md)  
  
-   [SQL_NO_DATA を返す](../../../odbc/reference/appendixes/returning-sql-no-data.md)  
  
-   [データを挿入するための SQLSetPos の呼び出し](../../../odbc/reference/appendixes/calling-sqlsetpos-to-insert-data.md)  
  
-   [序数での読み込み](../../../odbc/reference/appendixes/loading-by-ordinal.md)
