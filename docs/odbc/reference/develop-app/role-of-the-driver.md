---
title: ドライバーのロール |Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 2687e1a68789566fd7b660a8241d65ff4714a933
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47633570"
---
# <a name="role-of-the-driver"></a>ドライバーのロール
ドライバーは、すべてのエラーと警告のオフ ドライバー マネージャーによってチェックし、生成される状態レコードを並べ替えます。 (ODBC 2。*x*ドライバーには、状態レコードは順序付けしません)。データの切り捨て、データ変換、構文、およびいくつかの状態遷移のエラーと警告が含まれます。 エラーと警告のドライバー マネージャーによってを部分的にチェックされて、ドライバーは確認も可能性があります。 たとえば、ドライバー マネージャーのチェックがかどうかの値*操作*で**SQLSetPos**は法律、ドライバーがサポートされているかどうかを確認する必要があります。  
  
 ドライバーにもマップ*ネイティブ エラー* — データ ソースから返されるエラーは、-SQLSTATEs にします。 たとえば、ドライバーは、数違法な SQL の構文を SQLSTATE 42000 (構文エラーまたはアクセス違反) のさまざまなネイティブ エラーをマップする場合があります。 ドライバーは、状態レコードの SQL_DIAG_NATIVE フィールドに、ネイティブ エラー番号を返します。 ドライバーのドキュメントが引数に、データ ソースからのエラーと警告のマップ方法を表示する必要があります**SQLGetDiagRec**と**SQLGetDiagField**します。
