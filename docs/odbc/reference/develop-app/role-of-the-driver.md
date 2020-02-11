---
title: Driver | の役割Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7c344c1d8b3a4702728807af9dae7ed9ca7c5cd0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68020383"
---
# <a name="role-of-the-driver"></a>ドライバーのロール
ドライバーは、ドライバーマネージャーによって確認されなかったすべてのエラーと警告を確認し、生成された状態レコードを注文します。 (ODBC 2.*x*ドライバーは、ステータスレコードを注文しません。)これには、データの切り捨て、データ変換、構文、および一部の状態遷移におけるエラーと警告が含まれます。 ドライバーは、ドライバーマネージャーによって部分的にチェックされたエラーと警告を確認することもあります。 たとえば、ドライバーマネージャーは、 **SQLSetPos**の*操作*の値が有効かどうかをチェックしますが、ドライバーはサポートされているかどうかを確認する必要があります。  
  
 また、このドライバーは*ネイティブエラー* (つまり、データソースから sqlstates に返されたエラー) をマップします。 たとえば、ドライバーによって、無効な SQL 構文に関する多数のネイティブエラーが SQLSTATE 42000 (構文エラーまたはアクセス違反) にマップされる場合があります。 ドライバーは、状態レコードの SQL_DIAG_NATIVE フィールドにネイティブエラー番号を返します。 ドライバーのドキュメントでは、エラーと警告がデータソースから**SQLGetDiagRec**および**SQLGetDiagField**の引数にマップされる方法を示します。
