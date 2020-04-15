---
title: 環境遷移 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- environment transitions [ODBC]
- transitioning states [ODBC], environment
- state transitions [ODBC], environment
ms.assetid: 9d11b1ab-f4c8-48ca-9812-8c04303f939d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ebfb5475d24d5fc70c4cb46a666b2573066565a1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283302"
---
# <a name="environment-transitions"></a>環境の遷移
ODBC 環境には、次の 3 つの状態があります。  
  
|State|説明|  
|-----------|-----------------|  
|E0|未割り当て環境|  
|E1|割り当て済み環境、未割り当て接続|  
|E2|割り当て済み環境、割り当て済み接続|  
  
 次の表は、各 ODBC 関数が環境状態に与える影響を示しています。  
  
## <a name="sqlallochandle"></a>ハンドル  
  
|E0<br /><br /> 未割り当て|E1<br /><br /> Allocated|E2<br /><br /> Connection|  
|------------------------|----------------------|-----------------------|  
|E1[1]|--[4]|--[4]|  
|(IH)[2]|E2[5]<br />(HY010)[6]|--[4]|  
|(IH)[3]|(IH)|--[4]|  
  
 [1] この行は *、HandleType*がSQL_HANDLE_ENVされたときの遷移を示しています。  
  
 [2] この行は *、HandleType*がSQL_HANDLE_DBCされたときの遷移を示しています。  
  
 [3] この行は *、HandleType*がSQL_HANDLE_STMTまたはSQL_HANDLE_DESCされたときの遷移を示しています。  
  
 有効なハンドルを指し示す*を*指定して**SQLAllocHandle**を呼び出すと、そのハンドルが上書きされます。 これは、アプリケーション・プログラミング・エラーである可能性があります。  
  
 [5] 環境にSQL_ATTR_ODBC_VERSION環境属性が設定されていた。  
  
 [6] 環境にSQL_ATTR_ODBC_VERSION環境属性が設定されていなかった。  
  
## <a name="sqldatasources-and-sqldrivers"></a>SQL データソースと SQL ドライバー  
  
|E0<br /><br /> 未割り当て|E1<br /><br /> Allocated|E2<br /><br /> Connection|  
|------------------------|----------------------|-----------------------|  
|(IH)|--[1]<br />(HY010)[2]|--[1]<br />(HY010)[2]|  
  
 [1] 環境にSQL_ATTR_ODBC_VERSION環境属性が設定されていた。  
  
 [2] 環境にSQL_ATTR_ODBC_VERSION環境属性が設定されていません。  
  
## <a name="sqlendtran"></a>SQLEndTran  
  
|E0<br /><br /> 未割り当て|E1<br /><br /> Allocated|E2<br /><br /> Connection|  
|------------------------|----------------------|-----------------------|  
|(IH)[1]|--[3]<br />(HY010)[4]|--[3]<br />(HY010)[4]|  
|(IH)[2]|(IH)|--|  
  
 [1] この行は *、HandleType*がSQL_HANDLE_ENVされたときの遷移を示しています。  
  
 [2] この行は *、HandleType*がSQL_HANDLE_DBCされたときの遷移を示しています。  
  
 [3] 環境属性SQL_ATTR_ODBC_VERSION環境に設定されています。  
  
 [4] 環境にSQL_ATTR_ODBC_VERSION環境属性が設定されていません。  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|E0<br /><br /> 未割り当て|E1<br /><br /> Allocated|E2<br /><br /> Connection|  
|------------------------|----------------------|-----------------------|  
|(IH)[1]|E0|(HY010)|  
|(IH)[2]|(IH)|--[4]<br />E1[5]|  
|(IH)[3]|(IH)|--|  
  
 [1] この行は *、HandleType*がSQL_HANDLE_ENVされたときの遷移を示しています。  
  
 [2] この行は *、HandleType*がSQL_HANDLE_DBCされたときの遷移を示しています。  
  
 [3] この行は *、HandleType*がSQL_HANDLE_STMTまたはSQL_HANDLE_DESCされたときの遷移を示しています。  
  
 [4] 他の割り当てられた接続ハンドルがあった。  
  
 [5]*ハンドル*で指定された接続ハンドルが唯一割り当てられた接続ハンドルでした。  
  
## <a name="sqlgetdiagfield-and-sqlgetdiagrec"></a>フィールドと SQL を取得します。  
  
|E0<br /><br /> 未割り当て|E1<br /><br /> Allocated|E2<br /><br /> Connection|  
|------------------------|----------------------|-----------------------|  
|(IH)[1]|--|--|  
|(IH)[2]|(IH)|--|  
  
 [1] この行は *、HandleType*がSQL_HANDLE_ENVされたときの遷移を示しています。  
  
 [2] この行は *、HandleType*がSQL_HANDLE_DBC、SQL_HANDLE_STMT、またはSQL_HANDLE_DESCされたときの遷移を示しています。  
  
## <a name="sqlgetenvattr"></a>アズ・ビジトル  
  
|E0<br /><br /> 未割り当て|E1<br /><br /> Allocated|E2<br /><br /> Connection|  
|------------------------|----------------------|-----------------------|  
|(IH)|--[1]<br />(HY010)[2]|--|  
  
 [1] 環境にSQL_ATTR_ODBC_VERSION環境属性が設定されていた。  
  
 [2] 環境にSQL_ATTR_ODBC_VERSION環境属性が設定されていません。  
  
## <a name="sqlsetenvattr"></a>SQLSetEnvAttr  
  
|E0<br /><br /> 未割り当て|E1<br /><br /> Allocated|E2<br /><br /> Connection|  
|------------------------|----------------------|-----------------------|  
|(IH)|--[1]<br />(HY010)[2]|(HY011)|  
  
 [1] 環境にSQL_ATTR_ODBC_VERSION環境属性が設定されていた。  
  
 Attribute*引数が*SQL_ATTR_ODBC_VERSIONされず、環境にSQL_ATTR_ODBC_VERSION環境属性が設定されていなかった。  
  
## <a name="all-other-odbc-functions"></a>その他すべての ODBC 関数  
  
|E0<br /><br /> 未割り当て|E1<br /><br /> Allocated|E2<br /><br /> Connection|  
|------------------------|----------------------|-----------------------|  
|(IH)|(IH)|--|
