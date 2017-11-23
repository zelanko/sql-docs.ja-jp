---
title: "ステートメントを実行して、直接 (ODBC) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-how-to
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: statement execution
ms.assetid: b690f9de-66e1-4ee5-ab6a-121346fb5f85
caps.latest.revision: "12"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2910a47227b9ee20a3d39eb115639d3374758228
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="execute-a-statement-directly-odbc"></a>ステートメントの直接実行 (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

    
### <a name="to-execute-a-statement-directly-and-one-time-only"></a>ステートメントを直接一度だけ実行するには  
  
1.  ステートメントにパラメーター マーカーがある場合を使用して[SQLBindParameter](../../../relational-databases/native-client-odbc-api/sqlbindparameter.md)各パラメーターをプログラム変数にバインドします。 プログラム変数にデータ値を入力してから、実行時データ パラメーターをセットアップします。  
  
2.  呼び出す[SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399)ステートメントを実行します。  
  
3.  実行時データ入力パラメーターを使用している場合[SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399) SQL_NEED_DATA を返します。 使用してデータをチャンク単位で送信[SQLParamData](http://go.microsoft.com/fwlink/?LinkId=58405)と[SQLPutData](../../../relational-databases/native-client-odbc-api/sqlputdata.md)です。  
  
### <a name="to-execute-a-statement-multiple-times-by-using-column-wise-parameter-binding"></a>列方向のパラメーターのバインドを使用してステートメントを複数回実行するには  
  
1.  呼び出す[SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)を次の属性を設定します。  
  
     SQL_ATTR_PARAMSET_SIZE に、パラメーターのセット数 (S) を設定します。  
  
     SQL_ATTR_PARAM_BIND_TYPE を SQL_PARAMETER_BIND_BY_COLUMN に設定します。  
  
     SQL_ATTR_PARAMS_PROCESSED_PTR 属性を、処理されたパラメーターの数を格納する SQLUINTEGER 変数を指すように設定します。  
  
     Sql_attr_params_status_ptr をパラメーターの状態インジケーターを格納する SQLUSSMALLINT 変数の配列 [S] を指すように設定します。  
  
2.  各パラメーター マーカーについて、次の操作を行います。  
  
     データ値を格納する S パラメーター バッファーの配列を割り当てます。  
  
     データの長さを格納する S パラメーター バッファーの配列を割り当てます。  
  
     呼び出す[SQLBindParameter](../../../relational-databases/native-client-odbc-api/sqlbindparameter.md)ステートメント パラメーターにパラメーター データの値とデータの長さの配列をバインドします。  
  
     実行時データ テキストまたはイメージ パラメーターをセットアップします。  
  
     S データ値および S データの長さを、バインドされたパラメーター配列に置きます。  
  
3.  呼び出す[SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399)ステートメントを実行します。 ドライバーによって、S 回 (パラメーターのセットごとに 1 回) ステートメントが効率よく実行されます。  
  
4.  実行時データ入力パラメーターを使用している場合[SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399) SQL_NEED_DATA を返します。 使用してデータをチャンク単位で送信[SQLParamData](http://go.microsoft.com/fwlink/?LinkId=58405)と[SQLPutData](../../../relational-databases/native-client-odbc-api/sqlputdata.md)です。  
  
### <a name="to-execute-a-statement-multiple-times-by-using-row-wise-parameter-binding"></a>行方向のパラメーターのバインドを使用してステートメントを複数回実行するには  
  
1.  構造体の配列[S] を割り当てます。この S は行パラメーターのセット数です。 構造体には各パラメーターについて 1 つの要素があり、各要素は次の 2 つの部分で構成されています。  
  
     最初の部分は、パラメーター データを格納する適切なデータ型の変数です。  
  
     2 つ目の部分は、状態インジケーターを格納する SQLINTEGER 変数です。  
  
2.  呼び出す[SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)を次の属性を設定します。  
  
     SQL_ATTR_PARAMSET_SIZE に、パラメーターのセット数 (S) を設定します。  
  
     SQL_ATTR_PARAM_BIND_TYPE を、手順 1. で割り当てた構造体のサイズに設定します。  
  
     SQL_ATTR_PARAMS_PROCESSED_PTR 属性を、処理されたパラメーターの数を格納する SQLUINTEGER 変数を指すように設定します。  
  
     Sql_attr_params_status_ptr をパラメーターの状態インジケーターを格納する SQLUSSMALLINT 変数の配列 [S] を指すように設定します。  
  
3.  各パラメーター マーカーを呼び出して[SQLBindParameter](../../../relational-databases/native-client-odbc-api/sqlbindparameter.md)に手順 1. で割り当てた構造体の配列の最初の要素にある変数をパラメーターのデータ値とデータ長のポインターをポイントします。 パラメーターが実行時データ パラメーターである場合は、そのパラメーターをセットアップします。  
  
4.  バインドされたパラメーターのバッファー配列にデータ値を入力します。  
  
5.  呼び出す[SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399)ステートメントを実行します。 ドライバーによって、S 回 (パラメーターのセットごとに 1 回) ステートメントが効率よく実行されます。  
  
6.  実行時データ入力パラメーターを使用している場合[SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399) SQL_NEED_DATA を返します。 使用してデータをチャンク単位で送信[SQLParamData](http://go.microsoft.com/fwlink/?LinkId=58405)と[SQLPutData](../../../relational-databases/native-client-odbc-api/sqlputdata.md)です。  
  
 **注**列方向と行方向のバインドはより、通常使用と組み合わせて[SQLPrepare 関数](http://go.microsoft.com/fwlink/?LinkId=59360)と[SQLExecute](http://go.microsoft.com/fwlink/?LinkId=58400)よりと[SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399).  
  
## <a name="see-also"></a>参照  
 [実行中のクエリの操作方法に関するトピック &#40; ODBC &#41;](../../../relational-databases/native-client-odbc-how-to/execute-queries/executing-queries-how-to-topics-odbc.md)  
  
  
