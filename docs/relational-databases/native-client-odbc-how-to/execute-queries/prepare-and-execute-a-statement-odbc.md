---
title: ステートメントの準備と実行 (ODBC) |マイクロソフトドキュメント
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: eaf7e3518f369639ba3d2eb854a103ff839276c7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294124"
---
# <a name="prepare-and-execute-a-statement-odbc"></a>ステートメントの準備と実行 (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

    
### <a name="to-prepare-a-statement-once-and-then-execute-it-multiple-times"></a>ステートメントを 1 回だけ準備して複数回実行するには  
  
1.  [SQLPrepare 関数を](https://go.microsoft.com/fwlink/?LinkId=59360)呼び出して、ステートメントを準備します。  
  
2.  オプションで[、SQLNumParams](https://go.microsoft.com/fwlink/?LinkId=58404)を呼び出して、準備されたステートメント内のパラメーターの数を決定します。  
  
3.  必要に応じて、準備されたステートメント内の各パラメーターに対して次の操作を行います。  
  
    -   パラメータ情報を取得するには[、SQLDescribe パラム](../../../relational-databases/native-client-odbc-api/sqldescribeparam.md)を呼び出します。  
  
    -   [SQLBindParameter](../../../relational-databases/native-client-odbc-api/sqlbindparameter.md)を使用して、各パラメーターをプログラム変数にバインドします。 実行時データ パラメーターをセットアップします。  
  
4.  準備されたステートメントの各実行に対して次の操作を行います。  
  
    -   ステートメントにパラメーター マーカーがある場合は、バインドされたパラメーター バッファーにデータ値を格納します。  
  
    -   [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400)を呼び出して、準備されたステートメントを実行します。  
  
    -   実行時のデータ入力パラメーターが使用されている場合[、SQLExecute は](https://go.microsoft.com/fwlink/?LinkId=58400)SQL_NEED_DATAを返します。 データをチャンクで送信する場合は[、SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405)と[SQLPutData](../../../relational-databases/native-client-odbc-api/sqlputdata.md)を使用します。  
  
### <a name="to-prepare-a-statement-with-column-wise-parameter-binding"></a>列方向のパラメーターのバインドを使用してステートメントを準備するには  
  
1.  次の属性を設定するには[、SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)を呼び出します。  
  
    -   SQL_ATTR_PARAMSET_SIZE に、パラメーターのセット数 (S) を設定します。  
  
    -   SQL_ATTR_PARAM_BIND_TYPE を SQL_PARAMETER_BIND_BY_COLUMN に設定します。  
  
    -   SQL_ATTR_PARAMS_PROCESSED_PTR 属性を、処理されたパラメーターの数を格納する SQLUINTEGER 変数を指すように設定します。  
  
    -   SQL_ATTR_PARAMS_STATUS_PTR を、パラメーターの状態インジケーターを格納する SQLUSSMALLINT 変数の配列[S] を指すように設定します。  
  
2.  SQLPrepare を呼び出してステートメントを準備します。  
  
3.  オプションで[、SQLNumParams](https://go.microsoft.com/fwlink/?LinkId=58404)を呼び出して、準備されたステートメント内のパラメーターの数を決定します。  
  
4.  必要に応じて、準備されたステートメントの各パラメーターに対して、SQLDescribeParam を呼び出してパラメーター情報を取得します。  
  
5.  各パラメーター マーカーについて、次の操作を行います。  
  
    -   データ値を格納する S パラメーター バッファーの配列を割り当てます。  
  
    -   データの長さを格納する S パラメーター バッファーの配列を割り当てます。  
  
    -   SQLBindParameter を呼び出して、パラメーターのデータ値とデータ長の配列をステートメント パラメーターにバインドします。  
  
    -   パラメーターが実行時データの text または image パラメーターである場合は、それをセットアップします。  
  
    -   実行時データ パラメーターを使用する場合は、それらをセットアップします。  
  
6.  準備されたステートメントの各実行に対して次の操作を行います。  
  
    -   S データ値と S データ長をバインドされたパラメーター配列に入れます。  
  
    -   SQLExecute を呼び出して、準備されたステートメントを実行します。  
  
    -   実行時データ入力パラメーターが使用されている場合、SQLExecute は SQL_NEED_DATA を返します。 データをチャンクで送信する場合は、SQLParamData と SQLPutData を使用します。  
  
### <a name="to-prepare-a-statement-with-row-wise-bound-parameters"></a>行方向にバインドされたパラメーターを使用してステートメントを準備するには  
  
1.  構造体の配列[S] を割り当てます。この S は行パラメーターのセット数です。 構造体には各パラメーターについて 1 つの要素があり、各要素は次の 2 つの部分で構成されています。  
  
    -   最初の部分は、パラメーター データを格納する適切なデータ型の変数です。  
  
    -   2 つ目の部分は、状態インジケーターを格納する SQLINTEGER 変数です。  
  
2.  次の属性を設定するには[、SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)を呼び出します。  
  
    -   SQL_ATTR_PARAMSET_SIZE に、パラメーターのセット数 (S) を設定します。  
  
    -   SQL_ATTR_PARAM_BIND_TYPE を、手順 1. で割り当てた構造体のサイズに設定します。  
  
    -   SQL_ATTR_PARAMS_PROCESSED_PTR 属性を、処理されたパラメーターの数を格納する SQLUINTEGER 変数を指すように設定します。  
  
    -   SQL_ATTR_PARAMS_STATUS_PTR を、パラメーターの状態インジケーターを格納する SQLUSSMALLINT 変数の配列[S] を指すように設定します。  
  
3.  SQLPrepare を呼び出してステートメントを準備します。  
  
4.  各パラメーター・マーカーについて、SQLBindParameter を呼び出して、ステップ 1 で割り振った構造体の配列の最初のエレメント内の変数をパラメーター・データ値およびデータ長ポインターに指定します。 パラメーターが実行時データ パラメーターである場合は、そのパラメーターをセットアップします。  
  
5.  準備されたステートメントの各実行に対して次の操作を行います。  
  
    -   バインドされたパラメーターのバッファー配列にデータ値を入力します。  
  
    -   SQLExecute を呼び出して、準備されたステートメントを実行します。 ドライバーによって、S 回 (パラメーターのセットごとに 1 回) SQL ステートメントが効率よく実行されます。  
  
    -   実行時データ入力パラメーターが使用されている場合、SQLExecute は SQL_NEED_DATA を返します。 データをチャンクで送信する場合は、SQLParamData と SQLPutData を使用します。  
  
## <a name="see-also"></a>参照  
 [ODBC&#41;のクエリハウツートピック&#40;実行](../../../relational-databases/native-client-odbc-how-to/execute-queries/executing-queries-how-to-topics-odbc.md)  
  
  
