---
title: SQLGetInfo (カーソル ライブラリ) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetInfo function [ODBC], Cursor Library
ms.assetid: 1b4d220d-2c07-4f56-987e-36813bb1a6ce
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9067fd8b33cb2408f1ef6f0e58603eb4f1f7eb09
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307813"
---
# <a name="sqlgetinfo-cursor-library"></a>SQLGetInfo (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新しい開発作業でこの機能を使用することは避け、現在この機能を使用しているアプリケーションを変更する予定です。 マイクロソフトでは、ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックでは、カーソル ライブラリで**の SQLGetInfo**関数の使用について説明します。 **SQLGetInfo**の一般的な情報については、「 [SQLGetInfo 関数](../../../odbc/reference/syntax/sqlgetinfo-function.md)」を参照してください。  
  
 カーソル ライブラリは *、次の InfoType*値の値を返します (&#124;ビットごとの OR を表します)。その他の*InfoType*の値については、ドライバーで**SQLGetInfo**を呼び出します。  
  
|*Infotype*|戻り値|  
|----------------|--------------------|  
|SQL_BOOKMARK_PERSISTENCE|SQL_BP_SCROLL|  
|SQL_DYNAMIC_CURSOR_ATTRIBUTES1|0|  
|SQL_DYNAMIC_CURSOR_ATTRIBUTES2|0|  
|SQL_FETCH_DIRECTION[1]|&#124; SQL_FD_FETCH_RELATIVE &#124; SQL_FD_FETCH_PRIOR &#124; SQL_FD_FETCH_NEXT SQL_FD_FETCH_LAST &#124; &#124; &#124;&#124;&#124;&#124;&#124;SQL_FD_FETCH_BOOKMARK&#124;&#124;SQL_FD_FETCH_FIRSTSQL_FD_FETCH_FIRSTSQL_FD_FETCH_ABSOLUTE&#124;|  
|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1|&#124; &#124; SQL_CA1_POSITIONED_DELETE &#124; SQL_CA1_POS_POSITION SQL_CA1_LOCK_NO_CHANGE &#124; &#124; SQL_CA1_ABSOLUTE SQL_CA1_NEXTSQL_CA1_NEXTSQL_CA1_POSITIONED_UPDATEのSQL_CA1_SELECT_FOR_UPDATEを&#124;&#124;SQL_CA1_RELATIVESQL_CA1_NEXTSQL_CA1_RELATIVESQL_CA1_NEXT&#124;&#124;&#124;&#124;。|  
|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2|&#124; SQL_CA2_SENSITIVITY_UPDATESSQL_CA2_OPT_VALUES_CONCURRENCY&#124;SQL_CA2_READ_ONLY_CONCUR|  
|SQL_GETDATA_EXTENSIONS|SQL_GD_BLOCKドライバーによって返される値を&#124;**注意:** **SQLFetchScroll**を使用してデータを取得する場合 **、SQLGetData**はSQL_GD_ANY_COLUMNおよびSQL_GD_BOUNDビットマスクで指定された機能をサポートします。|  
|SQL_KEYSET_DRIVEN_CURSOR_ATTRIBUTES1|0|  
|SQL_KEYSET_DRIVEN_CURSOR_ATTRIBUTES2|0|  
|SQL_LOCK_TYPES[1]|SQL_LCK_NO_CHANGE|  
|SQL_STATIC_CURSOR_ATTRIBUTES1|&#124; &#124; SQL_CA1_POSITIONED_DELETE &#124; SQL_CA1_POS_POSITION &#124; SQL_CA1_LOCK_NO_CHANGE &#124; SQL_CA1_RELATIVE SQL_CA1_ABSOLUTE &#124; SQL_CA1_SELECT_FOR_UPDATESQL_CA1_SELECT_FOR_UPDATEのSQL_CA1_POSITIONED_UPDATE&#124;SQL_CA1_BOOKMARKSQL_CA1_BOOKMARKSQL_CA1_BOOKMARKSQL_CA1_BOOKMARKSQL_CA1_BOOKMARK&#124;&#124;&#124;&#124;&#124;&#124;SQL_CA1_POSITIONED_UPDATE&#124;&#124;SQL_CA1_POSITIONED_UPDATESQL_CA1_NEXT|  
|SQL_STATIC_CURSOR_ATTRIBUTES2|同時実行&#124;SQL_CA2_SENSITIVITY_UPDATESSQL_CA2_OPT_VALUES_&#124;SQL_CA2_READ_ONLY_CONCUR|  
|SQL_POS_OPERATIONS[1]|SQL_POS_POSITION|  
|SQL_POSITIONED_STATEMENTS[1]|&#124;SQL_PS_SELECT_FOR_UPDATE&#124; SQL_PS_POSITIONED_UPDATESQL_PS_POSITIONED_DELETE&#124;|  
|SQL_ROW_UPDATES|"Y"|  
|SQL_SCROLL_CONCURRENCY[1]|&#124;SQL_SCCO_OPT_VALUESSQL_SCCO_READ_ONLY|  
|SQL_SCROLL_OPTIONS|SQL_SO_FORWARD_ONLY &#124; SQL_SO_STATIC|  
|SQL_STATIC_SENSITIVITY[1]|SQL_SS_UPDATES|  
  
 [1] ODBC 2.x ドライバでカーソル ライブラリを使用する場合にのみ使用します。  
  
> [!IMPORTANT]  
>  カーソル ライブラリは、トランザクションがデータ ソースとしてコミットまたはロールバックされるときと同じカーソル動作を実装します。 つまり **、SQLEndTran**を呼び出すか、SQL_ATTR_AUTOCOMMIT接続属性を使用してトランザクションをコミットまたはロールバックすると、データ ソースがアクセス プランを削除し、接続上のすべてのステートメントのカーソルを閉じる可能性があります。 詳細については、 [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)のSQL_CURSOR_COMMIT_BEHAVIORおよびSQL_CURSOR_ROLLBACK_BEHAVIOR情報型を参照してください。
