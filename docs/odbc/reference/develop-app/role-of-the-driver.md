---
title: ドライバーの役割 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver error checking [ODBC]
- diagnostic information [ODBC], driver error checking
ms.assetid: cac64c24-a27d-4884-96c0-ea7988351711
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8c683d990aaa3fd6892369e734c06fd1c356bd0f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304284"
---
# <a name="role-of-the-driver"></a>ドライバーのロール
ドライバーは、ドライバー マネージャーでチェックされていないすべてのエラーと警告をチェックし、それが生成する注文の状態レコード。 (ODBC 2.*x*ドライバはステータス レコードを注文しません。これには、データの切り捨て、データ変換、構文、および一部の状態遷移におけるエラーと警告が含まれます。 ドライバーは、エラーと警告を部分的にチェックドライバー マネージャーでチェックすることもできます。 たとえば、ドライバー マネージャーは **、SQLSetPos**の*操作*の値が有効かどうかを確認するがドライバーは、ドライバーがサポートされているかどうかを確認する必要があります。  
  
 また、ドライバは*ネイティブ エラー* (つまり、データ ソースから返されるエラー) を SQLSTATEs にマップします。 たとえば、ドライバは、不正な SQL 構文に関するさまざまなネイティブ エラーを SQLSTATE 42000 (構文エラーまたはアクセス違反) にマップする場合があります。 ドライバーは、状態レコードのSQL_DIAG_NATIVE フィールドにネイティブ エラー番号を返します。 ドライバーのドキュメントでは、エラーと警告がデータ ソースから**SQLGetDiagRec と SQLGetDiagField**の引数にマップされる方法**を示す**必要があります。
