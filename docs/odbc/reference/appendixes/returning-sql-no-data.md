---
title: SQL_NO_DATA | を返すMicrosoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL_NO_DATA [ODBC]
- backward compatibility [ODBC], SQL_NO_DATA
- compatibility [ODBC], SQL_NO_DATA
ms.assetid: deed0163-9d1a-4e9b-9342-3f82e64477d2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3e2c806edd5d5647e09c00975ad7207ee5c2c876
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305113"
---
# <a name="returning-sql_no_data"></a>SQL_NO_DATA を返す
*Odbc 2.x アプリケーションが*odbc 2.x アプリケーションをただし時して**SQLExecDirect**、 **Sqlexecute**、または**sqlparamdata**を呼び出し、検索された update または delete ステートメントが実行されたが、データソースの行に影響を与えていない場合、odbc *3. x* *ドライバーは*SQL_SUCCESS を返す必要があります。 *Odbc 3.x アプリケーションで*odbc *3.x ドライバーを*使用する場合、 **SQLExecDirect**、 **Sqlexecute**、または**SQLPARAMDATA**が同じ結果で呼び出されると、odbc *3. x*ドライバーは SQL_NO_DATA を返す必要があります。  
  
 ステートメントのバッチ内の検索された update ステートメントまたは delete ステートメントがデータソースの行に影響を与えない場合は、 **Sqlmoreresults**によって SQL_SUCCESS が返されます。 SQL_NO_DATA を返すことはできません。これは、結果がそれ以上ないことを意味します。行が影響を受けている検索された更新/削除の結果がないということです。
