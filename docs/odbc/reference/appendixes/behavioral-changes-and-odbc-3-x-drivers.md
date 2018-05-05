---
title: 動作の変更と ODBC 3.x ドライバー |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- sql_attr_odbc_version [ODBC]
- backward compatibility [ODBC], behavioral changes
- compatibility [ODBC], behavioral changes
ms.assetid: 88a503cc-bff7-42d9-83ff-8e232109ed06
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f5eed90b0cfea267e2184018251d7a42da8bf670
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="behavioral-changes-and-odbc-3x-drivers"></a>動作の変更と ODBC 3.x ドライバー
環境属性 ODBC 2 が発生する必要があるかどうかがドライバーにまたを示します。*x*動作または ODBC 3 *.x*動作します。 また環境属性を設定する方法は、アプリケーションによって異なります。 ODBC 3 *.x*アプリケーションを呼び出す必要があります**SQLSetEnvAttr**を呼び出すことが後に、この属性を設定する**SQLAllocHandle**環境ハンドルの割り当てに呼び出しの前に、**SQLAllocHandle**接続ハンドルを割り当てられません。 ドライバー マネージャーを含む SQLSTATE HY010 を返しますこれに失敗した場合 (関数のシーケンス エラー) 後者の呼び出しに**SQLAllocHandle**です。  
  
> [!NOTE]  
>  動作の変更であり、アプリケーションの機能の詳細については、次を参照してください。[動作の変更](../../../odbc/reference/develop-app/behavioral-changes.md)です。  
  
 ODBC 2 です。*x*アプリケーションや ODBC 2 *。x* ODBC 3 で再コンパイルされたアプリケーション *.x*ヘッダー ファイルは呼び出さないでください**SQLSetEnvAttr**です。 ただし、呼び出す**SQLAllocEnv**の代わりに**SQLAllocHandle**環境ハンドルを割り当てられません。 そのため、アプリケーションを呼び出すと**SQLAllocEnv**ドライバー マネージャーで、ドライバー マネージャーを呼び出す**SQLAllocHandle**と**SQLSetEnvAttr**ドライバーにします。 したがって、ODBC 3 *.x*ドライバーに設定されているこの属性でカウントできる常にします。  
  
 標準に準拠したアプリケーションでは、呼び出しを ODBC_STD コンパイル フラグにコンパイルする場合**SQLAllocEnv** (が発生する可能性があるため**SQLAllocEnv** ISO では推奨されていません)、呼び出しにマップされて**SQLAllocHandleStd**コンパイル時にします。 実行時に、アプリケーション呼び出し**SQLAllocHandleStd**です。 ドライバー マネージャーは、また環境属性を SQL_OV_ODBC3 に設定します。 呼び出し**SQLAllocHandleStd**への呼び出しに相当**SQLAllocHandle**で、 *HandleType* SQL_HANDLE_ENV とへの呼び出しの**SQLSetEnvAttr**またを SQL_OV_ODBC3 に設定します。  
  
 特定ドライバーのアーキテクチャにおいて必要がある、ドライバーは、ODBC 2 として表示されます。*x*ドライバーまたは ODBC 3 *.x*接続に応じて、ドライバーです。 ドライバーここではできない可能性があります実際には、ドライバーがドライバー マネージャーと別のドライバーが存在するレイヤー。 たとえば、ODBC Spy と同様に、ドライバーを模倣こと可能性があります。 別の例には、EDA]/[SQL のように、ゲートウェイとして機能、可能性があります。 ODBC 3 として表示される *.x*ドライバー、そのようなドライバーは、エクスポートすることである必要があります**SQLAllocHandle**、および ODBC 2 として表示する*。x*ドライバーはエクスポートできる必要があります**SQLAllocConnect**、 **SQLAllocEnv**、および**SQLAllocStmt**です。 このドライバーのエクスポートをドライバー マネージャーが確認環境、接続、またはステートメントは、割り当てられるが、 **SQLAllocHandle**です。 ドライバーは、ドライバー マネージャーの呼び出しから**SQLAllocHandle**ドライバーにします。 場合は、ドライバーは ODBC 2 と連携しています。*x*ドライバー、ドライバーはへの呼び出しをマップする必要があります**SQLAllocHandle**に**SQLAllocConnect**、 **SQLAllocEnv**、または**SQLAllocStmt** をクリックします。 何も行う必要がありますも、 **SQLSetEnvAttr** ODBC 2 として機能しているときに呼び出します*。x*ドライバー。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [Datetime データ型](../../../odbc/reference/appendixes/datetime-data-types.md)  
  
-   [C データ型の下位互換性](../../../odbc/reference/appendixes/backward-compatibility-of-c-data-types.md)  
  
-   [固定長のブックマーク](../../../odbc/reference/appendixes/fixed-length-bookmarks.md)  
  
-   [SQLGetInfo のサポート](../../../odbc/reference/appendixes/sqlgetinfo-support.md)  
  
-   [SQL_NO_DATA を返す](../../../odbc/reference/appendixes/returning-sql-no-data.md)  
  
-   [データを挿入するための SQLSetPos の呼び出し](../../../odbc/reference/appendixes/calling-sqlsetpos-to-insert-data.md)  
  
-   [序数での読み込み](../../../odbc/reference/appendixes/loading-by-ordinal.md)
