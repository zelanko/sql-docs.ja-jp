---
title: SQLGetConnectOption 関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLGetConnectOption
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetConnectOption
helpviewer_keywords:
- SQLGetConnectOption function [ODBC]
ms.assetid: 59cde899-7957-4b5e-8677-f34d3b859bfd
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: da57d3d508355777f7c5033e4b47f8964e9bb0d6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32917677"
---
# <a name="sqlgetconnectoption-function"></a>SQLGetConnectOption 関数
**準拠**  
 バージョンで導入された: ODBC 1.0 標準準拠: 非推奨  
  
 **概要**  
 ODBC 3 *.x*、ODBC 2 *.x*関数**SQLGetConnectOption**代わりました**SQLGetConnectAttr**です。 詳細については、次を参照してください。 [SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)です。  
  
> [!NOTE]  
>  詳細については、どのようなドライバー マネージャーは、この関数にする際にマップ ODBC 2 *.x*アプリケーションは、ODBC 3 と連携して *.x*ドライバーを参照してください[非推奨機能のマッピング](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)旧バージョンとの互換性のための付録 g: ドライバーのガイドライン」にします。  
  
> [!NOTE]  
>  ODBC 3.8 で導入された SQL_ASYNC_DBC_FUNCTION_ENABLE 属性はサポートされていません**SQLGetConnectOption**です。 接続ハンドルでの非同期操作を使用するアプリケーションが使用する必要があります**SQLGetConnectAttr**です。  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
