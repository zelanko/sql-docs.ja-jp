---
title: システム関数 |Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 048db455419d2b74658b758f3a3c525b02bf37f3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47811410"
---
# <a name="system-functions"></a>システム関数
次の表は、ODBC スカラー関数のセットに含まれるシステム関数を一覧表示します。 呼び出して**SQLGetInfo**で、*情報の種類*アプリケーションの SQL_SYSTEM_FUNCTIONS、ドライバーがサポートするシステム関数を判断できます。  
  
 として表される引数*exp* SQL_NUMERIC、SQL_DECIMAL、SQL_TINYINT、SQL_SMALLINT、SQL_INTEGER、SQL と基になるデータ型を表す可能性があります、列、もう 1 つのスカラー関数、または、リテラルの結果の名前を指定できます_BIGINT、使用できます、SQL_REAL、SQL_DOUBLE、SQL_TYPE_DATE、SQL_TYPE_TIME、または sql_type_timestamp 型。  
  
 として表される引数*値*SQL_NUMERIC、SQL_DECIMAL、SQL_TINYINT、SQL_SMALLINT、SQL_INTEGER、SQL_BIGINT、使用できます、SQL_REAL、SQL_DOUBLE、sql _ 基になるデータ型を表すことが、リテラル定数であることができますTYPE_DATE、SQL_TYPE_TIME、または sql_type_timestamp 型。  
  
 返される値は、ODBC データ型として表されます。  
  
|機能|説明|  
|--------------|-----------------|  
|**データベース ()** (ODBC 1.0)|接続ハンドルに対応するデータベースの名前を返します。 (データベースの名前は、呼び出すことによっても使用可能な**SQLGetConnectOption** SQL_CURRENT_QUALIFIER 接続オプションを使用します)。|  
|**見つかれば (** *exp*、*値 * * *)** (ODBC 1.0)|場合*exp*が null、*値*が返されます。 場合*exp*が null でない*exp*が返されます。 データ型または型の*値*のデータ型と互換性があります*exp*します。|  
|**ユーザー ()** (ODBC 1.0)|DBMS のユーザー名を返します。 (ユーザー名も使用での**SQLGetInfo**情報の種類を指定することによって: SQL_USER_NAME)。これは、ログイン名と異なることができます。|
