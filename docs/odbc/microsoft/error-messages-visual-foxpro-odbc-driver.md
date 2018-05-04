---
title: エラー メッセージ (Visual FoxPro ODBC ドライバー) |Microsoft ドキュメント
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
- error messages [ODBC], Visual FoxPro ODBC driver
- Visual FoxPro ODBC driver [ODBC], error messages
- SQLSTATE [ODBC]
- FoxPro ODBC driver [ODBC], error messages
ms.assetid: 58ea9734-4edf-44da-ba80-938aa7b340e4
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4f6be0c46b1dcc777004edacda8a490438db438c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="error-messages-visual-foxpro-odbc-driver"></a>エラー メッセージ (Visual FoxPro ODBC ドライバー)
エラーが発生するときに、Visual FoxPro ドライバーには、次の情報が返されます。  
  
-   ネイティブ エラー番号とエラー メッセージ テキスト  
  
-   SQLSTATE (ODBC エラー コード) とエラー メッセージ テキスト  
  
 呼び出すことによってこのエラーの情報にアクセスする[SQLError](../../odbc/microsoft/sqlerror-visual-foxpro-odbc-driver.md)です。  
  
## <a name="native-errors"></a>ネイティブのエラー  
 データ ソースで発生したエラーの場合は、Visual FoxPro ドライバーは、ネイティブ エラー番号とエラー メッセージ テキストを返します。 ネイティブ エラー番号の一覧は、次を参照してください。 [Visual FoxPro ODBC ドライバー ネイティブのエラー メッセージ](../../odbc/microsoft/visual-foxpro-odbc-driver-native-error-messages.md)です。  
  
## <a name="sqlstate-odbc-error-codes"></a>SQLSTATE (ODBC エラー コード)  
 検出され、Visual FoxPro ドライバーによって返されるエラーの場合は、ドライバーは、返されたネイティブ エラー番号を適切な SQLSTATE にマップされます。 ネイティブ エラー番号にマップする ODBC エラー コードを持たない場合、Visual FoxPro ドライバーは SQLSTATE S1000 を返します (一般的なエラー)。  
  
 Visual FoxPro ODBC ドライバーは、対応する Visual FoxPro エラーによって生成される SQLSTATE 値の一覧は、次を参照してください。 [ODBC エラー コード](../../odbc/microsoft/odbc-error-codes-visual-foxpro-odbc-driver.md)です。  
  
## <a name="syntax"></a>構文  
 エラー メッセージでは、次の形式があります。  
  
 **[** *仕入先* **] [** *ODBC_component* **]** *error_message*  
  
 角かっこ () 内のプレフィックスは、次の表で定義されているエラーの原因を特定します。  
  
|データ ソース|Prefix|値|  
|-----------------|------------|-----------|  
|ドライバー マネージャー|[ベンダー]<br />[ODBC_component]<br />[data_source]|[Microsoft]<br />[ODBC ドライバー マネージャー]<br />なし|  
|Visual FoxPro ドライバー|仕入先]<br />[ODBC_component]<br />[data_source]|[Microsoft]<br />[ODBC Visual FoxPro driver]<br />なし|  
  
 たとえば、Visual FoxPro ODBC ドライバーは、見つかりませんでした。 ファイル employee.dbf と、次のエラー メッセージが返す可能性があります。  
  
 "[*Microsoft*] [*ODBC Visual FoxPro ドライバー*] 'employee.dbf' ファイルが存在しない"
