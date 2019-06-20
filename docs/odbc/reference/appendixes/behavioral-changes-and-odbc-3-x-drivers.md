---
title: 動作変更および ODBC 3.x ドライバー |Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e386aa60489fe3edb2caac3cb49ebad263ffdfac
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63026622"
---
# <a name="behavioral-changes-and-odbc-3x-drivers"></a>動作変更および ODBC 3.x ドライバー
環境属性 ODBC 2 が発生する必要があるかどうか、ドライバーを SQL_ATTR_ODBC_VERSION を示します。*x*動作または ODBC 3 *.x*動作します。 SQL_ATTR_ODBC_VERSION 環境属性を設定する方法は、アプリケーションによって異なります。 ODBC 3 *.x*アプリケーションを呼び出す必要があります**SQLSetEnvAttr**を呼び出すことが後に、この属性を設定する**SQLAllocHandle**環境ハンドルの割り当てに呼び出しの前に、**SQLAllocHandle**接続ハンドルを割り当てられません。 これを行うよう、失敗した場合、ドライバー マネージャーは SQLSTATE HY010 を返します (関数のシーケンス エラーです)、後者の呼び出しで**SQLAllocHandle**します。  
  
> [!NOTE]  
>  動作が変更されると、アプリケーションの機能の詳細については、次を参照してください。[動作が変更される](../../../odbc/reference/develop-app/behavioral-changes.md)します。  
  
 ODBC 2。*x*アプリケーションや ODBC 2 *。x* ODBC 3 と再コンパイルされたアプリケーション *.x*ヘッダー ファイルは呼び出さないでください**SQLSetEnvAttr**します。 ただし、呼び出す**SQLAllocEnv**の代わりに**SQLAllocHandle**環境ハンドルを割り当てられません。 そのため、アプリケーションを呼び出すと**SQLAllocEnv**ドライバー マネージャーは、ドライバー マネージャーで、 **SQLAllocHandle**と**SQLSetEnvAttr**ドライバー。 したがって、ODBC 3 *.x*ドライバー常に信頼性のこの属性が設定されています。  
  
 呼び出し、ODBC_STD コンパイル フラグでコンパイルされた標準に準拠したアプリケーションの場合**SQLAllocEnv** (ために発生する可能性があります**SQLAllocEnv** ISO で非推奨ではない)、呼び出しにマップされて**SQLAllocHandleStd**コンパイル時にします。 実行時に、アプリケーション呼び出し**SQLAllocHandleStd**します。 ドライバー マネージャーは、SQL_ATTR_ODBC_VERSION 環境属性を SQL_OV_ODBC3 に設定します。 呼び出し**SQLAllocHandleStd**への呼び出しに相当**SQLAllocHandle**で、 *HandleType* sql_handle_env としてとへの呼び出しの**SQLSetEnvAttr**を SQL_ATTR_ODBC_VERSION を SQL_OV_ODBC3 に設定します。  
  
 特定ドライバーのアーキテクチャでは、ODBC 2 として表示するドライバーが必要であります。*x*ドライバーや、ODBC 3 *.x*接続に応じて、ドライバー。 ドライバーここで実際にはありますが、ドライバー、ドライバー マネージャーと他のドライバーの間に存在するレイヤー。 たとえば、ODBC スパイのように、ドライバーを模倣こと可能性があります。 別の例では、EDA]/[SQL のように、ゲートウェイとして機能、可能性があります。 ODBC 3 として表示される *.x*ドライバーでは、このようなドライバーは、エクスポートすることである必要があります**SQLAllocHandle**、および ODBC 2 として表示する *。x*ドライバーはエクスポートできる必要があります**SQLAllocConnect**、 **SQLAllocEnv**、および**SQLAllocStmt**します。 ドライバー マネージャーが、このドライバーのエクスポートを確認します、環境、接続、またはステートメントは、割り当てられるが、 **SQLAllocHandle**します。 ドライバーは、ドライバー マネージャーの呼び出しから**SQLAllocHandle**ドライバー。 場合は、ドライバーは、ODBC 2 操作です。*x*ドライバー、ドライバーはへの呼び出しをマップする必要があります**SQLAllocHandle**に**SQLAllocConnect**、 **SQLAllocEnv**、または**SQLAllocStmt**必要に応じて、します。 何も行う必要がありますも、 **SQLSetEnvAttr** ODBC 2 として動作するときに呼び出す *。x*ドライバー。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [Datetime データ型](../../../odbc/reference/appendixes/datetime-data-types.md)  
  
-   [C データ型の下位互換性](../../../odbc/reference/appendixes/backward-compatibility-of-c-data-types.md)  
  
-   [固定長のブックマーク](../../../odbc/reference/appendixes/fixed-length-bookmarks.md)  
  
-   [SQLGetInfo のサポート](../../../odbc/reference/appendixes/sqlgetinfo-support.md)  
  
-   [SQL_NO_DATA を返す](../../../odbc/reference/appendixes/returning-sql-no-data.md)  
  
-   [データを挿入するための SQLSetPos の呼び出し](../../../odbc/reference/appendixes/calling-sqlsetpos-to-insert-data.md)  
  
-   [序数での読み込み](../../../odbc/reference/appendixes/loading-by-ordinal.md)
