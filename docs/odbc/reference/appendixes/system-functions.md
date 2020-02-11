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
ms.openlocfilehash: e0c7817d37e14ad07b9cc64f59691c27cf665177
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68070092"
---
# <a name="system-functions"></a>システム関数
次の表に、ODBC スカラー関数セットに含まれるシステム関数の一覧を示します。 SQL_SYSTEM_FUNCTIONS の*情報の種類*を使用して**SQLGetInfo**を呼び出すことによって、ドライバーでサポートされているシステム関数をアプリケーションで特定できます。  
  
 *Exp*として指定できる引数は、列の名前、別のスカラー関数の結果、またはリテラルであり、基になるデータ型を SQL_NUMERIC、SQL_DECIMAL、SQL_TINYINT、SQL_SMALLINT、SQL_INTEGER、SQL_BIGINT、SQL_FLOAT、SQL_REAL、SQL_DOUBLE、SQL_TYPE_DATE、SQL_TYPE_TIME、SQL_TYPE_TIMESTAMP として表すことができます。  
  
 *値*として示される引数にはリテラル定数を指定できます。この場合、基になるデータ型を SQL_NUMERIC、SQL_DECIMAL、SQL_TINYINT、SQL_SMALLINT、SQL_INTEGER、SQL_BIGINT、SQL_FLOAT、SQL_REAL、SQL_DOUBLE、SQL_TYPE_DATE、SQL_TYPE_TIME、SQL_TYPE_TIMESTAMP として表すことができます。  
  
 返される値は、ODBC データ型として表されます。  
  
|Function|[説明]|  
|--------------|-----------------|  
|**DATABASE ()** (ODBC 1.0)|接続ハンドルに対応するデータベースの名前を返します。 (データベースの名前は、SQL_CURRENT_QUALIFIER 接続オプションを指定して**SQLGetConnectOption**を呼び出すことによっても使用できます)。|  
|**Ifnull (** _exp_,_value_**)** (ODBC 1.0)|場合*exp*が null の場合、*値*が返されます。 場合*exp*が null でない場合、 *exp*が返されます。 使用できるデータ型または*値*の型は、 *exp*のデータ型と互換性がある必要があります。|  
|**USER ()** (ODBC 1.0)|DBMS 内のユーザー名を返します。 (ユーザー名は、[SQL_USER_NAME] という情報の種類を指定することで、 **SQLGetInfo**でも使用できます)。これは、ログイン名とは異なる場合があります。|
