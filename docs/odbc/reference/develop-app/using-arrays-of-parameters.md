---
title: "パラメーターの配列の使用 |Microsoft ドキュメント"
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
- arrays of parameter values [ODBC]
- parameter arrays [ODBC]
ms.assetid: 5a28be88-e171-4f5b-bf4d-543c4383c869
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a7c6a6ee4f066925d2a7ec46a2186134d75cb7e4
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="using-arrays-of-parameters"></a>パラメーターの配列の使用
アプリケーションの呼び出し、パラメーターの配列を使用する**SQLSetStmtAttr**で、*属性*SQL_ATTR_PARAMSET_SIZE パラメーター セットの数を指定の引数。 呼び出す**SQLSetStmtAttr**で、*属性*SQL_ATTR_PARAMS_PROCESSED_PTR ドライバーが処理された、パラメーターのセットの数を返すことができます、変数のアドレスを指定の引数などのエラーを設定します。 呼び出す**SQLSetStmtAttr**で、*属性*パラメーター値の行ごとに状態情報を返す対象の配列を指す SQL_ATTR_PARAM_STATUS_PTR の引数。 ドライバーは、ステートメントを保持する構造体でこれらのアドレスを格納します。  
  
> [!NOTE]  
>  ODBC 2 です。*x*、 **SQLParamOptions**パラメーターの複数の値を指定して呼び出されました。 ODBC 3 です。*x*への呼び出し**SQLParamOptions**への呼び出しから置き換え**SQLSetStmtAttr** SQL_ATTR_PARAMSET_SIZE と SQL_ATTR_PARAMS_PROCESSED_ARRAY 属性を設定するには.  
  
 ステートメントを実行する前に、アプリケーションは、各バインドの配列の各要素の値を設定します。 ドライバーはパラメーター値を取得し、データ ソースに格納されている情報を使用して、ステートメントの実行時可能であれば、ドライバーは、配列としてこれらの値を送信する必要があります。 パラメーターの配列の使用は、データ ソースに 1 回の呼び出しで配列内のすべてのパラメーターを含む SQL ステートメントを実行することによって実装が最適、この機能が Dbms で広く利用可能な今日です。 ただし、ドライバーをシミュレートできます、それぞれパラメーターの 1 つのセットを持つ SQL ステートメントを複数回の実行します。  
  
 アプリケーションでは、パラメーターの配列を使用する前に、アプリケーションで使用される、ドライバーでサポートされていることを確認する必要があります。 これには 2 つの方法があります。  
  
-   パラメーターの配列をサポートするドライバーだけを使用します。 アプリケーション ハード コードこれらのドライバーの名前したり、これらのドライバーのみを使用するユーザーを指示することができます。 カスタム アプリケーションおよび垂直方向のアプリケーションは、通常、限られた一連のドライバーを使用します。  
  
-   実行時のパラメーターの配列のサポートを確認します。 ドライバーは、SQL_ATTR_PARAMSET_SIZE ステートメント属性を 1 より大きい値に設定することである場合に、パラメーターの配列をサポートします。 汎用アプリケーションおよび垂直方向のアプリケーションのパラメーターの配列のサポートをよく、確認の実行時にします。  
  
 呼び出して行の数とパラメーター化された実行の結果セットの可用性を決定できる**SQLGetInfo** SQL_PARAM_ARRAY_ROW_COUNTS と SQL_PARAM_ARRAY_SELECTS オプションを使用します。 **挿入**、**更新**、および**削除**個々 の行の数 (1 つは各パラメーター セット) がいるかどうかを示すステートメント、SQL_PARAM_ARRAY_ROW_COUNTS オプション使用可能な (SQL_PARC_BATCH) または行をカウントするかどうかは、(SQL_PARC_NO_BATCH) いずれかにロールアップされます。 **選択**ステートメント、SQL_PARAM_ARRAY_SELECTS オプションかどうか、結果セットがかを示します (SQL_PAS_BATCH) のパラメーターのセットごとに使用可能な 1 つだけの結果セットは、使用可能な (SQL_PAS_NO_BATCH) かどうか。 ドライバーでは、結果セットの生成 – ステートメント パラメーターの配列を使って実行することはできません、SQL_PARAM_ARRAY_SELECTS は SQL_PAS_NO_SELECT を返します。 パラメーターの配列は、その他の種類のステートメントで使用できるかどうか、特にこれらのステートメントでパラメーターを使用するデータ ソースの特定と ODBC SQL 文法に従わないと、データ ソースの特定を勧めします。  
  
 SQL_ATTR_PARAM_OPERATION_PTR ステートメント属性によって示される配列は、パラメーターの行を無視する使用することができます。 その要素に対応するパラメーターのセットはから除外されて、配列の要素が SQL_PARAM_IGNORE に設定されている場合、 **SQLExecute**または**SQLExecDirect**呼び出します。 SQL_ATTR_PARAM_OPERATION_PTR 属性によって示される配列が割り当てられているアプリケーションによって入力し、ドライバーによって読み取られました。 フェッチされた行を入力パラメーターとして使用する場合は、パラメーター操作配列内の行の状態配列の値を使用できます。  
  
