---
title: エラー メッセージ (ビジュアル フォックスプロ ODBC ドライバー) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- error messages [ODBC], Visual FoxPro ODBC driver
- Visual FoxPro ODBC driver [ODBC], error messages
- SQLSTATE [ODBC]
- FoxPro ODBC driver [ODBC], error messages
ms.assetid: 58ea9734-4edf-44da-ba80-938aa7b340e4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 31f894e58da93fe6091dba306f8b765d14bac2cb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286402"
---
# <a name="error-messages-visual-foxpro-odbc-driver"></a>エラー メッセージ (Visual FoxPro ODBC ドライバー)
エラーが発生すると、Visual FoxPro ドライバーは、次の情報を返します。  
  
-   ネイティブエラー番号とエラー メッセージ テキスト  
  
-   SQLSTATE (ODBC エラー・コード) およびエラー・メッセージ・テキスト  
  
 このエラー情報にアクセスする場合[は、 SQLError](../../odbc/microsoft/sqlerror-visual-foxpro-odbc-driver.md)を呼び出します。  
  
## <a name="native-errors"></a>ネイティブ エラー  
 データ ソースで発生したエラーの場合、Visual FoxPro ドライバーは、ネイティブエラー番号とエラー メッセージ テキストを返します。 ネイティブ エラー番号の一覧については、「 [Visual FoxPro ODBC ドライバー ネイティブ エラー メッセージ](../../odbc/microsoft/visual-foxpro-odbc-driver-native-error-messages.md)」を参照してください。  
  
## <a name="sqlstate-odbc-error-codes"></a>SQLSTATE (ODBC エラー コード)  
 Visual FoxPro ドライバーによって検出され、返されるエラーの場合、ドライバーは、返されたネイティブ エラー番号を適切な SQLSTATE にマップします。 ネイティブ エラー番号に対応付ける ODBC エラー コードがない場合、Visual FoxPro ドライバは SQLSTATE S1000 (一般エラー) を返します。  
  
 対応するビジュアル FoxPro エラーに対してビジュアル フォックスプロ ODBC ドライバーによって生成される SQLSTATE 値の一覧については[、ODBC エラー コード](../../odbc/microsoft/odbc-error-codes-visual-foxpro-odbc-driver.md)を参照してください。  
  
## <a name="syntax"></a>構文  
 エラー メッセージの形式は次のとおりです。  
  
 **[** *仕入先* **] [** *ODBC_component* **]** *error_message*  
  
 角かっこ ([]) 内のプレフィックスは、次の表で定義されているエラーの原因を示します。  
  
|データ ソース|Prefix|[値]|  
|-----------------|------------|-----------|  
|ドライバー マネージャー|[ベンダー]<br />[ODBC_component]<br />[data_source]|[Microsoft]<br />[ODBC ドライバー マネージャー]<br />該当なし|  
|ビジュアルフォックスプロドライバー|ベンダー]<br />[ODBC_component]<br />[data_source]|[Microsoft]<br />[ODBC ビジュアル フォックスプロ ドライバー]<br />該当なし|  
  
 たとえば、ファイルの employee.dbf を見つけることができなかった場合、次のエラー メッセージが返される可能性があります。  
  
 "[*マイクロソフト**][ODBCビジュアルフォックスプロドライバ*]ファイル 'employee.dbf'が存在しません」
