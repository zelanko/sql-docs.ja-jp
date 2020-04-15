---
title: '付録 B: ODBC 状態遷移テーブル |マイクロソフトドキュメント'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- state transitions [ODBC]
- transitioning states [ODBC], about state transitions
- state transitions [ODBC], about state transitions
ms.assetid: 15088dbe-896f-4296-b397-02bb3d0ac0fb
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: db20c492ababbe6bf8f065fce88067c643f2694d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302886"
---
# <a name="appendix-b-odbc-state-transition-tables"></a>付録 B: ODBC の状態遷移テーブル
この付録の表は、ODBC 関数が環境、接続、ステートメント、および記述子の状態を遷移させる方法を示しています。 環境、接続、ステートメント、または記述子の状態は、通常、対応するタイプのハンドル (環境、接続、ステートメント、または記述子) を使用する関数を呼び出すことができる場合に指示します。 環境、接続、ステートメント、および記述子の状態は、次の図に示すように大まかに重複しています。 たとえば、接続状態 C5 と C6 の正確な重複とステートメント状態 S1 から S12 は、トランザクションが異なるデータ ソースで異なる時間に開始され、記述子状態 D1i (暗黙的に割り当てられた記述子) は記述子が関連付けられているステートメントの状態に依存し、状態 D1e (明示的に割り当てられた記述子) は、ステートメントの状態に依存しません。 各状態の詳細については、後の「[環境遷移](../../../odbc/reference/appendixes/environment-transitions.md)、[接続遷移](../../../odbc/reference/appendixes/connection-transitions.md)、[ステートメント遷移](../../../odbc/reference/appendixes/statement-transitions.md)、[および記述子遷移](../../../odbc/reference/appendixes/descriptor-transitions.md)」を参照してください。  
  
 環境と接続状態は、次のように重複します。  
  
 ![環境と接続の状態の重複](../../../odbc/reference/appendixes/media/app01.gif "app01")  
  
 接続とステートメントの状態は、次のように重複します。  
  
 ![接続とステートメントの状態の重複](../../../odbc/reference/appendixes/media/app02.gif "app02")  
  
 ステートメントと記述子の状態は、次のように重複します。  
  
 ![ステートメントと記述子の状態の重複](../../../odbc/reference/appendixes/media/app03.gif "app03")  
  
 接続状態と記述子状態は、次のように重複します。  
  
 ![接続と記述子の状態の重複](../../../odbc/reference/appendixes/media/app04.gif "app04")  
  
 遷移テーブルの各エントリは、次のいずれかの値になります。  
  
-   **--**-関数の実行後、状態は変更されません。  
  
-   **E**  

     **_n_** **、C_n_、S_n_、** または**S_n_****D_n_** - 環境、接続、ステートメント、または記述子の状態を指定された状態に移動します。  
 
-   **(IH)** - 無効なハンドルが関数に渡されました。 ハンドルが null ハンドルであったり、間違った型の有効なハンドルであった場合 (たとえば、ステートメント ハンドルが必要になったときに接続ハンドルが渡された場合) 関数はSQL_INVALID_HANDLE返します。それ以外の場合、動作は未定義であり、おそらく致命的です。 このエラーは、指定された状態で関数を呼び出した唯一の結果である場合にのみ表示されます。 このエラーは状態を変更せず、かっこで示されているように、ドライバー マネージャーによって常に検出されます。  
  
-   **NS** - 次の状態。 ステートメントの遷移は、ステートメントが非同期状態を通過していない場合と同じです。 たとえば **、SQLExecDirect**がSQL_STILL_EXECUTINGを返したために、結果セットを作成するステートメントが状態 S11 から状態 S11 に入ったとします。 状態 S11 の NS 表記は、ステートメントの遷移が結果セットを作成する状態 S1 のステートメントの遷移と同じであることを意味します。 **SQLExecDirect が**エラーを返す場合、ステートメントは S1 状態のままです。成功すると、ステートメントは状態 S5 に移動します。データが必要な場合、ステートメントは S8 状態に移行します。まだ実行している場合は、状態 S11 のままです。  

-   **_XXXXX_** または **(*XXXXX*)** - 遷移表に関連する SQLSTATE。ドライバー マネージャーによって検出された SQLSTATE は、かっこで囲まれています。 関数はSQL_ERRORと指定された SQLSTATE を返しましたが、状態は変わりません。 たとえば **、SQLPrepare**の前に呼**SQLPrepare**び出された場合、SQLSTATE HY010 (関数シーケンス エラー) が返されます。  

> [!NOTE]  
>  テーブルには、状態を変更しない遷移テーブルとは無関係のエラーは表示されません。 たとえば、環境状態 E1 で**SQLAllocHandle**が呼び出され、SQLSTATE HY001 (メモリ割り当てエラー) を返すと、環境は状態 E1 のままです。これは**SQLAllocHandle**の環境遷移テーブルには表示されません。  
  
 環境、接続、ステートメント、または記述子が複数の状態に移行できる場合は、それぞれの可能な状態が表示され、1 つ以上の脚注が各遷移が行われる条件を説明します。 次の脚注は、どのテーブルにも表示されます。  
  
