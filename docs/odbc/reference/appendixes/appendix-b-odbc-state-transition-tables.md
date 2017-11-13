---
title: "付録 b: ODBC 状態遷移テーブル |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- state transitions [ODBC]
- transitioning states [ODBC], about state transitions
- state transitions [ODBC], about state transitions
ms.assetid: 15088dbe-896f-4296-b397-02bb3d0ac0fb
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 775c3d0464443d11b833a230591b94293343086b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="appendix-b-odbc-state-transition-tables"></a>付録 b: ODBC 状態遷移のテーブル
この付録の内容の表では、ODBC 関数による環境、接続、ステートメント、および記述子の状態の遷移の発生を示しています。 通常、環境、接続、ステートメント、または記述子の状態は、ハンドル (環境、接続、ステートメント、または記述子) の対応する型を使用する関数を呼び出すことができる場合は決定します。 環境、接続、ステートメント、および記述子の状態は次の図に示すようにほぼと重複します。 たとえば、接続の正確な重複の状態の C5 と C6、S1 S12 からはデータ ソースに依存する、さまざまなデータ ソースに異なる時刻でトランザクションを開始し、記述子の状態 (暗黙的に割り当てられた記述子) D1i 依存ステートメントの状態記述子が関連付けられているステートメントの状態、状態 (明示的に割り当てられた記述子) D1e 中には任意のステートメントの状態に依存しないです。 各状態の説明は、次を参照してください[環境遷移](../../../odbc/reference/appendixes/environment-transitions.md)、[接続遷移](../../../odbc/reference/appendixes/connection-transitions.md)、[ステートメント遷移](../../../odbc/reference/appendixes/statement-transitions.md)、および[記述子遷移。](../../../odbc/reference/appendixes/descriptor-transitions.md)、後の「します。  
  
 環境と接続の状態は、次のように重複します。  
  
 ![環境と接続の状態の重複](../../../odbc/reference/appendixes/media/app01.gif "app01")  
  
 接続とステートメントの状態は次のとおり重複します。  
  
 ![接続とステートメントの状態が重なっている](../../../odbc/reference/appendixes/media/app02.gif "app02")  
  
 ステートメントと記述子の状態は次のとおり重複します。  
  
 ![ステートメントと記述子の状態が重なっている](../../../odbc/reference/appendixes/media/app03.gif "app03")  
  
 接続と記述子の状態は次のとおり重複します。  
  
 ![接続と記述子の状態が重なっている](../../../odbc/reference/appendixes/media/app04.gif "app04")  
  
 移行テーブル内の各エントリには、次の値のいずれかを指定できます。  
  
-   **--**、関数を実行した後状態は変更されません。  
  
-   **E**  
     ***n***、  **C*n***、  **S*n***、または**D*n** *、環境、接続、ステートメント、または記述子の状態が指定した状態に移動します。  
  
-   **(組み込み)** : 関数に無効なハンドルが渡されました。 場合は、ハンドルが null のハンドルか、誤った型の有効なハンドル — など、接続ハンドルが、ステートメント ハンドルが必要なときに渡されました: SQL_INVALID_HANDLE 以外を返しますそれ以外の場合の動作は未定義と致命的な可能性があります。 このエラーは、指定された状態で、関数の呼び出しの可能な唯一の結果である場合にのみに表示されます。 このエラーは、状態は変更されませんありが常に検出されたドライバー マネージャーによって、かっこで示されます。  
  
-   **NS** : 次の状態。 ステートメントの移行は、ステートメントが非同期状態を完了していない場合と同じです。 たとえば、結果セットを作成するステートメントの状態に S11 状態 S1 からため**SQLExecDirect** SQL_STILL_EXECUTING が返されます。 状態 S11 NS 表記では、ステートメントの遷移と同じ状態 S1 内のステートメントの結果セットを作成することを意味します。 場合**SQLExecDirect**エラーを返します、ステートメントは状態 S1 のまま以外の場合は成功した場合、ステートメントに移動 S5 を記述する以外の場合はデータを必要とする場合、ステートメント S8; の状態をし移動がまだ実行中の場合 S11 の状態のままにします。  
  
-   ***XXXXX***または **(*XXXXX*) * *-移行テーブルに関連付けられている、SQLSTATESQLSTATEs ドライバー マネージャーによって検出されたは、かっこで囲まれます。 関数から SQL_ERROR と指定の SQLSTATE 返されましたが、状態は変更されません。 たとえば場合、 **SQLExecute**前に呼び出されます**SQLPrepare**、SQLSTATE HY010 が返されます (関数のシーケンス エラーです)。  
  
> [!NOTE]  
>  テーブルでは、状態を変更しない移行テーブルに関係のないエラーは表示されません。 たとえば、 **SQLAllocHandle** E1 環境の状態で呼び出され、SQLSTATE HY001 を返します (メモリ割り当てエラー) は、環境の状態のまま E1 ですこれは、用の環境移行テーブルに表示されません**。SQLAllocHandle**です。  
  
 環境、接続、ステートメント、または記述子は、1 つ以上の状態に移動できる場合、考えられる各状態を示すし、1 つまたは複数の脚注が、条件を各遷移が行わを説明します。 次の脚注任意のテーブルで表示されます。  
  
