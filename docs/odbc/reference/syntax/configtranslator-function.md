---
title: ConfigTranslator 関数 |Microsoft ドキュメント
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
- ConfigTranslator
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- ConfigTranslator
helpviewer_keywords:
- ConfigTranslator [ODBC]
ms.assetid: 7c22f07e-36de-425b-aa67-e32a84afae92
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8b0c064453d84d10037eb1360c20b2fab8ecb1d8
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="configtranslator-function"></a>ConfigTranslator 関数
**準拠**  
 バージョンが導入されています。 ODBC 2.0  
  
 **概要**  
 **ConfigTranslator**トランスレーターの既定の変換オプションを返します。 これは、トランスレーター DLL または別のセットアップ DLL に存在できます。  
  
## <a name="syntax"></a>構文  
  
```  
  
BOOL ConfigTranslator(  
     HWND     hwndParent,  
     DWORD *  pvOption);  
```  
  
## <a name="arguments"></a>引数  
 *hwndParent*  
 [入力]親ウィンドウ ハンドル。 関数では、ハンドルが null の場合、ダイアログ ボックスは表示されません。  
  
 *pvOption*  
 [出力]32 ビットの変換オプション。  
  
## <a name="returns"></a>戻り値  
 関数は、それが成功した場合、FALSE が失敗した場合に TRUE を返します。  
  
## <a name="diagnostics"></a>診断  
 ときに**ConfigTranslator**は FALSE を返します、関連付けられている *\*pfErrorCode*への呼び出しで値がインストーラー エラー バッファーにポストされた**SQLPostInstallerError**と呼び出すことによって取得できます**SQLInstallerError**です。 次の表、  *\*pfErrorCode*によって返される値**SQLInstallerError**とコンテキストでこの関数のいずれかを説明します。  
  
|*\*pfErrorCode*|[エラー]|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_HWND|無効なウィンドウ ハンドル|*HwndParent*引数が無効または NULL。|  
|ODBC_ERROR_DRIVER_SPECIFIC|ドライバー固有またはトランスレーター エラー|定義された ODBC インストーラーのエラーがないドライバー固有のエラーです。 *SzError*への呼び出しで引数、 **SQLPostInstallerError**関数は、ドライバー固有のエラー メッセージを含める必要があります。|  
|ODBC_ERROR_INVALID_OPTION|無効な変換オプション|*PvOption*引数に無効な値が含まれています。|  
  
## <a name="comments"></a>コメント  
 トランスレーターが 1 つの翻訳オプションのみをサポートしている場合**ConfigTranslator** TRUE を返し、セット*pvOption*オプションの 32 ビットにします。 それ以外の場合、既定の変換を使用するオプションを決定します。 **ConfigTranslator**ユーザーが既定の変換オプションを選択 ダイアログ ボックスを表示できます。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|変換オプションを取得します。|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|翻訳者を選択します。|[SQLGetTranslator](../../../odbc/reference/syntax/sqlgettranslator-function.md)|  
|翻訳オプションの設定|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|
