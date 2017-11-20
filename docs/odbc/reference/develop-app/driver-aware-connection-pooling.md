---
title: "ドライバー対応接続プール |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53e7e3f7-edab-4d0b-8943-45442ba3ebc9
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: bf5c6405d4492a4cf559c3a62f53f69eb8a3fdeb
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="driver-aware-connection-pooling"></a>ドライバー対応接続プール
ドライバー対応接続プールは、Windows 8 では、ドライバー マネージャーの新しい機能です。 ドライバー対応接続プールにより、ドライバーの作成者に、接続プールの ODBC ドライバーでの動作をカスタマイズできます。  
  
> [!NOTE]  
>  ドライバー対応接続プールは、カーソル ライブラリではサポートされていません。 アプリケーションでは、ドライバー対応接続プールが有効になっているときに、SQLSetConnectAttr 経由でのカーソル ライブラリを有効にしようとしている場合は、エラー メッセージが表示されます。  
  
 ドライバー対応接続アドレスをプールは次の問題は、ドライバー マネージャーの接続プールに関連します。  
  
 **プールの断片化**ドライバー マネージャーはから返されるだけ接続プールの新しい接続要求の接続文字列と正確に一致である場合。  完全一致を要求するように、ドライバー マネージャーの理由の 1 つは、すべてのドライバー固有の接続文字列キーワードと値、ドライバー マネージャーによって認識されないです。  ただし、ドライバーは、データベース (の正確な時刻の差は、データ ソースによって異なります) の新しい接続を開くために必要な時間よりも小さい値を変更できるため、いくつかの接続文字列キーワードの値 (など、データベースの名前) には、完全に一致するは不要です。 また、一部の接続属性 SQL_ATTR_CURRENT_CATALOG) などの相違点の相違 (SQL_ATTR_LOGIN_TIMEOUT) などその他の属性よりも変更する時間がかかります。 これには、すぎる、できなくなるドライバー マネージャーは、最低コスト、再利用可能な接続プールを使用して、します。 多くの新しい接続を作成する場合、ドライバー、アプリケーションのパフォーマンスが低下することができ、データ ソースのスケーラビリティが低下する可能性がします。 ドライバー対応接続プールをドライバーがより正確に接続要求は、プール内の接続を再利用のコストを見積もるためのプールの断片化を削減できます。  
  
 **アプリケーションの基本設定の無関係**一部のデータ ソースを効率的に新しい接続を開きます (一部の属性をリセットすると比較して) ため、アプリケーションが少し不一致を再利用を試みることがなく新しい接続を開きたい場合がありますプールとリセットのいくつかの値 (ただし低速接続プールの初期化句の中にはこの可能性があります) からの接続。 一部のアプリケーション可能性があります、サーバーの負荷を小さく保ち、適切な動作の不一致を修正する大きなコストである可能性がありますが、接続の数を少なくを開きます。 ドライバー対応接続プールなしを指定できません 基本設定のこのような実際には、ドライバー マネージャーがすべてのドライバー固有の接続属性を認識しないため。 ドライバー対応接続プールにより、ドライバーをできるように、ユーザーの設定に基づいて、プールからの接続を再利用のコストがより正確に見積もることができます (SQLSetConnectAttr のドライバー固有の属性) を持つユーザーの設定を取得できます。  
  
 ドライバー対応接続プールの詳細については、次を参照してください。 [ODBC ドライバーで接続プールの認識開発](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)です。  
  
## <a name="determining-driver-support"></a>ドライバーのサポートを決定します。  
 ドライバー対応接続プールは、省略可能な機能のドライバーをサポートしない可能性があります。 調べるかどうか、ドライバーでサポートされるを使用して、SQL_DRIVER_AWARE_POOLING_SUPPORTED*情報の種類*の[SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)です。  
  
## <a name="how-to-enable-driver-aware-connection-pooling"></a>ドライバー対応接続プールを有効にする方法  
 SQL_CP_DRIVER_AWARE に SQL_ATTR_CONNECTION_POOLING 属性を設定して、アプリケーションがドライバーの接続プールの認識を使用して[SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md)です。 ドライバーは接続プールの認識をサポートしていない場合、ドライバー マネージャーの接続プールが使用されます (SQL_CP_DRIVER_AWARE ではなく、SQL_CP_ONE_PER_HENV が指定されていた場合と同じ)。 ODBC 2.x、3.x アプリケーションには、この機能が有効にすることができます。  
  
## <a name="see-also"></a>参照  
 [ODBC ドライバーの開発](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)