|脚注|意味|  
|--------------|-------------|  
|b|前または後。 カーソルは、結果セットの開始前、または結果セットの終了後に位置付けされました。|  
|c|現在の関数。 現在の関数が非同期で実行されていました。|  
|d|データが必要です。 SQL_NEED_DATA返される関数。|  
|e|エラーが発生します。 関数がSQL_ERRORを返しました。|  
|i|無効な行です。 カーソルが結果セットの行に置かれていたが、その行が削除されたか、または行の操作でエラーが発生した。 行状況配列が存在する場合、行の行状況配列の値はSQL_ROW_DELETEDまたはSQL_ROW_ERROR。 (行の状態の配列は、SQL_ATTR_ROW_STATUS_PTR ステートメント属性によって示されます。|  
|nf|見つかりません。 SQL_NO_DATA返される関数。 これは、検索された更新ステートメントまたは削除ステートメントの実行後に **、SQLExecDirect** **、SQLExecute、** または**SQLParamData**がSQL_NO_DATAを返す場合には適用されません。|  
|np|準備ができていません。 声明は準備されていませんでした。|  
|nr|結果がありません。 ステートメントは結果セットを作成しないか、作成しませんでした。|  
|o|その他の機能。 別の関数が非同期で実行されていました。|  
|p|準備。 声明は準備されました。|  
|r|結果。 ステートメントは、(おそらく空の)結果セットを作成します。|  
|s|正常終了しました。 SQL_SUCCESS_WITH_INFOまたはSQL_SUCCESSを返す関数。|  
|v|有効な行。 カーソルが結果セット内の行に位置し、行が正常に挿入されたか、更新されたか、または行に対する別の操作が正常に完了しました。 行状況配列が存在する場合、行の行状況配列の値は、SQL_ROW_ADDED、SQL_ROW_SUCCESS、またはSQL_ROW_UPDATED。 (行の状態の配列は、SQL_ATTR_ROW_STATUS_PTR ステートメント属性によって示されます。|  
|x|実行。 SQL_STILL_EXECUTING返される関数。|  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
 この例では *、HandleType*がSQL_HANDLE_ENVされている場合の**SQLFreeHandle**の環境状態遷移テーブルの行は次のようになります。  
  
|E0<br /><br /> 未割り当て|E1<br /><br /> Allocated|E2<br /><br /> Connection|  
|------------------------|----------------------|-----------------------|  
|(IH)|E0|(HY010)|  
  
 **SqlFreeHandle**がSQL_HANDLE_ENVに設定された*ハンドルの種類*で環境状態 E0 で呼び出された場合、ドライバー マネージャーはSQL_INVALID_HANDLEを返します。 *HandleType*が SQL_HANDLE_ENV に設定された状態 E1 で呼び出された場合、関数が成功すると環境は状態 E0 に移行し、関数が失敗した場合は状態 E1 に留まります。 *ハンドルの種類*がSQL_HANDLE_ENVに設定されている状態 E2 で呼び出された場合、ドライバー マネージャーは常に SQL_ERRORと SQLSTATE HY010 (関数シーケンス エラー) を返し、環境は状態 E2 のままです。  
  
 状態遷移表を理解するには、どの項目 (環境、接続、ステートメント、または記述子) を参照するかを理解する必要があります。 関数が型 X の項目のハンドルを受け取っているとします。その関数の X 状態遷移テーブルでは、関数を呼び出す場合、型 X の項目のハンドルがその項目にどのように影響するかを説明します。 たとえば **、SQLDisconnect**は接続ハンドルを受け入れます。 **SQLDisconnect**の接続状態遷移テーブルでは **、SQLDisconnect**が呼び出される接続の状態にどのように影響するかについて説明します。  
  
 関数が Y 型の項目のハンドルを受け取っているとします。その関数の X 状態遷移テーブルは、タイプ Y の項目に関連付けられたタイプ X のハンドルを使用して関数を呼び出すと、タイプ Y の項目にどのような影響を与えるかを説明します。たとえば **、SQLDisconnect**のステートメント状態遷移テーブルでは **、SQLDisconnect**が、ステートメントが関連付けられている接続のハンドルを使用して呼び出されたときのステートメントの状態に対する SQLDisconnect の影響について説明します。  
  
 この付録では、以下のトピックを取り上げます。  
  
-   [環境の遷移](../../../odbc/reference/appendixes/environment-transitions.md)  
  
-   [接続の遷移](../../../odbc/reference/appendixes/connection-transitions.md)  
  
-   [ステートメントの遷移](../../../odbc/reference/appendixes/statement-transitions.md)  
  
-   [記述子の遷移](../../../odbc/reference/appendixes/descriptor-transitions.md)