|脚注|意味|  
|--------------|-------------|  
|b|前に、または後にします。 または、結果セットの終了後に結果セットの開始前に、カーソルが配置されました。|  
|c|現在の関数。 現在の関数は非同期的に実行しています。|  
|d|データを必要とします。 関数には、SQL_NEED_DATA が返されます。|  
|e|エラー状態。 関数には、SQL_ERROR が返されます。|  
|i|行が無効です。 カーソルの位置が結果内の行セットといずれかの行が削除されたか、行に対して操作でエラーが発生しました。 行の状態配列が存在する場合は、行の状態配列内の行の値が SQL_ROW_DELETED または SQL_ROW_ERROR。 (行の状態配列を指す SQL_ATTR_ROW_STATUS_PTR ステートメント属性です。)|  
|%nf|見つかりませんでした。 関数には、SQL_NO_DATA が返されます。 これは適用されないとき**SQLExecDirect**、 **SQLExecute**、または**SQLParamData**更新または delete ステートメントを検索を実行した後 SQL_NO_DATA が返されます。|  
|np|準備されていません。 ステートメントが準備されていませんでした。|  
|nr|結果はありません。 ステートメントは、されませんまたは結果セットを作成できませんでした。|  
|o|その他の関数。 別の関数は非同期的に実行しています。|  
|p|準備ができているとします。 ステートメントが準備されました。|  
|r|結果。 または (おそらく空) の結果セットを作成してステートメントです。|  
|s|正常終了しました。 関数には、SQL_SUCCESS_WITH_INFO または SQL_SUCCESS が返されます。|  
|v|有効な行です。 カーソルが結果セット内の行に配置されていると、行が正常に挿入された、正常に更新または行に対する別の操作が正常に完了しました。 行の状態配列が存在する場合は、行の状態配列内の行の値が SQL_ROW_ADDED、SQL_ROW_SUCCESS、または SQL_ROW_UPDATED です。 (行の状態配列を指す SQL_ATTR_ROW_STATUS_PTR ステートメント属性です。)|  
|x|実行中。 関数には、SQL_STILL_EXECUTING が返されます。|  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
 テーブルではこの例では、環境の状態遷移内の行の**SQLFreeHandle**とき*HandleType*は sql_handle_env としては次のようにします。  
  
|E0<br /><br /> 未割り当て|E1<br /><br /> 割り当てられています。|E2<br /><br /> 接続|  
|------------------------|----------------------|-----------------------|  
|(組み込み)|E0|(HY010)|  
  
 場合**SQLFreeHandle**環境状態 E0 で呼び出される*HandleType* SQL_INVALID_HANDLE が返されない、ドライバー マネージャーを SQL_HANDLE_ENV に設定します。 使用して状態 E1 で呼び出された場合*HandleType* SQL_HANDLE_ENV に設定すると、環境を E0 状態の場合は、関数が成功し、関数が失敗した場合に、E1 の状態のままに移動します。 使用して状態 E2 で呼び出された場合*HandleType* SQL_HANDLE_ENV に設定すると、ドライバー マネージャーは、常に返します SQL_ERROR と SQLSTATE HY010 (関数のシーケンス エラー)、環境の状態のまま E2 とします。  
  
 状態遷移のテーブルを理解するのを参照しているアイテム (環境、接続、ステートメント、または記述子) を理解する必要があります。 関数は、項目の種類 X のハンドルを受け入れるとします。その関数の X の状態遷移表では、どの呼び出し元関数 X の種類のアイテムのハンドルを使用してそのがアイテムに影響について説明します。 たとえば、 **SQLDisconnect**接続ハンドルを受け入れます。 接続の状態遷移表**SQLDisconnect**説明方法**SQLDisconnect**呼び出されますが、接続の状態に影響します。  
  
 関数は、Y が X と等しくない、項目の種類、Y のハンドルを受け入れるとします。その関数の X の状態遷移表では、どの呼び出し Y、型の項目に関連付けられている型のハンドルである関数に影響を与える型 Y の項目について説明します。たとえば、ステートメントの状態遷移表の**SQLDisconnect**について説明する方法**SQLDisconnect**を持つ接続のハンドルを使用して呼び出されたときに、ステートメントの状態に影響しますステートメントは、関連付けられます。  
  
 この付録の内容には、次のトピックが含まれています。  
  
-   [環境の移行](../../../odbc/reference/appendixes/environment-transitions.md)  
  
-   [接続の切り替え](../../../odbc/reference/appendixes/connection-transitions.md)  
  
-   [ステートメントの遷移](../../../odbc/reference/appendixes/statement-transitions.md)  
  
-   [記述子の遷移](../../../odbc/reference/appendixes/descriptor-transitions.md)

