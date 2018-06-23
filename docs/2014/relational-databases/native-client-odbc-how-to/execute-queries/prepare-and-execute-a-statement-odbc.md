---
title: Prepare および Execute ステートメント (ODBC) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- statement execution
- statement preparation
ms.assetid: 0adecc63-4da5-486c-bc48-09a004a2fae6
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 58a3ecf2419f0b3e3b74ba6e3b1a6293d928d550
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36173498"
---
# <a name="prepare-and-execute-a-statement-odbc"></a>ステートメントの準備と実行 (ODBC)
    
### <a name="to-prepare-a-statement-once-and-then-execute-it-multiple-times"></a>ステートメントを 1 回だけ準備して複数回実行するには  
  
1.  呼び出す[SQLPrepare 関数](http://go.microsoft.com/fwlink/?LinkId=59360)ステートメントを準備します。  
  
2.  必要に応じて、呼び出す[SQLNumParams](http://go.microsoft.com/fwlink/?LinkId=58404)を準備されたステートメントのパラメーターの数を決定します。  
  
3.  必要に応じて、準備されたステートメント内の各パラメーターに対して次の操作を行います。  
  
    -   呼び出す[SQLDescribeParam](../../native-client-odbc-api/sqldescribeparam.md)パラメーター情報を取得します。  
  
    -   使用して、各パラメーターをプログラム変数にバインド[SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md)です。 実行時データ パラメーターをセットアップします。  
  
4.  準備されたステートメントの各実行に対して次の操作を行います。  
  
    -   ステートメントにパラメーター マーカーがある場合は、バインドされたパラメーター バッファーにデータ値を格納します。  
  
    -   呼び出す[SQLExecute](http://go.microsoft.com/fwlink/?LinkId=58400)準備されたステートメントを実行します。  
  
    -   実行時データ入力パラメーターを使用している場合[SQLExecute](http://go.microsoft.com/fwlink/?LinkId=58400) SQL_NEED_DATA を返します。 使用してデータをチャンク単位で送信[SQLParamData](http://go.microsoft.com/fwlink/?LinkId=58405)と[SQLPutData](../../native-client-odbc-api/sqlputdata.md)です。  
  
### <a name="to-prepare-a-statement-with-column-wise-parameter-binding"></a>列方向のパラメーターのバインドを使用してステートメントを準備するには  
  
1.  呼び出す[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)を次の属性を設定します。  
  
    -   SQL_ATTR_PARAMSET_SIZE に、パラメーターのセット数 (S) を設定します。  
  
    -   SQL_ATTR_PARAM_BIND_TYPE を SQL_PARAMETER_BIND_BY_COLUMN に設定します。  
  
    -   SQL_ATTR_PARAMS_PROCESSED_PTR 属性を、処理されたパラメーターの数を格納する SQLUINTEGER 変数を指すように設定します。  
  
    -   SQL_ATTR_PARAMS_STATUS_PTR を、パラメーターの状態インジケーターを格納する SQLUSSMALLINT 変数の配列[S] を指すように設定します。  
  
2.  ステートメントの準備 SQLPrepare を呼び出します。  
  
3.  必要に応じて、呼び出す[SQLNumParams](http://go.microsoft.com/fwlink/?LinkId=58404)を準備されたステートメントのパラメーターの数を決定します。  
  
4.  必要に応じて、準備されたステートメント内の各パラメーターのパラメーター情報を取得する SQLDescribeParam を呼び出します。  
  
5.  各パラメーター マーカーについて、次の操作を行います。  
  
    -   データ値を格納する S パラメーター バッファーの配列を割り当てます。  
  
    -   データの長さを格納する S パラメーター バッファーの配列を割り当てます。  
  
    -   ステートメントのパラメーターにパラメーター データの値とデータの長さの配列をバインドする場合は、SQLBindParameter を呼び出します。  
  
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
  
2.  呼び出す[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)を次の属性を設定します。  
  
    -   SQL_ATTR_PARAMSET_SIZE に、パラメーターのセット数 (S) を設定します。  
  
    -   SQL_ATTR_PARAM_BIND_TYPE を、手順 1. で割り当てた構造体のサイズに設定します。  
  
    -   SQL_ATTR_PARAMS_PROCESSED_PTR 属性を、処理されたパラメーターの数を格納する SQLUINTEGER 変数を指すように設定します。  
  
    -   SQL_ATTR_PARAMS_STATUS_PTR を、パラメーターの状態インジケーターを格納する SQLUSSMALLINT 変数の配列[S] を指すように設定します。  
  
3.  ステートメントの準備 SQLPrepare を呼び出します。  
  
4.  各パラメーター マーカーについて、手順 1. で割り当てた構造体の配列の最初の要素にある変数をパラメーター データの値とデータ長のポインターを指す場合は、SQLBindParameter を呼び出します。 パラメーターが実行時データ パラメーターである場合は、そのパラメーターをセットアップします。  
  
5.  準備されたステートメントの各実行に対して次の操作を行います。  
  
    -   バインドされたパラメーターのバッファー配列にデータ値を入力します。  
  
    -   準備されたステートメントを実行する SQLExecute を呼び出します。 ドライバーによって、S 回 (パラメーターのセットごとに 1 回) SQL ステートメントが効率よく実行されます。  
  
    -   実行時データ入力パラメーターを使用している場合、SQLExecute は SQL_NEED_DATA を返します。 SQLParamData と SQLPutData を使用してチャンク単位でデータを送信します。  
  
## <a name="see-also"></a>参照  
 [クエリを実行方法に関するトピック&#40;ODBC&#41;](executing-queries-how-to-topics-odbc.md)  
  
  