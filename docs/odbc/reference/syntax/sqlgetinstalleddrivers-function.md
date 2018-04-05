---
title: SQLGetInstalledDrivers 関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- SQLGetInstalledDrivers
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetInstalledDrivers
helpviewer_keywords:
- SQLGetInstalledDrivers function [ODBC]
ms.assetid: a1983a2e-0edf-422e-bd1b-ec5db40a34bc
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 64b8479b23f76c8af74be77b4f44e3bca6f8a6f6
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="sqlgetinstalleddrivers-function"></a>SQLGetInstalledDrivers 関数
**準拠**  
 1.0 ODBC のバージョンで導入されました。  
  
 **概要**  
 **SQLGetInstalledDrivers**システム情報 [ODBC Drivers] セクションを読み取るし、インストールされたドライバーの説明の一覧を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
BOOL SQLGetInstalledDrivers(  
     LPSTR   lpszBuf,  
     WORD    cbBufMax,  
     WORD *  pcbBufOut);  
```  
  
## <a name="arguments"></a>引数  
 *lpszBuf*  
 [出力]インストールされているドライバーの記述のリスト。 リスト構造については、「コメント」を参照してください。  
  
 *cbBufMax*  
 [入力]長さ*lpszBuf*です。  
  
 *pcbBufOut*  
 [出力]合計バイト数 (null 終了バイトを除く) で返される*lpszBuf*です。 場合は、使用できるバイト数を返すより大きいまたは等しい*cbBufMax*でのドライバーの説明の一覧*lpszBuf*に切り捨てられます*cbBufMax*マイナス、null 終端文字です。 *PcbBufOut*引数が null ポインターを指定できます。  
  
## <a name="returns"></a>戻り値  
 関数は、それが成功した場合、FALSE が失敗した場合に TRUE を返します。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLGetInstalledDrivers**は FALSE を返します、関連付けられている *\*pfErrorCode*を呼び出して値を取得する**SQLInstallerError**です。 次の表、  *\*pfErrorCode*によって返される値**SQLInstallerError**とコンテキストでこの関数のいずれかを説明します。  
  
|*\*pfErrorCode*|[エラー]|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|一般的なインストーラーのエラー|エラーが発生する特定のインストーラーのエラーがなかった。|  
|ODBC_ERROR_INVALID_BUFF_LEN|無効なバッファーの長さ|*LpszBuf*引数が NULL または無効、または*cbBufMax*引数が 0 未満です。|  
|ODBC_ERROR_COMPONENT_NOT_FOUND|コンポーネントがレジストリに見つかりません|インストーラーは、レジストリで、[ODBC Drivers] セクションを見つけられませんでした。|  
|ODBC_ERROR_OUT_OF_MEM|メモリ不足|インストーラーは、メモリの不足のため、関数を実行できませんでした。|  
  
## <a name="comments"></a>コメント  
 各ドライバーの説明は、null バイトで終了し、null バイトのリスト全体が終了します。 (つまり、2 つの null バイトの末尾を示す一覧です。)場合は、割り当てられたバッファーのサイズが不十分リスト全体を保持するために、エラーが発生せず、一覧は切り捨てられます。 Null ポインターとして渡される場合、エラーが返されます*lpszBuf*です。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|ドライバーの説明と属性を返す|[SQLDrivers](../../../odbc/reference/syntax/sqldrivers-function.md)|