## <a name="error-processing"></a>エラー処理  
 ステートメントの実行中にエラーが発生した場合、実行関数はエラーが返され、エラーを含む行の数に行番号の変数を設定します。 ただし、エラー セットが実行されるまたはエラー セットが実行されます (ただし、期間の終了時刻) の前にすべての行かどうか、すべての行かどうかは、データ ソースの特定を勧めします。 パラメーターのセットが処理されるため、ドライバーは、SQL_ATTR_PARAMS_PROCESSED_PTR ステートメント属性を現在処理されている行の数で指定したバッファーを設定します。 すべては設定エラー セットが実行される点を除いて、する場合、ドライバーはすべての行を処理した後、SQL_ATTR_PARAMSET_SIZE にこのバッファーを設定します。  
  
 場合は、SQL_ATTR_PARAM_STATUS_PTR ステートメント属性を設定すると、 **SQLExecute**または**SQLExecDirect**を返します、*パラメーター状態配列*ステータスを提供します。各一連のパラメーターです。 パラメーター状態配列は、アプリケーションによって割り当てられ、ドライバーによってデータ格納します。 その要素は、パラメーターの行の SQL ステートメントが正常に実行されたかどうか、またはパラメーターのセットを処理中にエラーが発生したかどうかを示します。 エラーが発生した場合、ドライバーは SQL_PARAM_ERROR パラメーター状態配列内の対応する値を設定し、sql_success_with_info が返されます。 アプリケーションでは、どの行が処理された、状態配列を確認できます。 行番号を使用して、アプリケーションできます多くの場合、エラーを修正して処理を再開します。  
  
 呼び出しによって返される SQL_PARAM_ARRAY_ROW_COUNTS と SQL_PARAM_ARRAY_SELECTS オプションによって決まりますが、パラメーター状態配列の使用方法**SQLGetInfo**です。 **挿入**、**更新**、および**削除**SQL_PARAM_ARRAY_ の SQL_PARC_BATCH が返される場合は状態情報がステートメント、パラメーター状態配列に入力されますROW_COUNTS が SQL_PARC_NO_BATCH が返される場合はできません。 **選択**ステートメント、パラメーター状態配列は入力 SQL_PARAM_ARRAY_SELECT、に対して SQL_PAS_BATCH が返される場合、SQL_PAS_NO_BATCH または SQL_PAS_NO_SELECT が返されます。  
  
## <a name="data-at-execution-parameters"></a>実行時データ パラメーター  
 SQL_DATA_AT_EXEC または、SQL_LEN_DATA_AT_EXEC の結果は、長さ/インジケーター配列内の値のいずれかの場合 (*長さ*) マクロをこれらの値のデータに送信された**SQLPutData**通常の方法でします。 このプロセスの次の側面は、すぐに明確ではないために、特別なコメントを注意してください。  
  
-   ドライバーでは、SQL_NEED_DATA を返します、ときに必要なデータの行に行番号の変数のアドレスを設定があります。 単一の値を持つように、アプリケーションは、ドライバーがパラメーターの 1 つのセット内のパラメーター値を要求する順序についてどのような想定を作成できません。 SQL_ATTR_PARAMS_PROCESSED_PTR ステートメント属性で指定したバッファーが、エラーが発生するで指定された行の状態配列内の行の状態の行の番号に設定されている場合は、実行時データ パラメーターの実行でエラーが発生した、SQL_ATTR_PARAM_STATUS_PTR ステートメント属性 SQL_PARAM_ERROR、およびへの呼び出しに設定されて**SQLExecute**、 **SQLExecDirect**、 **SQLParamData**、または**SQLPutData** SQL_ERROR を返します。 このバッファーの内容は不定**SQLExecute**、 **SQLExecDirect**、または**SQLParamData** SQL_STILL_EXECUTING を返します。  
  
-   ドライバーでの値が解釈されないため、 *ParameterValuePtr*の引数**SQLBindParameter**アプリケーションが、配列へのポインターを提供している場合、実行時データ パラメーターの**SQLParamData**いませんを抽出し、アプリケーションをこの配列の要素を返します。 代わりに、アプリケーションのスカラー値が提供を返します。 つまり、によって返される値**SQLParamData**は対象のパラメーターを指定する十分なアプリケーションに必要なデータを送信以外の場合は、アプリケーションが現在の行番号を考慮する必要もします。  
  
     ときにだけでパラメーターの配列の要素の一部は実行時データ パラメーターで、アプリケーションする必要がありますのアドレスを渡すの配列で*ParameterValuePtr*すべてのパラメーターの要素を含むです。 この配列は、実行時データ パラメーターではないパラメーターの通常どおりに解釈されます。 実行時データ パラメーターの値を**SQLParamData**への提供、アプリケーションでは、通常を使用すると、ドライバーを何度でこの要求しているデータを特定するのには、配列のアドレスでは常にします。

