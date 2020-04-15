---
title: ドライバー対応接続プール |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 53e7e3f7-edab-4d0b-8943-45442ba3ebc9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 70b70c841f37bd69179137c807c0dadcfd932d2b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287602"
---
# <a name="driver-aware-connection-pooling"></a>ドライバー対応接続プール
ドライバー対応接続プールは、Windows 8 のドライバー マネージャーの新機能です。 ドライバー対応接続プールを使用すると、ドライバーの作成者は、ODBC ドライバーでの接続プールの動作をカスタマイズできます。  
  
> [!NOTE]  
>  ドライバー対応接続プールは、カーソル ライブラリではサポートされていません。 アプリケーションは、SQLSetConnectAttr を使用してカーソル ライブラリを有効にしようとすると、エラー メッセージを受け取ります。  
  
 ドライバー対応接続プールは、ドライバー マネージャーの接続プールに関連する次の問題を解決します。  
  
 **プールの断片化**ドライバー マネージャーは、プールから接続が新しい接続要求の接続文字列と完全に一致する場合にのみ、接続を返します。  ドライバー マネージャーが完全一致を要求する理由の 1 つは、ドライバー マネージャーがドライバー固有の接続文字列キーワードとその値を理解しないことです。  ただし、一部の接続文字列キーワード値 (データベース名など) は、新しい接続を開くために必要な時間よりも短い時間でデータベースを変更できるため、正確に一致する必要はありません (正確な時間差はデータ ソースによって異なります)。 また、一部の接続属性 (SQL_ATTR_CURRENT_CATALOGなど) の違いは、他の属性 (SQL_ATTR_LOGIN_TIMEOUTなど) の違いよりも変更に時間がかかります。 これも、ドライバー マネージャーがプールから最も低コストで再利用可能な接続を使用するのを防ぐことができます。 ドライバーが多数の新しい接続を作成する必要がある場合、アプリケーションのパフォーマンスが低下し、データ ソースのスケーラビリティが低下する可能性があります。 ドライバーは、接続要求のプールで接続を再利用するコストを見積もることができるので、プールの断片化は、ドライバー対応接続プールで削減できます。  
  
 **アプリケーションの好みの考慮なし**一部のデータ ソースは、新しい接続を効率的に開くことができる (一部の属性をリセットする場合と比較して) ため、アプリケーションはプールから少し不一致の接続を再利用して値をリセットするのではなく、新しい接続を開くことを好む場合があります (ただし、接続プールの初期化句の間に時間がかかる場合があります)。 ただし、アプリケーションによっては、サーバーの負荷を小さく抑え、接続を開く回数を減らしますが、正しい動作のために不一致を修正するコストが大きくなる可能性があります。 ドライバー マネージャーでは、ドライバー固有の接続属性を認識しないため、ドライバー対応接続プールを使用しないと、この種の優先順位を効果的に指定することはできません。 ドライバー対応接続プールを使用すると、ドライバーはユーザー設定を取得できます (ドライバー固有の属性 SQLSetConnectAttr) を使用して、ユーザーの好みに基づいてプールから接続を再利用するコストをより良く見積もることができます。  
  
 ドライバー対応接続プールの詳細については[、「ODBC ドライバーでの接続プール認識の開発](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)」を参照してください。  
  
## <a name="determining-driver-support"></a>ドライバのサポートの決定  
 ドライバー対応接続プールは、ドライバーがサポートしない可能性があるオプションの機能です。 ドライバーがサポートしているかどうかを確認するには、 [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)の*SQL_DRIVER_AWARE_POOLING_SUPPORTEDの情報の種類*を使用します。  
  
## <a name="how-to-enable-driver-aware-connection-pooling"></a>ドライバー対応接続プールを有効にする方法  
 アプリケーションは[、sqlSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md)でSQL_CP_DRIVER_AWAREにSQL_ATTR_CONNECTION_POOLING属性を設定することで、ドライバーの接続プールの認識を使用できます。 ドライバーが接続プールの認識をサポートしていない場合は、ドライバー マネージャーの接続プールが使用されます (SQL_CP_ONE_PER_HENV指定された場合と同じSQL_CP_DRIVER_AWARE)。 ODBC 2.x および 3.x アプリケーションでは、この機能を有効にできます。  
  
## <a name="see-also"></a>参照  
 [ODBC ドライバーの開発](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)
