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
ms.openlocfilehash: b940eac1548582285e7d41e0014cfe911dfb1137
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63254186"
---
# <a name="role-of-the-driver"></a>ドライバーのロール
ドライバーは、すべてのエラーと警告のオフ ドライバー マネージャーによってチェックし、生成される状態レコードを並べ替えます。 (ODBC 2。*x*ドライバーには、状態レコードは順序付けしません)。データの切り捨て、データ変換、構文、およびいくつかの状態遷移のエラーと警告が含まれます。 エラーと警告のドライバー マネージャーによってを部分的にチェックされて、ドライバーは確認も可能性があります。 たとえば、ドライバー マネージャーのチェックがかどうかの値*操作*で**SQLSetPos**は法律、ドライバーがサポートされているかどうかを確認する必要があります。  
  
 ドライバーにもマップ*ネイティブ エラー* - データ ソースによって返されるエラー - SQLSTATEs にします。 たとえば、ドライバーは、数違法な SQL の構文を SQLSTATE 42000 (構文エラーまたはアクセス違反) のさまざまなネイティブ エラーをマップする場合があります。 ドライバーは、状態レコードの SQL_DIAG_NATIVE フィールドに、ネイティブ エラー番号を返します。 ドライバーのドキュメントが引数に、データ ソースからのエラーと警告のマップ方法を表示する必要があります**SQLGetDiagRec**と**SQLGetDiagField**します。
