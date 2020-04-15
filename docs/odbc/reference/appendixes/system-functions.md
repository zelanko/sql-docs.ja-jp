---
title: システム機能 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- system functions [ODBC]
- functions [ODBC], system functions
ms.assetid: 36614b4c-e037-43ef-8692-67f4861b144d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ca71687887444cafc502c15683f3972cf6308e6b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302833"
---
# <a name="system-functions"></a>システム関数
次の表は、ODBC スカラー関数セットに含まれるシステム関数の一覧です。 *情報の種類*がSQL_SYSTEM_FUNCTIONSの**SQLGetInfo**を呼び出すことによって、アプリケーションは、ドライバーでサポートされているシステム関数を決定できます。  
  
 *exp*として示される引数は、列の名前、別のスカラー関数の結果、または、基になるデータ型をSQL_NUMERIC、SQL_DECIMAL、SQL_TINYINT、SQL_SMALLINT、SQL_INTEGER、SQL_BIGINT、SQL_FLOAT、SQL_REAL、SQL_DOUBLE、SQL_TYPE_DATE、SQL_TYPE_TIME、またはSQL_TYPE_TIMESTAMPとして表すことができます。  
  
 *value*として示される引数はリテラル定数で、基になるデータ型は、SQL_NUMERIC、SQL_DECIMAL、SQL_TINYINT、SQL_SMALLINT、SQL_INTEGER、SQL_BIGINT、SQL_FLOAT、SQL_REAL、SQL_DOUBLE、SQL_TYPE_DATE、SQL_TYPE_TIME、またはSQL_TYPE_TIMESTAMPとして表すことができます。  
  
 返される値は、ODBC データ型として表されます。  
  
|機能|説明|  
|--------------|-----------------|  
|**データベース( )** (ODBC 1.0)|接続ハンドルに対応するデータベースの名前を返します。 (データベースの名前は、SQL_CURRENT_QUALIFIER接続オプションを指定して**SQLGetConnectOption**を呼び出すことによっても使用できます。|  
|**IFNULL(** _exp_,_値_**)** (ODBC 1.0)|*exp*が null の場合は、*値*が返されます。 *exp*が null でない場合は *、exp*が返されます。 可能なデータ型または*値*の型は *、 exp*のデータ型と互換性がある必要があります。|  
|**ユーザー( )** (ODBC 1.0)|DBMS でユーザー名を返します。 (ユーザー名は、情報の種類を指定して**SQLGetInfo**を使用しても利用SQL_USER_NAME。これはログイン名とは異なる場合があります。|
