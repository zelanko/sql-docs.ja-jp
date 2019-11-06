---
title: 準備し、ステートメントの実行 (ODBC) |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- statement execution
- statement preparation
ms.assetid: 0adecc63-4da5-486c-bc48-09a004a2fae6
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3fd2ff0c2dae01c10b720ed31fee88430a82cbe0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67898521"
---
# <a name="prepare-and-execute-a-statement-odbc"></a>ステートメントの準備と実行 (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

    
### <a name="to-prepare-a-statement-once-and-then-execute-it-multiple-times"></a>ステートメントを 1 回だけ準備して複数回実行するには  
  
1.  呼び出す[SQLPrepare 関数](https://go.microsoft.com/fwlink/?LinkId=59360)ステートメントを準備します。  
  
2.  必要に応じて、呼び出す[SQLNumParams](https://go.microsoft.com/fwlink/?LinkId=58404)準備されたステートメントのパラメーターの数を決定します。  
  
3.  必要に応じて、準備されたステートメント内の各パラメーターに対して次の操作を行います。  
  
    -   呼び出す[SQLDescribeParam](../../../relational-databases/native-client-odbc-api/sqldescribeparam.md)パラメーター情報を取得します。  
  
    -   使用して、各パラメーターをプログラム変数にバインド[SQLBindParameter](../../../relational-databases/native-client-odbc-api/sqlbindparameter.md)します。 実行時データ パラメーターをセットアップします。  
  
4.  準備されたステートメントの各実行に対して次の操作を行います。  
  
    -   ステートメントにパラメーター マーカーがある場合は、バインドされたパラメーター バッファーにデータ値を格納します。  
  
    -   呼び出す[SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400)準備されたステートメントを実行します。  
  
    -   実行時データ入力パラメーターを使用している場合[SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) SQL_NEED_DATA を返します。 使用して、データをチャンク単位で送信[SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405)と[SQLPutData](../../../relational-databases/native-client-odbc-api/sqlputdata.md)します。  
  
### <a name="to-prepare-a-statement-with-column-wise-parameter-binding"></a>列方向のパラメーターのバインドを使用してステートメントを準備するには  
  
1.  呼び出す[SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)次の属性を設定します。  
  
    -   SQL_ATTR_PARAMSET_SIZE に、パラメーターのセット数 (S) を設定します。  
  
    -   SQL_ATTR_PARAM_BIND_TYPE を SQL_PARAMETER_BIND_BY_COLUMN に設定します。  
  
    -   SQL_ATTR_PARAMS_PROCESSED_PTR 属性を、処理されたパラメーターの数を格納する SQLUINTEGER 変数を指すように設定します。  
  
    -   SQL_ATTR_PARAMS_STATUS_PTR を、パラメーターの状態インジケーターを格納する SQLUSSMALLINT 変数の配列[S] を指すように設定します。  
  
2.  SQLPrepare ステートメントの準備を呼び出します。  
  
3.  必要に応じて、呼び出す[SQLNumParams](https://go.microsoft.com/fwlink/?LinkId=58404)準備されたステートメントのパラメーターの数を決定します。  
  
4.  必要に応じて、準備されたステートメント内の各パラメーターのパラメーター情報を取得する SQLDescribeParam を呼び出します。  
  
5.  各パラメーター マーカーについて、次の操作を行います。  
  
    -   データ値を格納する S パラメーター バッファーの配列を割り当てます。  
  
    -   データの長さを格納する S パラメーター バッファーの配列を割り当てます。  
  
    -   ステートメントのパラメーターにパラメーター データの値とデータ長の配列をバインドする場合は、SQLBindParameter を呼び出します。  
  
    -   パラメーターが実行時データの text または image パラメーターである場合は、それをセットアップします。  
  
    -   実行時データ パラメーターを使用する場合は、それらをセットアップします。  
  
6.  準備されたステートメントの各実行に対して次の操作を行います。  
  
    -   S データ値および S データの長さをバインドされたパラメーター配列に格納します。  
  
    -   準備されたステートメントを実行する SQLExecute を呼び出します。  
  
    -   実行時データ入力パラメーターを使用している場合、SQLExecute は SQL_NEED_DATA を返します。 SQLParamData と SQLPutData を使用してチャンク単位でデータを送信します。  
  
### <a name="to-prepare-a-statement-with-row-wise-bound-parameters"></a>行方向にバインドされたパラメーターを使用してステートメントを準備するには  
  
1.  構造体の配列[S] を割り当てます。この S は行パラメーターのセット数です。 構造体には各パラメーターについて 1 つの要素があり、各要素は次の 2 つの部分で構成されています。  
  
    -   最初の部分は、パラメーター データを格納する適切なデータ型の変数です。  
  
    -   2 つ目の部分は、状態インジケーターを格納する SQLINTEGER 変数です。  
  
2.  呼び出す[SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)次の属性を設定します。  
  
    -   SQL_ATTR_PARAMSET_SIZE に、パラメーターのセット数 (S) を設定します。  
  
    -   SQL_ATTR_PARAM_BIND_TYPE を、手順 1. で割り当てた構造体のサイズに設定します。  
  
    -   SQL_ATTR_PARAMS_PROCESSED_PTR 属性を、処理されたパラメーターの数を格納する SQLUINTEGER 変数を指すように設定します。  
  
    -   SQL_ATTR_PARAMS_STATUS_PTR を、パラメーターの状態インジケーターを格納する SQLUSSMALLINT 変数の配列[S] を指すように設定します。  
  
3.  SQLPrepare ステートメントの準備を呼び出します。  
  
4.  各パラメーター マーカーについて、手順 1. で割り当てた構造体の配列の最初の要素では、その変数をパラメーター データの値とデータ長のポインターを指す SQLBindParameter を呼び出します。 パラメーターが実行時データ パラメーターである場合は、そのパラメーターをセットアップします。  
  
5.  準備されたステートメントの各実行に対して次の操作を行います。  
  
    -   バインドされたパラメーターのバッファー配列にデータ値を入力します。  
  
    -   準備されたステートメントを実行する SQLExecute を呼び出します。 ドライバーによって、S 回 (パラメーターのセットごとに 1 回) SQL ステートメントが効率よく実行されます。  
  
    -   実行時データ入力パラメーターを使用している場合、SQLExecute は SQL_NEED_DATA を返します。 SQLParamData と SQLPutData を使用してチャンク単位でデータを送信します。  
  
## <a name="see-also"></a>関連項目  
 [クエリを実行方法に関するトピック&#40;ODBC&#41;](../../../relational-databases/native-client-odbc-how-to/execute-queries/executing-queries-how-to-topics-odbc.md)  
  
  
