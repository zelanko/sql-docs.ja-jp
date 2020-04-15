---
title: 直接ステートメントを実行する (ODBC) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- statement execution
ms.assetid: b690f9de-66e1-4ee5-ab6a-121346fb5f85
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9a4516f25ee6d18ddb56bedab1e55a2924c03873
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294226"
---
# <a name="execute-a-statement-directly-odbc"></a>ステートメントの直接実行 (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

    
### <a name="to-execute-a-statement-directly-and-one-time-only"></a>ステートメントを直接一度だけ実行するには  
  
1.  ステートメントにパラメーター・マーカーがある場合は[、SQLBindParameter を](../../../relational-databases/native-client-odbc-api/sqlbindparameter.md)使用して各パラメーターをプログラム変数にバインドします。 プログラム変数にデータ値を入力してから、実行時データ パラメーターをセットアップします。  
  
2.  ステートメントを実行するには[、SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399)を呼び出します。  
  
3.  実行時のデータ入力パラメーターが使用されている場合は[、SQL_NEED_DATA](https://go.microsoft.com/fwlink/?LinkId=58399)返します。 データをチャンクで送信する場合は[、SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405)と[SQLPutData](../../../relational-databases/native-client-odbc-api/sqlputdata.md)を使用します。  

### <a name="to-execute-a-statement-multiple-times-by-using-column-wise-parameter-binding"></a>列方向のパラメーターのバインドを使用してステートメントを複数回実行するには  
  
1.  次の属性を設定するには[、SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)を呼び出します。  
  
     SQL_ATTR_PARAMSET_SIZE に、パラメーターのセット数 (S) を設定します。  
  
     SQL_ATTR_PARAM_BIND_TYPE を SQL_PARAMETER_BIND_BY_COLUMN に設定します。  
  
     SQL_ATTR_PARAMS_PROCESSED_PTR 属性を、処理されたパラメーターの数を格納する SQLUINTEGER 変数を指すように設定します。  
  
     パラメータステータスインジケータを保持するSQLUSSMALLINT変数の配列[S]を指すSQL_ATTR_PARAMS_STATUS_PTRを設定します。  
  
2.  各パラメーター マーカーについて、次の操作を行います。  
  
     データ値を格納する S パラメーター バッファーの配列を割り当てます。  
  
     データの長さを格納する S パラメーター バッファーの配列を割り当てます。  
  
     [SQLBindParameter](../../../relational-databases/native-client-odbc-api/sqlbindparameter.md)を呼び出して、パラメーターのデータ値とデータ長の配列をステートメント パラメーターにバインドします。  
  
     実行時データ テキストまたはイメージ パラメーターをセットアップします。  
  
     S データ値および S データの長さを、バインドされたパラメーター配列に置きます。  
  
3.  ステートメントを実行するには[、SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399)を呼び出します。 ドライバーによって、S 回 (パラメーターのセットごとに 1 回) ステートメントが効率よく実行されます。  
  
4.  実行時のデータ入力パラメーターが使用されている場合は[、SQL_NEED_DATA](https://go.microsoft.com/fwlink/?LinkId=58399)返します。 データをチャンクで送信する場合は[、SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405)と[SQLPutData](../../../relational-databases/native-client-odbc-api/sqlputdata.md)を使用します。  
  
### <a name="to-execute-a-statement-multiple-times-by-using-row-wise-parameter-binding"></a>行方向のパラメーターのバインドを使用してステートメントを複数回実行するには  
  
1.  構造体の配列[S] を割り当てます。この S は行パラメーターのセット数です。 構造体には各パラメーターについて 1 つの要素があり、各要素は次の 2 つの部分で構成されています。  
  
     最初の部分は、パラメーター データを格納する適切なデータ型の変数です。  
  
     2 つ目の部分は、状態インジケーターを格納する SQLINTEGER 変数です。  
  
2.  次の属性を設定するには[、SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)を呼び出します。  
  
     SQL_ATTR_PARAMSET_SIZE に、パラメーターのセット数 (S) を設定します。  
  
     SQL_ATTR_PARAM_BIND_TYPE を、手順 1. で割り当てた構造体のサイズに設定します。  
  
     SQL_ATTR_PARAMS_PROCESSED_PTR 属性を、処理されたパラメーターの数を格納する SQLUINTEGER 変数を指すように設定します。  
  
     パラメータステータスインジケータを保持するSQLUSSMALLINT変数の配列[S]を指すSQL_ATTR_PARAMS_STATUS_PTRを設定します。  
  
3.  各パラメーター・マーカーについて[、SQLBindParameter](../../../relational-databases/native-client-odbc-api/sqlbindparameter.md)を呼び出して、ステップ 1 で割り振った構造体の配列の最初のエレメント内の変数をパラメーターのデータ値およびデータ長ポインターに指定します。 パラメーターが実行時データ パラメーターである場合は、そのパラメーターをセットアップします。  
  
4.  バインドされたパラメーターのバッファー配列にデータ値を入力します。  
  
5.  ステートメントを実行するには[、SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399)を呼び出します。 ドライバーによって、S 回 (パラメーターのセットごとに 1 回) ステートメントが効率よく実行されます。  
  
6.  実行時のデータ入力パラメーターが使用されている場合は[、SQL_NEED_DATA](https://go.microsoft.com/fwlink/?LinkId=58399)返します。 データをチャンクで送信する場合は[、SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405)と[SQLPutData](../../../relational-databases/native-client-odbc-api/sqlputdata.md)を使用します。  
  
 **注**列方向および行方向のバインディングは[、SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399)よりも[SQLPrepare 関数](https://go.microsoft.com/fwlink/?LinkId=59360)および[SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400)と共に使用される方が一般的です。  
  
## <a name="see-also"></a>参照  
 [ODBC&#41;のクエリハウツートピック&#40;実行](../../../relational-databases/native-client-odbc-how-to/execute-queries/executing-queries-how-to-topics-odbc.md)  
  
  
